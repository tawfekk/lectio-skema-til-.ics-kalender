# Lectioskema til .ics

Node http server der konverterer fra lectioskemaer til .ics formatet.

Spørgsmål, kommentarer, pull requests osv. meget velkomne!


## Installationsguide

Det antages at der installeres på en Ubuntu / Linux-lignende platform.

0. Installer nødvendige pakker
   ```
   sudo apt install curl libgbm1 tor wget
   ```
1. Installer Node.js. Hent nyeste udgave fra <https://nodejs.org/en/download/>
2. Hent filerne, pak ud, naviger til den udpakkede mappe
   ```
   wget https://github.com/soeren-b-c/lectio-skema-til-.ics-kalender/archive/master.zip
   unzip master.zip
   cd lectio-skema-til-.ics-kalender-master
   ```
3. Installer nødvendige pakker
   ```
   npm install
   npm audit fix
   ```
4. Find dit SKOLE-ID og LÆRER-ID / ELEV-ID  i adressefeltet i dit personlige Lectio-skema.
Eksempel lærer: https://www.lectio.dk/lectio/SKOLE-ID/SkemaNy.aspx?type=laerer&laererid=LÆRER-ID
Eksempel elev: https://www.lectio.dk/lectio/SKOLE-ID/SkemaNy.aspx?type=elev&elevid=ELEV-ID
5. Kopier filen `sample-db.csv` til `db.csv`
   ```
   cp sample-db.csv db.csv
   ```
6. Rediger filen `db.csv`, og tilret med dit SKOLE-ID, og angiv dit brugernavn og kodeord. F.eks. `1,AA,hunter1`, hvis du går på skole 1, med brugernavn AA og kodeord hunter1.
7. (Hvis _og kun hvis_ du kører koden på en Raspberry Pi eller lignende, så fjern kommenteringen på linje 57 i browser.js filen https://github.com/soeren-b-c/lectio-skema-til-.ics-kalender/blob/340eba9f381732c9cc87dbbc61ce854eafdffde2/browser.js#L53-L57 og installer chromium `sudo apt install chromium-browser`.)
8. Start programmet
   ```
   npm start
   ```
9. Besøg web-adressen <http://localhost:9002/?laerer=LÆRER-ID&uger=2&type=laerer&skole=SKOLE-ID> hvis du er lærer, eller <http://localhost:9002/?skole=SKOLE-ID&elev=ELEV-ID> hvis du er elev, og erstatter SKOLE-ID og LÆRER-ID / ELEV-ID med dine egne værdier.
Du får nu genereret en .ics kalender-fil med dit skema.
10. **ALLE SKEMAER FOR ALLE ELEVER OG LÆRERE PÅ DIN SKOLE ER NU TILGÆNGELIGE**, hvis din computer er tilgængelig udefra på port 9002.
    Det er du (med tanke på [GDPR](https://en.wikipedia.org/wiki/General_Data_Protection_Regulation)) nok ikke interesseret i. Der er en grund til at Lectio skjuler skemaerne bag et login.
    Det er **måske en god ide at begrænse adgang udefra**. Brug f.eks. *ufw* til det.
    ```
    man ufw
    sudo ufw deny 9002
    ```

Se [setup.md](docs/setup.md) for forslag til setup og daglig brug.

# Licens

Programmet er oprindeligt skrevet af Emil Bach Mikkelsen og udgivet under ISC licensen.

Emils oprindelige kode kan findes her: [https://github.com/emmikkelsen/node-lectio-til-ics](https://github.com/emmikkelsen/node-lectio-til-ics)

Yderligere bidrag af Scott Mathieson og Leonora.

Programmet kan hentes her: [https://github.com/soeren-b-c/node-lectio-til-ics/](https://github.com/soeren-b-c/node-lectio-til-ics/)
  
# Links

Koden bor her: https://github.com/soeren-b-c/lectio-skema-til-.ics-kalender

Se også: https://skema.click
