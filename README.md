# OPPERCHAMPI — De Muziekeditie

6 deelnemers · 6 rondes · 12 vragen per ronde (6 Spotify-fragmenten + 6 grafische beeldraadsels) · 72 vragen.

## Opgeloste serverfout (versie 2)

De Netlify Function gebruikt nu Functions API v2 (`export default` met Request/Response). Dit is nodig voor automatische Netlify Blobs-configuratie. Als de vorige versie bij **Maak de quizkamer aan** een serverfout gaf, vervang dan de bestaande bestanden in je GitHub-repository, commit ze en laat Netlify opnieuw deployen. Controleer in Netlify bij **Logs → Functions → room** als er toch nog een fout is.

## Publiceren op Netlify

Dit is **geen gewone losse HTML-pagina**: de zes smartphones delen hun spelstand via een Netlify Function en Netlify Blobs. Uploaden via alleen Netlify Drop is **niet voldoende**. Gebruik een GitHub-repository of de Netlify CLI.

**Via GitHub**
1. Pak de ZIP uit. Zet de inhoud van de map in de root van een nieuwe GitHub-repository (ook `netlify/functions/room.mjs`, `questions.js`, `app.js`, `package.json` en `netlify.toml`).
2. Netlify → **Add new project** → **Import an existing project** → GitHub → selecteer de repository.
3. De configuratie wordt uit `netlify.toml` opgehaald. Build command: `npm run build`; Publish directory: `.`; Functions directory: `netlify/functions`.
4. Laat Netlify deployen. De URL eindigt normaal op `.netlify.app`. Open deze HTTPS-URL op een gsm.
5. Maak de kamer aan. De QR-code verwijst automatisch naar jouw gepubliceerde site met de kamercode.
6. Alle zes spelers bezoeken de URL, geven een unieke naam op en melden zich aan. De eerste speler start het spel.

**Let op:** de quiz gebruikt `@netlify/blobs`. De eerste online test moet bevestigen dat Netlify Blobs op jouw site beschikbaar en correct geconfigureerd is. Ongepubliceerde HTML werkt niet met zes telefoons.

## Rolverdeling

- Aanmeldvolgorde bepaalt de quizmasterrotatie: ronde 1 speler 1, ronde 2 speler 2, enzovoort.
- De quizmaster scoort in die ronde niet. De andere vijf krijgen voor een juist antwoord 100 punten.
- Iedereen speelt precies 5 rondes × 12 vragen = **60 scorekansen**.
- Iedere ronde start met een overdrachtsscherm. De quizmaster selecteert wie eigenaar is van de gsm waarop Spotify staat. Dat toestel gaat fysiek naar de quizmaster en wordt via bluetooth met de speaker verbonden.
- De quizmaster kan Spotify op het overgedragen toestel bedienen. Hij of zij ziet op de eigen quiztelefoon de tracknaam, artiest en een Spotify-zoeklink. Spelers zien deze niet.
- De quizmaster speelt ongeveer 15–25 seconden af en laat de overige vijf antwoorden. Daarna onthult de quizmaster de antwoorden.
- Aan het einde van elk blok met 12 vragen komt het klassement. Na ronde 6 volgt het winnaarscherm.

## Beeldvragen en auteursrechten

De beeldvragen bevatten **originele emoji-/typografische raadsels**, geen gekopieerde platenhoezen of persfoto's. Dit is een bewuste keuze: platenhoezen zijn doorgaans auteursrechtelijk beschermd en vrij beschikbaar op het internet betekent niet vrij herbruikbaar.

De muziekfragmenten spelen **niet automatisch via de website**. De quizmaster speelt tracks af in diens eigen Spotify-app, volgens de normale Spotify-gebruiksvoorwaarden. De website biedt alleen een zoeklink en sluit geen Spotify API aan.

## Beperkingen en tips

- Online internetverbinding nodig voor alle zes smartphones. Bij sommige telefoons wordt een achtergrondtab gepauzeerd; terug naar de quiz haalt de actuele stand op.
- De quizmaster kan de tracknamen van de ronde die hij of zij leidt zien; dankzij de vaste rotatie doet iedereen dit precies één ronde.
- Iemand die wil spieken in de broncode van de site kan quizgegevens inspecteren; dit is een gezelschapsspel, geen professioneel beveiligde examenapp.
- De backend is bedoeld voor een groep van zes, niet voor honderden gelijktijdige spelers. Bij exact gelijktijdige antwoorden kunnen `get`-en-`set`-updates in Netlify Blobs botsen; test dit voor het weekend.
- Gebruik op Android het toestel met Spotify-app en bluetoothspeaker als doorgeefapparaat; de quizmaster mag zijn/haar eigen gsm als quizscherm gebruiken.
