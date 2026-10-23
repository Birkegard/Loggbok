Loggbok

Sprint 1 - vecka 39:
Under den första sprinten jobbade jag med att lägga till CI för frontend, såg till att frontend kunde 
köra lokalt efter att Jimmy hade skapat repot, skapade en CORS-konfiguration i orderservice för att 
tillåta att frontend kan ansluta mot den, skapade en gemensam header och footer med länkar till olika 
sidor på webbplatsen. Vi började att undersöka en betallösning och hur vi isf ville bygga 
och implementera den. Jag gjorde även den första delen av kundvagnen, så att användare kunde lägga till
produkter, att kundvagnen gick att toggla, och ett alert-meddelande när en produkt läggs till.

Hade inga problem med dom tasks jag gjorde under den här veckan. Det som var lite klurigt var att 
hitta information om hur man sätter upp CORS i en applikation, något som vi inte hade gjort tidigare.

Samarbetet i gruppen fungerade på det stora hela bra. Korta och koncisa daily scrums, 
tydlig uppdelning inför demon och en givande retro där vi pratade om kommunikation. 
Ett stort problem var att Kevin inte deltog på sprintplaneringen, något han meddelade en halvtimme 
innan mötet. Men vi lyckades jobba runt det och han fick sina tasks tilldelade. Mycket av det som fanns
i backlogen för sprint 1 var grundläggande uppstart av frontend vilket gjorde att planning pokern gick
snabbt och vi var väldigt överens på alla punkter.

Vi har nog gjort lite annorlunda kontra andra grupper här då vi sätter upp tydliga mål för vad som ska 
vara klart under sprinten och istället för att skapa user stories och sätter som kort i trello, så
skapar vi kort av hela den stora uppgiften och i det kortet skapar vi en checklista med vad som 
behöver lösas (user stories). Ett sätt som har fungerat bra för oss att arbeta på.

----------------------------------------------------------------------------------------------------------
Sprint 2 - vecka 40:
De uppgifter som jag fick i andra sprinten var att konfigurera testmiljö och komponenttesta
ProductCard. Jag gjorde även kundvagn del 3 efter att Kevin var klar med del 2, det som gjordes i 
del 3 var att varukorgen skulle finnas kvar vid omladdning av sidan (spara i sessionStorage), 
när kunden trycker på knappen för att köpa så skapas en order i order-service och varukorgen töms.
Vid fel så skapades ett felmeddelande. Jag började även med att läsa på om betalningslösningen med
Stripe samt började koda betallösningen utifrån dom delar vi kom överens om.

Hade inga större problem denna veckan heller. Det blev däremot en del efterforskning kring testerna,
främst att hitta en lösning för att isolera ProductCard-sidan till testerna. Det gjordes med vi.fn() 
när man trycker på knappen som anropar onAdd. Använden även fireEvent för att simulera ett klick på
knappen, så att det gick att se så rätt produkt lades i kundvagen.

Denna veckan var jag scrummaster. Tycker det var rätt roligt och lärorikt, fick beröm från gruppen
att jag är pedagogisk och tydlig i det jag gör och hur jag fördelar uppgifter, ordet och kan ta 
beslut på vad som behöver göras. Sprintplaneringen gick bra, vi kom igång ordentligt med betallösningen
och delade upp så att Jimmy tittade på WebHooks, jag tog själva paymentservice med tillhörande arbete
och Maria började pilla med frontend. Överlag så flöt arbetet på väldigt bra, alla var engagerade,
vi hade bra kommunikation hela veckan och hade mycket fint att visa upp på demon.

----------------------------------------------------------------------------------------------------------
Sprint 3 - vecka 41:
Under tredje sprinten så blev det väldigt stort fokus på att försöka få igång betallösningen och få
den att synka med order-service och frontend, något vi till slut lyckades med och kunde få till ett
fullständigt flöde. Extra roligt var det när vi på fredagen även kunde få till så att det gick att
få en orderbekräftelse via mail. Det enda vi upptäckte var att mailet skickades innan man kom till
betalsidan, något vi löste veckan efter genom att flytta metoden som triggade mail till att komma 
senare i flödet. Utöver det skapade jag sidan för detaljer om en specifik produkt, jag la till en knapp
för detta, och såg till så att all relevant info renderas på ett kort som såg ut som det gjorde på 
produktsidan, men mycket större och med lite annan ordningsföljd av informationen.

Även denna vecka blev det en del efterforskning men den här gången om hur vi skulle få betallösningen
att fungera som vi ville, det blev en del if-satser för att kunna stoppa en betalning om priset ändras
innan checkout, om fel användare anropar betalningen etc. Lösningen blev som sagt if-satser med hjälp 
av AI och dokumentation fick vi tillslut till det.

Kevin var scrummaster och det mesta flöt på bra. Han hade en del problem med att få det att fungera 
lokalt men svårt att säga varför. Vet inte om han hade gjort PR-s på alla ändringar som gjorts.
Detta medförde att jag fick köra demon på Sprint-reviewen, vilket gick bra då hela mitt flöde fungerade.

----------------------------------------------------------------------------------------------------------
Sprint 4 - vecka 42:
Fjärde sprinten inleddes med en uppgift som låg kvar från tidigare vecka, det var att lägga till en
"lägg till i kundvagn"-knapp även på produktdetaljsidan. Vilket vi fått instruktioner om, något som
gick smidigt med de instruktioner vi fått under tidigare lektioner. I övrigt denna vecka har jag suttit
mycket med Gateway efter att Jimmy startade repot under söndagen. Jag la till miljövariabler, konfigurerade
CORS, kopplade den till våran order-service och payment-service. Samt skapade hjälpmetoderna send och
forwardPost. Vi har även under sprinten deployat både gateway och payment-service på render och satt
miljövariabler för detta i env.local. Vi har även testat hela flödet och det fungerar som det ska.

Ett problem vi upptäckte när vi sparade kundvagnen i sessionen var att den låg kvar oavsett vem som 
loggade in på siten under pågende session. För att fixa detta ändrade vi så att kundvagenen sparas
på den specifika användaren som är inloggad istället för att den sparas på hela sessionen. Detta medför
också att produkterna ligger kvar om jag senare loggar in och vill fortsätta att handla där jag var.

Jag, Jimmy och Maria-Pia har haft väldigt tät kontakt med varandra under veckan och fått ordning på
dom tasks som vi haft på oss. Kommunikationen från Kevin har varit väldigt bristfällig. När vi väl fick
kontakt med honom i torsdags så förklarade han att han höll på att flytta in möbler i sin lägenhet. Vi 
var även lite i osynk med vad vi hade för förväntningar, min tanke var att vi skulle få klart med att
spara användarens token i en cookie medan delar av gruppen tänkte att det låg under kommande sprint. 
Så det vi kom överens om är att den uppdaeringen görs under sprint nummer 5.

----------------------------------------------------------------------------------------------------------
Sprint 5 - vecka 43:
Denna veckan har jag fixat för att cookies ska fungera i frontend, vilket har inneburit att alla services 
har fått attributet credentials: include. Login-metoden har uppdaterats så att logga in/logga ut uppdateras
med om det finns en inloggad användare eller inte. Jag var även tvungen att uppdatera våran protectedroute
så att den både kollar om det är en user, och att den får behörighet till rätt sida samt att den inte ser 
admin-fliken när den är inloggad. Även om det skulle vara möjligt att se den så hade en vanlig user inte kunnat
nå själva endpoiten sett till säkerhetsfiltret som finns i mikrotjänsten. Vidare har vi alla i gruppen undersökt
vitest, RTL och MSW samt skrivet en kortare dokumentation om vad det är och vad skillnaderna är på komponent-, 
integration- och e2e-tester. Jag skapade utifrån det tester för att mocka auth/me samt /products så att en 
inloggad användare kan se produkterna som finns samt att man får ett felmeddelande om hämtning misslyckades.
Slutligen den här veckan så driftsatte jag våran frontend på render.

Vi hade inga större problem under veckan, det vi hittade var att när man gjorde en lyckad betalning så blev
man redirected till localhost, något vi var tvungen att sätta miljövariabler för, så att vi kom rätt. Det var 
även ganska klurigt att få till det med cookies i vår frontend då vi även har integrerat payment. Men med lite 
hjälp av AI, en del hjälp av dokumentation och stöd av varandra så fick vi till det.

Under veckan som gått har jag varit scrummaster igen. Något som likt första gången gick relativt smärtfritt 
jag satte upp tydliga mål utifrån backlogen från gruppen och därefter bedömde vi dom olika uppgifterna i 
backlog och bestämde vem som gjorde vad. Som tidigare har vi haft bra kontakt i teamet och vi har hjälpt 
varandra om det är något som har strulat, samt varit bra på att säga till om man behöver hjälp. Olyckligt 
i början var att en person tog fel på tiden för planeringsmötet. Vad gäller start, stop och continue på 
retro så hade vi egentligen inga nya start eller stop då vi tycker att arbetet flyter på bra och den 
förändring som vi gjorde med att flytta all kommunikation från teams till discord var bra. Så dom två 
continue vi kom fram till var att fortsätta lyfta dom småsaker i applikationen som inte är klara med
till exempel layout. Vi var även tydliga med att vi vill fortsätta att jobba på discord.

--------------------------------------------------------------------------------------------------------------
