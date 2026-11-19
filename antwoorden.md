1. Wat is het verschil tussen uses: en run:? Geef van elk een voorbeeld uit je workflows.
run: voert een commando uit dat je zelf schrijft, zoals in een Linux-terminal. Voorbeeld: run: pytest of run: mkdir rapport in ci.yml.
uses: gebruikt een bestaande, kant-en-klare action (meestal uit de GitHub Marketplace); instellingen geef je mee met with:. Voorbeeld: uses: actions/checkout@v4 of uses: actions/setup-python@v5.


2. Waarom staat het wachtwoord niet in de YAML, en waarom zie je in de log ***?
De YAML staat in de repository en in de git-historiek: iedereen met toegang kan het wachtwoord lezen. Dat is een security risk. Daarom zet je het als secret in Settings → Secrets and variables → Actions; daar wordt het versleuteld bewaard en in de workflow gebruik je enkel de naam: ${{ secrets.STUDENTNAAM }}.
GitHub maskeert secrets in de logs: in plaats van de waarde zie je ***, zodat niemand ze kan zien.

3. Waarom moet je in de job “rapport” opnieuw uitchecken als je bestanden uit de repo nodig hebt?
Elke job draait op een eigen, nieuwe runner (een lege virtuele machine). De bestanden van de repository die in job “test” werden uitgecheckt, staan niet op de machine van job “rapport”. Daarom moet je in elke job die repo-bestanden nodig heeft opnieuw actions/checkout gebruiken.