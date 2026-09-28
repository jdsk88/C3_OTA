v2.3.0: integracja z Google Home (Sinric Pro), nazwa i lokalizacja z huba

- Google Home przez chmurę Sinric Pro (Google Home nie obsługuje ESP-NOW,
  a Matter wymagałby Arduino 3.x). Działa w trybach STA i AP + STA.
  Urządzenia: Fan (wł./wył., prędkość -> tryb Ulubiony), czujnik
  temperatury/wilgotności i czujnik jakości powietrza (PM2.5/PM10),
  każde opcjonalne.
- Nowa sekcja System -> Google Home: App Key, App Secret (tylko do
  zapisu), ID urządzeń, stan połączenia.
- Zmiany z UI, ESP-NOW i trybu Auto trafiają do Google Home na bieżąco,
  odczyty czujników co najwyżej co 61 s (limit Sinric Pro).
- Backoff połączenia (2 s ... 60 s), żeby brak internetu nie blokował
  pętli; stos pętli 16 KB na handshake TLS.
- ESP-NOW: komendy "identity" i "config" (nazwa/lokalizacja ustawiane
  z panelu), tożsamość wypychana do huba po zmianie, walidacja długości
  nazwy (32 B) i lokalizacji (24 B) także w API.
- ArduinoJson 6 -> 7 i C++17 (wymagane przez SinricPro 5.x).

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>
