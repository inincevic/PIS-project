## Opis projekta
Ovaj projekt, PokeGuesserProject, je baziran na funkcionalnosti pogađanja Pokémon-a. Korisnik putem sučelja (frontend-a) šalje atribute aplikaciji na backend, gdje aplikacija slaže upit za bazu podataka. Tada se u bazi podataka traži Pokémon sa zadanim atributima.

Ukoliko je neki Pokémon pronađen, ispisati će se, u slučaju da nije pronađen frontend će poslati upozorenje.

*Potencijalno će ovaj dio biti maknut. MORAM DODATI ENKCIPCIJU* Korisnik aplikacije može aplikaciju koristit za više načina. Kao gost, ili kao registrirani korisnik.
Ukoliko aplikaciju koristi kao gost, ima samo funkcionalnosti navedene gore.
Kako bi netko mogao koristiti aplikaciju kao registrirani korisnik, mora se registrirati, za što postoji opcija.
Nakon registracije i prijave, korisnik će imati dodatne opcije odabira najdražeg Pokémon-a i prikaza liste svih Pokémon-a koje je ranije pogodio.

## Funkcionalnosti

Funkcionalnosti aplikacije:
- pogađanje Pokémon-a
- registracija korisnika
- prijava korisnika
- odabir najdražeg Pokémon-a
- prikaz liste pogođenih Pokémon-a

## Lokalno pokretanje aplikacije

Potrebno stvoriti docker-e za loklano pokretanje

### 1. stvaranje mreže u kojoj će dokeri komunicirati

docker network create project_network

### 2. stvaranje mongodb dockera

docker pull mongodb

docker run --name mongodb -p 27017:27017 --net project_network -d mongo

### 3. stvaranje baze i dodavanje podatka

Databaza ne dolazi sa podatcima.

Potrebno je u MongoDB Compass-u stvoriti novu bazu podataka i nazvati je "PokeGuesserProject", te u njoj stvoriti kolekcije sa imenima kao datoteke za unos podataka koje se nalaze u Mongo_imports folderu. Potom je potrebno unijeti te podatke u kolecije korištenjem Add Data funkcije.


### 4. stvaranje i pokretanje dockera za backend

docker build . -f backend_docker.dockerfile -t inincevic/backend

docker run --name backend -p 5000:5000 --net project_network -d inincevic/backend  

### stvaranje i pokretanje dockera za frontend

docker build . -f frontend_docker.dockerfile -t inincevic/frontend

docker run --name frontend -p 8080:8080 --net project_network -d inincevic/frontend

Nakon navedenih koraka, aplikaciju se može koristit na http://localhost:8080
