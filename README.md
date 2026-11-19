# oefenPE-DevOps

Opgave 1 — Basisworkflow (6 punten)
Maak een workflow aan met als bestandsnaam basis.yml en als naam "PE Basis".
Voorzie als trigger een handmatige start én een start bij elke push. [→ C]
Voeg een job toe met als naam "basis" die start op een Ubuntu virtuele machine. [→ F]
Voeg volgende stappen toe:
1.  Een stap die de code van de repository uitcheckt. [→ 1]
2.  Een stap die de tekst "Student: <studentennummer>" print. [→ 2 — let op de : ]
3.  Een stap die een directory pe aanmaakt, en daarin het bestand <studentennummer>.txt met als inhoud "Hogeschool PXL". Voeg daaronder in hetzelfde bestand de huidige datum toe. [→ 4 + 6/7]
4.  Een stap die de inhoud van dat bestand toont. [→ 8]
5.  Een verificatiestap die de listing en inhoud van alle directories toont (ls -alhR). [→ 9]
6.  Een stap die toont wie de workflow gestart heeft en op welke branch. [→ 3]
7.  Een stap die het bestand bewaart als artifact met de naam "pe-bestand". [→ 24]

Opgave 2 — CI-workflow met Python (8 punten)
Maak een workflow aan met als bestandsnaam ci.yml en als naam "PE CI".
Triggers:
• een handmatige start met een input parameter niveau: keuze tussen snel en volledig; [→ C inputs]
• een start bij elke pull request naar de main branch. [→ C pull_request]
Voorzie voor de hele workflow een omgevingsvariabele STUDENT met als waarde je studentennummer. [→ E]
Voeg een job "test" toe op ubuntu-latest, met een omgevingsvariabele NIVEAU gevuld met de gekozen input. [→ F env]
Stappen:
1.  De code uitchecken.
2.  Python 3.12 installeren. [→ 14]
3.  De dependencies uit requirements.txt installeren. [→ 15]
4.  In één stap: een directory rapport aanmaken en de testen uitvoeren met pytest, waarbij de output wordt opgeslagen in rapport/testrapport.txt. [→ 16b]
5.  Een stap die de tekst "Student: … - Niveau: …" toont met beide variabelen. [→ 10]
6.  Enkel als het niveau volledig is: een stap die de listing van alle directories toont. [→ 12]
7.  Enkel als het niveau snel is: een stap die de tekst "Snelle run" toont. [→ 12]
8.  Een stap die het testrapport bewaart als artifact "testrapport", ook als de testen falen. [→ 24]
Voeg een tweede job "rapport" toe die pas start nadat "test" klaar is. Die toont de tekst "Klaar: gestart door <wie> op <besturingssysteem>". [→ G + 3]


Opgave 3 — Secrets (3 punten)
• Maak in je repository een repository secret STUDENTNAAM met als waarde je voornaam. [→ sectie 11]
• Maak een workflow secret.yml met als naam "PE Secret", enkel manueel te starten, met een job "geheim" op ubuntu-latest.
• Een stap die de secret toont via een omgevingsvariabele (in de log moet *** verschijnen). [→ 11]
• Een stap die altijd de tekst "Secret gebruikt" toont. [→ 26]


Opgave 4 — Theorie (3 punten)
Maak in de root het bestand antwoorden.md en beantwoord kort (in het Nederlands):
1.  Wat is het verschil tussen uses: en run:? Geef van elk een voorbeeld uit je workflows.
2.  Waarom staat het wachtwoord niet in de YAML, en waarom zie je in de log ***?
3.  Waarom moet je in de job "rapport" opnieuw uitchecken als je bestanden uit de repo nodig hebt? (tip: runner)
Indienen
• Doe een commit met als bericht "einde oefen-PE" en push naar main.
• Doe 2 runs van "PE Basis", 2 runs van "PE CI" (één met snel, één met volledig) en 1 run van "PE Secret".
• Controleer dat alle runs groen zijn en dat de artifacts pe-bestand en testrapport bestaan.
Veel succes!
