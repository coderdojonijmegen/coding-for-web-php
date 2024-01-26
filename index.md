---
title: "Web - Development - Php"
date: 2020-11-18T23:07:16+01:00
draft: false
toc: true
headercolor: "teal-background"
onderwerp: PHP
---

We gaan programmeren met PHP.

<!--more-->

## Introductie
De meestgebruikte programmeertaal voor websites is PHP. Het is een heel handige taal waarmee je een eigen slimme website kunt bouwen.

Je gaat nu leren hoe PHP werkt, en dat doe je door een online vriendenboek te maken. Je leert informatie op te slaan, hoe je uitrekend hoeveel dagen oud je vrienden zijn, en hoe je een plaatje maakt met hun lievelingskleur.

## Benodigdheden
Als je websites wil bouwen met PHP, heb je een plek nodig waar je software kunt schrijven. We gebruiken nu CodeAnywhere. Daar kun je oefenen met PHP, en zie je ook meteen hoe het resultaat eruitziet.

Als je je niet eerder hebt aangemeld, ga dan naar https://codeanywhere.com/signup. Vul je mailadres in, een wachtwoord, kruis het hokje aan, en klik op 'register'. Open het mailtje dat CodeAnywhere je gestuurd heeft om op de link te klikken. Ga door naar de editor: https://codeanywhere.com/editor.

In het scherm dat je daar ziet, vul je eerst je naam in. Bij 'Search stack' vul je PHP7 in, en dan klik je op PHP 7 in de lijst daaronder. Klik onderaan op 'create' en wacht af.

## Stappen
### Je eerste webpagina
Als het goed is, zie je nu een omgeving waarin je kunt beginnen aan het maken van je eigen website.

Maak de eerste pagina aan door in het menu bovenaan te klikken op File, en dan 'New File'. Nu kun je in het grote zwarte vlak in het midden beginnen met je eerste webpagina.

Een webpagina ziet er in het begin altijd zo uit als hieronder. Kopiëer en plak dit voorbeeld in het zwarte vlak:

{{< highlight html >}}
	<html>
	  <head>
	    <title>Mijn website</title>
	  </head>
	  <body>
	    <h1>Welkom</h1>
	  </body>
	</html>
{{< /highlight >}}
			
In het blokje 'head' staat informatie over je site, zoals de titel. In het blok daaronder, de body, staat alles dat te zien is op de pagina, zoals de kop, tekst en plaatjes.

Deze indeling met <>-tekens noemen we HTML. Dat is de taal waarmee je opgeeft wat waar op de pagina komt te staan en hoe het eruit ziet.

`<h1>` is bijvoorbeeld een HTML-code waarmee je opgeeft dat het een dikgedrukte kop bovenaan de tekst is.

Bewaar je pagina door in het File-menu op 'Save' te klikken. Klik in het venster dat je dan ziet op 'file name' en vul daar in: index.php Klik daaronder op je naam en dan onderaan het venster op 'Save'.

Nu kun je je webpagina bekijken. Klik op de 'play'-knop bovenaan:

![webpagina bekijken](play-knop.png)


### PHP mee laten doen
Je website is nu nog heel eenvoudig - en niet zo slim. Hij laat alleen zien wat jij hebt ingetypt.

Je kunt je webpagina er ook steeds anders uit laten zien, door PHP te gebruiken. De programmacodes van PHP kun je gewoon tussen de HTML-code zetten.

Voeg deze regel toe aan je webpagina, direct onder de regel met <h1>:

{{< highlight php >}}
	<?php echo '<p>Hallo wereld</p>'; ?>
{{< /highlight >}} 
			
Zo dus:

{{< highlight html >}}
	<html>
	  <head>
	    <title>Mijn website</title>
	  </head>
	  <body>
	    <h1>Welkom</h1>
	    <?php echo '<p>Hallo wereld</p>'; ?> 
	  </body>
	</html>
{{< /highlight >}} 
			
Je laat weten waar de PHP-code begint met <?php en sluit het blokje weer af met ?>. <p> is HTML en geeft aan waar een nieuwe alinea begint. Zoals de meeste codes in HTML sluit je die ook weer af, met </p>.
En klik weer op 'play'.

Het enige dat je PHP nu laat doen, is iets laten zien in de browser (het programma waarmee je de website bekijkt). Gelukkig kun je met PHP nog veel slimmere dingen maken, en dat gaan we nu doen.

### Websites slimmer maken
Eén van de manieren waarop je een webpagina wat slimmer kunt maken, is door PHP een beetje te laten meedenken.

Je kunt bijvoorbeeld steeds iets anders laten zien op basis van het adres (de url) dat een bezoeker intypt om bij jouw webpagina te komen.

Verander de PHP-regel uit het vorige voorbeeld zodat dit er komt te staan:

{{< highlight html >}}
	<html>
	  <head>
	    <title>Mijn website</title>
	  </head>
	  <body>
	    <h1>
	      <?php echo 'Hallo ' . $_REQUEST["naam"] . '!'; ?>
	    </h1>
	  </body>
	</html>
{{< /highlight >}} 
			
Let erop dat je ook de <p>-codes uit het vorige voorbeeld weghaalt. Let ook op dat de H1-kop pas afsluit ná de PHP-code. De PHP code moet dus tussen <h1> en </h1> staan.

PHP zegt nu met het commando echo 'Hallo' tegen een naam die in het webadres van je pagina wordt genoemd. We laten dat zo zien.

Sla je pagina op (via File en Save) en druk weer op 'play'.

Je ziet nu dat de kop van de pagina is veranderd in 'Hallo !'. Meer niet, want we hebben nog geen naam genoemd in het webadres.

Tik in de adresbalk achter het adres van je site ?naam= en dan je naam. Het zou er ongeveer zo uit moeten zien:

	<sitenaam>/?naam=Steven

of zo:

	<sitenaam>/index.php?naam=Steven

Druk op enter om de pagina opnieuw te laden. Probeer het daarna nog een paar keer met een andere naam in het adres.

### Formulieren
Wat je nu zou kunnen doen, is een persoonlijke pagina maken voor elk van je vrienden en familieleden. Door een formulier op die pagina te zetten, kunnen zij meer informatie over zichzelf invullen. Zo maak je je eigen online vriendenboek.

Maak dit formulier:

{{< highlight html >}}
	<html>
	  <head>
	    <title>Vriendenboek van Jaap</title>
	  </head>
	  <body>
	    <h1>
	      <?php echo 'Hallo ' . $_REQUEST["naam"] . '!'; ?>
	    </h1>
	
	    <form action="resultaten.php" method="post">
	      <p>
	        Je voornaam: 
	        <input type="text" name="naam" value="<?php echo $_REQUEST["naam"]; ?>" />
	      </p>
	      <p>
	         Hoe oud ben je? 
	         <input type="text" name="leeftijd" />
	      </p>
	      <p><input type="submit" value="Opsturen" /></p>
	    </form>
	
	  </body>
	</html>
{{< /highlight >}} 
			
Vul hier je eigen naam in. [bij de titel]

[als we de naam al weten, dan vult PHP die hier alvast in]

Voeg zelf nog twee vragen toe voor het vriendenboek: hoe lang ze zijn (in centimeters) en nog iets, zoals bijvoorbeeld wat hun favoriete film is. Let erop dat je elk input-veld een unieke 'name' geeft, dus bijvoorbeeld 'name="lengte"'.

### Resultaten van het formulier
In de code kun je zien dat het formulier de ingevulde informatie doorgeeft aan een andere pagina die resultaten.php heet. Die pagina gaan we nu aanmaken.

Ga bij CodeAnywhere naar File en klik op 'New file'.

Maak een pagina die ongeveer lijkt op die hieronder. Denk eraan dat je het antwoord op je zelfbedachte vraag ook nog moet opvangen.

{{< highlight html >}}
	<html>
	  <head>
	    <title>Vriendenboek van Jaap</title>
	  </head>
	  <body>
	    <h1>Resultaten</h1>
	
	    <p>Hoi <?=$_REQUEST["naam"]?>, je bent dus <?=$_REQUEST["leeftijd"]?> jaar oud en <?=$_REQUEST["lengte"]?> centimeter lang.</p>
	
	  </body>
	</html>
{{< /highlight >}} 
			
[dit is een iets andere manier om PHP even snel iets in te laten vullen]

Sla je nieuwe pagina op (File, en dan Save) en vul bij 'file name' in resultaten.php Klik daaronder op je naam en klik onderaan op Save. Klik weer op 'play'.
![opslaan als](save-as.png)

### Rekenen met PHP
De informatie die iemand invult, wordt door PHP opgeslagen in variabelen. Variabel betekent dat iets steeds anders kan zijn. In dit geval kan de variabele 'leeftijd' 4 zijn of 12, maar ook 125 of zelfs een woord zoals 'slagroomtaart'.

Je kunt ook rekenen met die variabelen.

Dus stel dat iemand heeft ingevuld dat ze 12 is, dan kunnen we uitrekenen wat haar geboortejaar is.

Voeg deze regels toe aan resultaten.php:

{{< highlight php >}} 
	<?php
	$leeftijd = $_REQUEST["leeftijd"];
	$jaar = 2018;
	echo "<p>Dat betekent dat je geboren bent in ";
	echo $jaar - $leeftijd;
	echo ".</p>";
	?>
	
{{< /highlight >}} 
			
En bekijken het resultaat door deze pagina op te slaan en je eerste pagina weer te starten.


Voeg nu zelf de code toe om met PHP te laten zien hoeveel centimeter deze vriend of vriendin langer of korter is dan jij bent.
![opslaan](geboren-in.png)

### Informatie bewaren: cookies
Informatie verzamelen met formuleren en die gegevens opslaan in variabelen is leuk, maar het probleem is dat die informatie weg is als je de browser sluit of naar een andere website gaat. Je bezoeker zal dus elke keer dat hij of zij terugkomt opnieuw het formulier moeten invullen.

We kunnen dat voorkomen door de informatie op te slaan in cookies (het Engelse woord voor koekjes).

Zet deze code bovenaan in resultaten.php:

{{< highlight php >}} 
	<?php
	  $_COOKIE['bezoek']++;
	  setcookie('bezoek', $_COOKIE['bezoek']);
	?>
	
{{< /highlight >}} 
			
Het werkt alleen als je deze code vóór <html> zet, dus dat er niks voor de code naar de browser wordt gestuurd om te laten zien.
Zet nu deze regel onderaan de pagina, net boven </body>:
{{< highlight html >}} 
	<small>
	  Je hebt deze pagina nu <?=$_COOKIE['bezoek']?> keer bekeken.
	</small>
	
{{< /highlight >}} 

[de <small>-code maakt de tekst iets kleiner dan de rest]

Vernieuw de pagina een paar keer en je zult zien dat de informatie uit de cookie steeds opnieuw wordt bijgewerkt en onthouden.

Zoals het er nu staat, wordt de cookie ook weer weggegooid als de bezoeker de browser afsluit. Als je wil dat hij of zij de informatie nog wat langer zal kunnen zien, dan moet je de cookie zo opslaan:
{{< highlight php >}} 
	setcookie('bezoek', $_COOKIE['bezoek'], time() + 600000);
	
{{< /highlight >}} 
			
Op die manier blijft de informatie bewaard tot 600.000 seconden na nu, oftewel een week.

### Informatie bewaren: tekstbestandjes
Als we echt een vriendenboek willen maken, dan moet de site informatie kunnen opslaan, zodat jij de informatie van je vrienden ook kunt lezen.

Programmeurs die websites bouwen, gebruiken meestal een database om informatie te bewaren, maar je kunt daar ook een simpel tekstbestandje voor gebruiken.

Dat werkt als volgt. In resultaten.php, onder de regel met setcookie, zetten we de antwoorden uit het formulier achter elkaar en zetten we die in een tekstbestandje:

{{< highlight php >}} 
	$tekstbestandje = '/tmp/vrienden.txt';
	$antwoorden = 
	  $_REQUEST["naam"] . ";" .
	  $_REQUEST["leeftijd"]  . ";" . 
	  $_REQUEST["lengte"] . "\n";  file_put_contents($tekstbestandje, $antwoorden, FILE_APPEND);
	  
{{< /highlight >}} 
			
[Met de punt (.) plakken we in PHP variabelen en tekst aan elkaar. De \n op het eind zorgt ervoor dat er na deze rij een nieuwe regel komt.]

[FILE_APPEND zorgt ervoor dat we steeds een nieuwe regel toevoegen aan het tekstbestandje, in plaats van dat de antwoorden het enige zijn dat erin komt te staan]

Voeg je eigen variabelen toe aan $antwoorden (die van de extra vragen die je in het formulier hebt gezet). Zorg er wel voor dat er steeds weer een puntkomma tussen komt te staan, want zo houden we de variabelen uit elkaar.

### Tekstbestand lezen
Nu gaan we een pagina maken waar je ziet wie jouw vragenlijst hebben ingevuld.

Ga bij CodeAnywhere naar File en klik op 'New file'. Zet deze code erin om het tekstbestand te lezen en te laten zien wat erin staat:

{{< highlight html >}} 
	<html>
	  <html>
	  <head>
	    <title>Vriendenboek van Jaap</title>
	  </head>
	  <body>
	    <h1>Vrienden</h1>
	
	    <?php
	    
	    $tekstbestand = fopen("/tmp/vrienden.txt", "r");
	    
	    while( ! feof($tekstbestand) ) {
	
	      $vriend = explode(";", fgets($tekstbestand));
	      echo $vriend[0] . " is " . $vriend[1] . " jaar en $vriend[2] cm lang.<br>";
	
	    }
	    
	    fclose($tekstbestand);
	    
	    ?>
	    
	  </body>
	</html>
	
{{< /highlight >}} 

[Het uitroepteken betekent 'niet', feof betekent 'het eind van het bestand' en fgets betekent 'haal een nieuwe regel van het bestand op'. Hier staat dus: laat een nieuwe regel zien zolang we nog niet onderaan het tekstbestand zijn.]

[Met 'explode' hakken we de regel in stukjes. Waar een puntkomma staat begint een nieuwe variabele. $vriend wordt zo een lijst en dat noemen we in PHP een array. De lijst is genummerd en begint bij 0, en daarom vinden we de naam met $vriend[0]. ]

Sla je nieuwe pagina op (File, en dan Save) en vul bij 'file name' in vrienden.php Klik daaronder op je naam en klik onderaan op Save. Klik weer op 'play'.

![](save-as-vrienden.png)

Ga naar je nieuwste pagina door achter het webadres /vrienden.php te zetten en op enter te drukken.

Het adres zou er ongeveer zo uit moeten zien:

	<sitenaam>/vrienden.php

Als je ziet wat je zelf daarstraks hebt ingevuld in het formulier, dan werkt het! Ga terug naar de eerste pagina om het formulier nog een paar keer in te vullen, om alles te testen.

### Jaren en dagen
Dit deel is nog niet af :(

	[Aantal dagen uitrekenen tot je verjaardag, hoeveel dagen je al leeft, hoeveel Saturnus-jaren je al bent, hoeveel dagen je ouder of jonger bent dan je vriend.
	> formulier aanpassen zodat we ook de dag van de maand en de maand hebben voor de geboortedatum
	> Datetime-object maken
	> link naar info over rekenen met data (zodat we ook leren hoe je documentatie over functies kunt vinden op PHP.org)
	]
			
### Hyperlinks
Dit deel is nog niet af :(

	[unordered list maken met voor elke vriend een aparte link naar een nieuw bestand, waar we alle info laten zien over die vriend op basis van de 
		meegegeven naam-parameter. Op die pagina moeten we dus met while en if bekijken welke regel van het bestand we moeten gebruiken.]
			
### Plaatjes maken met PHP
Dit deel is nog niet af :(

	[plaatje met lievelingskleur genereren
	> formulier aanpassen zodat we ook de lievelingskleur weten
	> 
			
### To do:
* een mail sturen met iemands eigen url (zou je ook kunnen doen als iemand jarig is of een nieuwe entry wordt gedaan)
* mensen in laten loggen met een wachtwoord
* tekst aanpassen aan of het ochtend of middag is
			
## Vervolg
Meer informatie:

* https://www.phphulp.nl/php/tutorial/overig/php-beginners-handleiding/575/variabelen/1482/
* https://www.phphulp.nl/php/tutorials/php-functies/6/
* https://www.w3resource.com/php-exercises/php-basic-exercises.php

{{< licentie rel="http://creativecommons.org/licenses/by-nc-sa/4.0/">}}
