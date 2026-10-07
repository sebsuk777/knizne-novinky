# Knižné novinky do Discordu


Automatická kontrola https://www.databazeknih.cz/novinky každú hodinu v 23. minúte. Vyberá iba najnovší týždenný článok typu „… knižní novinky (41. týden)“. Ostatné články ignoruje.


## Aktivácia


1. V Discorde vytvor webhook pre požadovaný kanál.
2. V tomto repozitári otvor Settings → Secrets and variables → Actions → New repository secret.
3. Názov: `DISCORD_WEBHOOK_URL`. Hodnota: URL webhooku. Nikdy ju nevkladaj do kódu ani README.
4. Otvor Actions → Knizne novinky → Run workflow. Pre skutočné odoslanie zruš zaškrtnutie „Iba kontrola bez odoslania do Discordu“.


Pri prvom skutočnom spustení sa odošle jeden aktuálny týždenný článok. Potom iba nový. Správa obsahuje názov, odkaz, popis a obrázok, ak ich stránka poskytuje. Pri novom článku označí role Čtenář📚 a Čtenářka🪶 v texte nad náhľadom. Ostatné role ani @everyone neoznačuje.


## Ako funguje pamäť


Po potvrdenom odoslaní do Discordu sa uloží odkaz do `last-sent.json` a automaticky sa vytvorí commit. Tento súbor nemaž, inak sa aktuálny článok odošle znova. Pri výpadku sa staršie články spätne neposielajú; vyberá sa iba najnovší.


## Prevádzka


- Beží na GitHube, počítač nemusí byť zapnutý. Verejný repozitár používa bezplatný štandardný runner.
- Rozvrh nie je záruka presného času: GitHub môže kontrolu oneskoriť alebo vynechať.
- Bez uloženého webhooku nič neposiela. Skúšobné spustenie nemení pamäť ani neposiela správy.
- Stav a chyby nájdeš v záložke Actions. Zmena štruktúry webu môže vyžadovať úpravu filtra.
- Ak odoslanie prejde, ale uloženie stavu alebo sieťové potvrdenie zlyhá, môže výnimočne vzniknúť duplicita.
- Pri dlhodobej neaktivite verejného repozitára môže GitHub vypnúť rozvrh; znovu ho zapni v Actions. Bežné týždenné uloženie nového článku vytvára aktivitu.


## Vypnutie


Actions → Knizne novinky → menu troch bodiek → Disable workflow.

