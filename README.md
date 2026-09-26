# C3_OTA

Gotowe do wgrania obrazy oczyszczacza powietrza na ESP32-C3 SuperMini.
Źródła są w prywatnym repozytorium; tutaj trafia wyłącznie wynik kompilacji.

| Plik | Co to jest |
|---|---|
| `manifest.json` | wersja, data, notatki, adresy i sumy SHA-256 obrazów — to czyta urządzenie |
| `firmware.bin` | aplikacja (slot `app0`/`app1`, offset `0x10000`) |
| `littlefs.bin` | interfejs WWW (partycja `spiffs`, offset `0x350000`) |
| `bootloader.bin` | bootloader (offset `0x0`) — tylko do pierwszego wgrania przez USB |
| `partitions.bin` | tablica partycji (offset `0x8000`) — tylko do pierwszego wgrania przez USB |
| `RELEASE_NOTES.md` | opis zmian bieżącej wersji |

## Aktualizacja przez WiFi (OTA)

Urządzenie samo sprawdza `manifest.json` z gałęzi `main` tego repozytorium
po połączeniu z routerem i co 6 godzin. Gdy wersja jest nowsza niż działająca,
w interfejsie pojawia się baner „Dostępna aktualizacja” — po kliknięciu
**Zainstaluj** oczyszczacz pobiera `firmware.bin` i `littlefs.bin`, weryfikuje
SHA-256, zapisuje je i restartuje się. Komputer nie jest potrzebny.

## Pierwsze wgranie przez USB

Wymaga `esptool` (`pip install esptool`). Płytka w trybie programowania nie
jest potrzebna — SuperMini wchodzi w niego sam przez USB.

```sh
esptool.py --chip esp32c3 --baud 460800 write_flash \
  0x0      bootloader.bin \
  0x8000   partitions.bin \
  0x10000  firmware.bin \
  0x350000 littlefs.bin
```

Po starcie urządzenie tworzy sieć `WeatherStation` (hasło `weather1234`),
interfejs jest pod `http://192.168.4.1`. Kolejne wersje przychodzą już przez OTA.
