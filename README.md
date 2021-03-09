<img src="https://firebasestorage.googleapis.com/v0/b/portfoliobymartinnilsen.appspot.com/o/Projects%2Funigrade.png?alt=media&token=fe7f2a12-8e05-446f-8071-6b9a8f2445f6" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="500" height="500" />

# KarakterKalkulator

Dette er et kommandolinjeverktøy utviklet med Python, med den hensikt å kunne registrere universitets- og høgskolekarakterer som bygger på A-E systemet, og regne ut det vektede snittet [1-5] basert på studiepoeng og karakter i hvert fag.

---

## Oppsett

Du kan laste ned prosjektet som zip-fil eller klone prosjektet. En må ha python3 installert, samt anbefales pip for å installere de pakkene en må ha for å kjøre koden. 

Med pip kan du kjøre:

`pip install -r requirements.txt` 

i terminalen og den fikser avhengighetene for deg. 

## Kjøre koden

Dette prosjektet tar i bruk pakken `argh`, som gjør det mulig å definere ulike parametere i terminalkommandoen for kjøring.

```
Grunnleggende:
$ python unigrade.py

Utvidelser:
-a               : Legge til ny karakter
-p <path>        : Se hvordan snittet vil se ut dersom en legger til karakterene definert i denne filen.
```

NB! Ved å definere en shebang øverst i koden (satt til env python3 her), markere den som executable og
legge til dir i path skal man kunne kjøre den uten å ha "python" foran, samt filendelsen ".py". [[StackOverflow](https://stackoverflow.com/questions/27494758/how-do-i-make-a-python-script-executable/27494871)]. Om du ikke ønsker gjøre dette slenger du på filendelsen på filen unigrade (`unigrade.py`) før du kjører den.

---

## Eksempel på bruk

### Se gjeldende snitt

```
$ unigrade
Subject    Grade      Credits
---------  -------  ---------
Eksempel1  A               10
Eksempel2  B                5
Eksempel3  Pass             5

Your weighted average grade is 4.67, with a total of 20 credits.
```

### Legge til ny karakter

```
$ unigrade -a
Name: Eksempel4
Score: C
Credits: 10
```

### Se snitt dersom du får følgende karakterer

Denne funksjonen går ut på at man kan definere en ny liste med karakterer på formen:

```
Subject,Grade,Credits
Eksempel2,A,5
Eksempel4,B,10
```

Og ved å utføre kommandoen `unigrade -p <path>` vil disse legges til i utregningen, men ikke legges inn i oversikten over karakterer du har fått til nå. Dersom du vurderer ta opp en eksamen kan du ved å definere det samme navnet i denne listen se hvilken forskjell en annen karakter utgjør på snittet ditt.

```
$ unigrade -p "/Desktop/predict.csv"
Subject    Grade      Credits
---------  -------  ---------
Eksempel1  A               10
Eksempel3  Pass             5
Eksempel2  A                5
Eksempel4  B               10

Your weighted average grade is 4.60, with a total of 30 credits.
```

Eksempelfilen kalt predict.csv kan tas i bruk for å legge til forutsette karakterer, det er viktig at header-linjen er den samme som i grades.csv.

---

Dersom du skulle finne en feil i koden, legg gjerne inn en PR, opprett et issue eller send det på [mail](mailto:martinjnilsen@icloud.com?subject=[GitHub]%20Karakterkalkulator) til meg.
