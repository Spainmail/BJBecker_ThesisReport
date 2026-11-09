<br>
<h1>How do I achieve seamless level streaming similar to Alan Wake II?</h1>
<br>
<i>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>Thesis Project by Billy Becker</i></b><br>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Yrgo 2026</p>
<br><br><br><br><br><br><br><br><br>

<h2>Introduktion</h2>
<br><br>

Jag är Billy, och det här är mitt examensarbete som student på Göteborgs YRGO.
Ämnet och frågeställningen jag valt är något jag intresserats av en längre tid, och iochmed min bakgrund inom speldesign har jag till viss del stött på det tidigare om än i annan kontext.
Jag har alltid stört mig på när man kan känna av i frame timingen att något tungt laddas in, och imponerats av när det inte är uppenbart. Strax innan det var dags för examensarbete spelade jag spelet Mortal Shell II, som kom så irriterande nära att lyckas på konsoll (specifikt när spelaren går ner i en dungeon). Att försöka komma så nära seamless som möjligt och förstå hur man undviker stora frame timing dips är huvudmålet med detta arbetet.<br>
<br>
Jag tror att mina efterforskningar inom detta kommer att gagna mig genom att jag lär mig optimisering när det gäller level och asset streaming, vilket blir alltmer viktigare ju större spelvärldar blir. Eftersom kontexten för produkten av arbetet kommer utvecklas i Unity kommer jag förhoppningsvis att kunna tala självsäkert om vilka metoder och tekniker som ger mest "bang for the buck" när det gäller att få ner lag spikes vid scen- och asset streaming.<br>
<br>

<h2>Frågeställning - "How do I achieve seamless streaming similar to Alan Wake II?"</h2>
<br><br>

Jag vill med arbetet undersöka och komma fram till sätt att förstå hur level- och asset streaming påverkar frame timing, och hur vi kan minimera den påverkan. Jag valde spelet Alan Wake II specifikt för att jag hade färskt i minne tillfällen då spelaren gick från ett rum till ett annat genom en dörr, bara för att sekunder senare gå tillbaka genom samma dörr men hamna i ett tredje utrymme. Detta imponerade på mig i hur "smooth" det kändes, och jag antog att det var ett väldigt snyggt hanterande av att strömma in detta tredje område.<br>
I första veckan av examensarbetet upptäckte jag att även om AW2 garanterade använder sig av level- och asset streaming så är detta inte sättet de åstadkom den effekten. De teleporterar helt enkelt spelaren mellan "set piece"-utrymmen som redan finns i minne, på ett sätt som inte märks. De tre rummen var således alltid där, och det jag upplevde som level streaming var i själva verket ett elegant sätt att förflytta spelaren/rum för att få den sömlösa effekten. Trots detta väljer jag att ha kvar AW2 i titeln av mitt arbete eftersom resultatet jag vill åstadkomma är samma även om tillvägagångssättet är ett annat i mitt fall.<br>


<br><br>
TO DO/Skeleton text:<br>
- Translate to english (yes!).
- More generally about me, eventually funneled towards touchpoints with this topic and prior experiences with scene loading.
- Reference game and why it turned out to be misguided.<br>
&nbsp;&nbsp;&nbsp;&nbsp;  - Thought the seamless level transitions were more dependant on streaming in quickly and asynchronously. Still obviously a thing, but the specific moments during the game that impressed me turned out to use a different technique (teleporting player to a different part of the level in a way they don't notice)<br>
&nbsp;&nbsp;&nbsp;&nbsp;  - Still kept the title as-is since it does convey my goals well.<br>
- Why this thesis would be of use to anyone else.<br>
&nbsp;&nbsp;&nbsp;&nbsp;  - <br>
