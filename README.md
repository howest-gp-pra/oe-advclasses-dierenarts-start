# Oefening advanced classes : dierenarts - beginsituatie
In deze solution is reeds aanwezig : 
- een WPF project
- een class library

### De Class library Dierenarts.CORE

Deze bibliotheek bevat volgende klassen (de klassen zijn reeds aangemaakt maar je moet wel nog zelf de members toevoegen)

  - de (lege) klasse **Animal** : dit is de superklasse
  
    deze klasse dient over volgende eigenschappen te beschikken : 
    - Specie : string
    - Gender : byte, nullable  (null = onbekend, 0 = mannelijk, 1 = vrouwelijk)
    - DateOfBirth : datetime, nullable
    - Name : string
    - Breed : string
    
    deze klassen dient over 1 constructor te beschikken met dezelfde argumenten als de eigenschappen 
    
    deze klasse dient over de methode Age() te beschikken die een string retourneert met daarin de leeftijd van het dier (bv return $"{jaren} jaar, {maanden} maanden, {dagen} dagen";).  Om dit op te lossen bekijk je best even de TimeSpan struct van .Net.
    
    deze klasse dient de ToString() te overriden.
    Opgepast : (zie verder) gaat het om een vogel, dan wordt de soort en de roepnaam gegeven; gaat het om een zoogdier, dan wordt de soort, het ras en de roepnaam gegeven
    
    Deze klasse dient over een methode Summary() te beschikken die een lege string retourneert (de reden wordt straks duidelijk)
    
    Zorg er ten slotte voor dat de eigenschappen en de constructor enkel gebruikt kunnen worden door subklassen
    
  - de (lege) klasse **Mammal** : dit is een subklasse van *Animal*
    
    deze klasse heeft als bijkomende eigenschappen : 
    - Height : int
    - Sterilized : bool , nullable
    
    Voorzie hier een constrcutor die naast de eigenschappen van de basisklasse ook bovenstaande 2 eigenschappen ontvangt.
    
    Deze klasse heeft eveneens de methode Summary().
    Deze methode retourneert een stuk tekst dat later in onze WPF zal afgebeeld moeten worden.  Deze tekst zou er bijvoorbeeld als volgt moeten uitzien : 

      - Noor is een Hond van het ras Cocker Spaniel
      - Geslacht = vrouwelijk
      - Is gestereliseerd
      - Schofhoogte = 34
      - Geboren op 01/12/2008
      - Leeftijd = 11 jaar, 0 maanden, 6 dagen
 
     
  - de (lege) klasse **Bird** : dit is een subklasse van *Animal*

    deze klasse heeft als bijkomende eigenschappen : 
    - Width : int
    - CanFly : bool , nullable
    
    Voorzie hier een constrcutor die naast de eigenschappen van de basisklasse ook bovenstaande 2 eigenschappen ontvangt.
    Let wel, voor vogels wordt GEEN ras (breed) bijgehouden.  Bij het doorsturen van de argumenten naar de constructor van de basisklasse stuur je gewoon een lege string bij Breed.
    
    Deze klasse heeft eveneens de methode Summary().
    Deze methode retourneert een stuk tekst dat later in onze WPF zal afgebeeld moeten worden.  Deze tekst zou er bijvoorbeeld als volgt moeten uitzien : 

      - Marie is een Kip
      - Geslacht = vrouwelijk
      - Kan niet vliegen
      - Spanwijdte = 42
      - Geboren op 23/04/2012
      - Leeftijd = 7 jaar, 7 maanden, 15 dagen
 
   - de (reeds gemaakt) klasse **AnimalSpecies** 
      
      Deze klasse kan 2 arrays aanleveren met daarin de verschillende diersoorten die we bijhouden.
 
 In het WPF venster gaan we enkel het toevoegen van nieuwe dieren programmeren.  Uiteraard kan je dit programma nog zelf uitbreiden...
 
### Het WPF venster.
Het is de bedoeling dat ofwel een zoogdier ofwel een vogel wordt toegevoegd.
Wanneer op rdbMammal wordt geklikt dienen volgende zaken te gebeuren : 
- cmbSpecies dient gevuld te worden met de beschikbare zoogdieren (hond, kat, hamster, hangbuikvarken)
- lblBreed en txtBreed dienen zichtbaar te worden gemaakt
- lblHeightWidth dient voorzien te worden van de tekst "Schofhoogte"
- lblSterilizedCanFly dient voorzien te worden van de tekst "Gestereliseerd"

Wanneer op rdbBird wordt geklikt dienen volgende zaken te gebeuren : 
- cmbSpecies dient gevuld te worden met de beschikbare vogelsoorten (kip, kanarie, parkiet)
- lblBreed en txtBreed dienen onzichtbaar te worden gemaakt
- lblHeightWidth dient voorzien te worden van de tekst "Spanwijdte"
- lblSterilizedCanFly dient voorzien te worden van de tekst "Kan vliegen"

Wanneer op btnAdd wordt geklikt lees je de diverse controls uit, doe je eventueel wat foutcontrole en maak je het gepaste object aan.  Dit object voeg je meteen toe aan lstAnimals (je mag nog een List bijhouden, maar dat is op zich niet nodig gezien alle objecten ondergebracht worden in de listbox).

Wanneer een dier geselecteerd wordt in de listbox, dan dient in tbkSumary het resultaat van de methode Sumary() van het betrokken object te worden getoond.
