v2.2.6: tryb "Tylko ESP-NOW", porządki w zakładce System

- Nowy tryb sieci "Tylko ESP-NOW": WiFi wyłączone, radio działa
  tylko dla wyświetlacza, na kanale z chwili przełączenia.
- Przycisk BOOT przytrzymany 5 s przywraca WiFi z każdego trybu
  (AP + STA z zapisanym routerem, inaczej AP).
- Sekcja Sieć zbiera wszystko: stan połączenia, WiFi, wyświetlacz
  (ESP-NOW) i urządzenie (nazwa, lokalizacja).
- Przełącznik ESP-NOW zapisuje się od razu.
- Poprawki układu na telefonie.
- Build przypięty do platformy espressif32@6.10.0.
