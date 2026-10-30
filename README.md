# Sprintplanering - CheckoutLite

Individuell övning i agil metodik och Scrum.

Fyll i README:n enligt uppgiften i `uppgift.md`.

## Scrum-roller

- **Product Owner:** Filip Lind (även Utvecklare)
- **Scrum Master:** Sara Viberg (även Utvecklare)
- **Utvecklare:** Erik Strand, Mia Nordin

## Sprintmål

När sprinten är klar ska CheckoutLite presentera en fungerande kassaöversikt i gränssnittet där kunden ser butiksnamn och valuta, automatisk beräkning av totalsumma med moms, tydlig fraktstatus samt validering av rabattkod.

### Agil motivering

Genom att dela upp kassafunktionerna i korta iterationer kan vi testa orderflödet tidigt i gränssnittet. Om skatteberäkningar eller valideringsregler behöver justeras upptäcker vi det under sprintens gång i stället för dagen före lansering.

## Produktbacklog

### US-1: Visa butiksinformation
- **User Story:** Som en kund vill jag se butikens namn och valuta i sidhuvudet för att känna trygghet i vilken marknad jag handlar på.
- **Acceptanskriterier:** Funktionen `visaButikInfo()` returnerar `"Nordic Gear (SEK)"` så att elementet `#header-info` visar butik och valuta.
- **Ansvarig:** Filip Lind

### US-2: Beräkna totalbelopp och moms
- **User Story:** Som en kund vill jag få ordersumman och 25 % moms kalkylerad automatiskt för att veta exakt vad mitt köp kostar.
- **Acceptanskriterier:** `raknaTotal(varusumma)` adderar 25 % moms och returnerar totalbeloppet som numeriskt värde.
- **Ansvarig:** Sara Viberg

### US-3: Avgöra fraktvillkor
- **User Story:** Som en kund vill jag se om min beställning kvalificerar sig för fri frakt för att kunna avgöra om jag ska lägga till fler varor.
- **Acceptanskriterier:** `statusFrakt(total)` returnerar `"Fri frakt"` om totalen är > 500, annars `"Frakt tillkommer (49 kr)"`.
- **Ansvarig:** Erik Strand

### US-4: Validera rabattkod
- **User Story:** Som en kund vill jag kunna skriva in en rabattkod så att systemet kontrollerar att den uppfyller formatkravet.
- **Acceptanskriterier:** `valideraKupong(kod)` returnerar `true` om koden är minst 4 tecken lång, annars `false`.
- **Ansvarig:** Mia Nordin

## Daily Standup & Sprint-anpassning

### Standup-notering
Teamet genomförde sin 5-minuters morgonsynk. Alla funktioner var i fas, men Product Owner lyfte ett önskemål från butiksledningen gällande rabattkoder.

### Sprint-anpassning (Kravändring)
- **Vad:** Butiksledningen kräver att kupongkoder ska vara skiftlägesokänsliga (både "SOMMAR" och "sommar" ska accepteras).
- **Vem:** Product Owner uppdaterade acceptanskriteriet för US-4. Mia Nordin anpassade funktionen så att koden normaliseras med `.toLowerCase()` före formatkontroll.
- **Varför sprintmålet håller:** Ändringen ryms inom samma modul och påverkar inte kassaöversiktens övergripande funktionalitet eller leveransdatum.