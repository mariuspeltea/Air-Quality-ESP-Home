# Air Quality ESP Home
Iată un exemplu de cod YAML pentru ESPHome care include toate componentele menționate: un senzor de temperatură și umiditate DHT22, un releu pentru centrala termică, un senzor de mișcare pentru aprinderea luminii, un senzor de flacara și un senzor de gaz MQ-2 cu buzzer. Acest cod este destinat pentru o placă ESP32 Devkit V1.
DHT22: Senzorul de temperatură și umiditate DHT22 este conectat la GPIO23.
Releu: Releul pentru centrala termică este conectat la GPIO22.
Senzor de mișcare: Senzorul de mișcare PIR este conectat la GPIO21 și controlează lumina camerei conectată la GPIO19.
Senzorul de flacără cu IR OKY3053 este conectat la pinul GPIO25. Acesta are un device_class de tip safety și folosește un filtru delayed_on pentru a evita alarmele false cauzate de fluctuații rapide.
Automatizare: La detectarea flăcării (on_press), buzzerul se va activa, iar când flacăra nu mai este detectată (on_release), buzzerul se va dezactiva.
MQ-2: Senzorul de gaz MQ-2 este conectat la GPIO34 și are un buzzer conectat la GPIO18. Buzzerul se activează când nivelul gazului detectat depășește o valoare specificată (2.0 în acest caz).
Pentru a automatiza funcționarea luminii doar noaptea, după apusul soarelui, poți folosi componenta time din ESPHome pentru a obține informații despre răsărit și apus. Apoi, poți crea o condiție care verifică dacă este noapte înainte de a aprinde lumina în funcție de senzorul de mișcare.
Explicații:
Componenta time: Folosim platforma homeassistant pentru a sincroniza ora și pentru a obține informații despre răsărit și apus.
Condiția pentru senzorul de mișcare: În secțiunea on_press, adăugăm o condiție sun.is_below_horizon pentru a verifica dacă soarele este sub orizont (este noapte) înainte de a aprinde lumina camerei.
