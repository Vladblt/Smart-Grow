Descrierea Proiectului
Sistem IoT automatizat și serviciu web pentru monitorizarea microclimatului și irigarea inteligentă a unei mini-sere.

User Stories (Backlog)

Ca utilizator, vreau să adaug o componentă hardware nouă (ex: senzor DHT22 sau senzor capacitiv de umiditate a solului) în sistem, pentru a o asocia mini-serei mele.

Ca utilizator, vreau să vizualizez panoul principal cu valorile citite în timp real de senzori și starea camerei de monitorizare (ESP32-CAM), pentru a ști starea mediului.

Ca utilizator, vreau să modific pragul de umiditate la care releul declanșează automat pompa de apă, pentru a ajusta irigarea.

Ca utilizator, vreau să văd un istoric tabelar al activărilor pompei de apă din ultima săptămână.

Ca utilizator, vreau să șterg citirile senzorilor mai vechi de o lună, pentru a menține baza de date curată.

Arhitectura și Principiile SOLID aplicate
Proiectul respectă arhitectura MVC și mecanismul de Dependency Injection (DI) nativ din .NET.

Controlerele: Vor prelua exclusiv cererile HTTP (ex: comanda manuală de pornire a ventilatorului de 12V) și vor returna datele fără a conține logică de business.

Serviciile: Logica de business (ex: decizia de a porni irigarea pe baza datelor de la senzorul BH1750 sau DHT22) va fi izolată în servicii specifice (ex: IClimateService), respectând Principiul Inversării Dependențelor.

Modele / DTOs: Datele trimise către interfața web vor fi împachetate în Data Transfer Objects, separat de entitățile bazei de date.

Proiectarea Bazei de Date

Tabel Senzor: Id, NumeSenzor, Tip (Temperatura, Umiditate Sol, Lumina), StatusActiv.

Tabel CitireMicroclimat: Id, SenzorId, Valoare, DataInregistrarii.

Tabel RegulaAutomatizare: Id, PragMinim, TimpFunctionarePompa, Activa.
