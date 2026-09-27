v2.2.4: osobne pomiary DHT22 i SDS011, naprawa SDS011

- Naprawa: SDS011 nie wracał po resecie ESP32 (np. po OTA). Czujnik
  zostawał uśpiony, bo dostawał komendy przed wybudzeniem - teraz
  zawsze jest najpierw budzony.
- Nowe przyciski "Zmierz DHT22" i "Zmierz SDS011" obok "Zmierz
  wszystko" (dawniej "Zmierz teraz").
- Sam odczyt DHT22 odświeża wartości na żywo, ale nie trafia do
  historii i nie zmienia wentylatora w trybie Auto.
- API: POST /api/measure?sensor=all|dht|sds.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
