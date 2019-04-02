# South-Zubony International Airport (*SZIA*) alkalmazás

![](img/logo.png)

## Elvégzendő feladatok
  - Modell osztályok elkészítése: `Airline`, `News`, `Flight`, `Complaint`
  - Alkalmazás vázának elkészítése: be van rakva a `UITabBarController`, amelyhez tartozik `5` db nézetvezérlő. 
  - Az érkező és induló járatok képernyők elkészítése (kedvencek mentésével együtt).

## Bevezetés
Sokan emlegették már, hogy milyen jó volna, ha a dél-zubonyi reptérnek is lenne mobilalkalmazása, hiszen Zubonyon keresztül naponta több millió ember utazik és a reptér honlapja közel sem tökéletes. Szerencsére a járatinformációkhoz elég komoly *webes API* áll rendelkezésre, illetve a zubonyi utasok jellemzően iPhone-t használnak.

A következő két órában a *SZIA* alkalmazás első pár képernyőjét kell elkészíteni `iOS` platformra, `iOS 11` minimum platform, `Swift 5` és `Xcode 10` használatával.

## Alkalmazás specifikációja
Az elkészítendő mobilaklamazás négy főbb funkciót ölel fel:
  
  - járatinformációk megjelenítése és mentése,
  - reptéri hírek megjelenítése, 
  - reptér térképen történő megjelenítése,
  - panaszbejelentés.

### Járatinformációk
Az alkalmazásban lehetőség van az induló és érkező járatok listaszerű megtekintésére. Az egyes járatokat lehetőség van kedvencnek jelölni, ekkor azt el kell tudni menteni a telefon lokális adatbázisában és internet nélkül is meg kell tudni jeleníteni. A járatinformációkat az internetről kell letölteni.

### Hírek
A reptér aktuális híreit egy listában kell megjeleníteni: egy elemre rányomva megjelenik a hír részletes leírása. A híreket az internetről kell letölteni.

### Térkép
Zubony koordinátái megegyeznek a BME Q épület koordinátáival, a repteret egy térkép nézeten kell megjeleníteni.

### Panaszbejelentés
Lehetőség van panaszt tenni, amely egy form kitöltését és elküldését jelenti, ehhez lehetőség van képet is mellékelni.

## Modell
Az alkalmazásban a következő objektumok szerepelnek, zárójelben a kapcsolódó adatok:

  - `Légitársaság` (*kép*, *név*, *azonosító*)
  - `Járat` (*járatszám*, *azonosító*, *indulás*, *érkezés*, *kiinduló város*, *cél város*, *státusz*, *checkin szám*, *kapu szám*, *késés*, *megjegyzés*, *légitársaság azonosítója*)
  - `Hír` (*azonosító*, *cím*, *tartalom*, *dátum*)
  - `Panasz` (*tartalom*, *panasz tárgya*, *bejelentő neve*, *bejelentő email címe*, *bejelenő telefonszáma*, *kép*)

## Szerver

Az alkalmazás adatohoz a végpont a [`http://szia-backend.herokuapp.com/api/`](http://szia-backend.herokuapp.com/api/) címen érhető el. Kipróbálni a kéréseket a [`http://szia-backend.herokuapp.com/explorer/`](http://szia-backend.herokuapp.com/explorer/) címen lehet. Amire szükség lesz a feladat elkészítése során:

- `GET` /Airlines
- `POST` /Complaints
- `GET` /Flights
- `GET` /News

## Alkalmazás képernyők
Az alkalmazás különböző funkciói különböző képernyőkön jelennek meg, amelyek külön lapokon (tabokon) találhatók. Az itt szereplő képernyők vázlatok(!), a feladat része, hogy a vázlatok alapján mindenki maga dizájnolja meg az alkalmazást a saját ízlése alapján.

### Érkező járatok
Az első lapon található az érkező járatok képernyő. Itt láthatóak az érkező járatok listaszerűen. A lista a frissítés gombra nyomva frissíthető (vagy pl. *swipe to refresh*), ilyenkor letölti a szerverről a legfrisebb járat információkat (opcionálisan a lista lefelé *swipe*-polásával). Egy elemre kattintva kedvencnek jelölhető, amelyet adatbázisban el kell tudni tárolni. Ezt valamilyen módon, pl csillag vagy felirat jelezni kell.

![](img/flight_list.png)


### Induló járatok
Analóg az érkező járatokkal.

### Hírek és hírek részletei
A harmadik lapon található a hírek nézet, amelyen a legfrisebb hírek jelennek meg időrendben. Egy hírre kattintva láthatóak annak részletei.

### Térkép nézet
A térkép nézeten dél-Zubony látszik a térképen, rányomva pedig megjelennek a reptér alapinformációi.

### Panaszbejelentés
A utolsó lapon látható a panaszbejelentő, amely egy kitöltendő *form*. Kiöltése után a `Send` gombra kattintva küldhető fel a szerverre. Lehetőség van képet is feltölteni a szerverre.
