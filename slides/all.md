# Entity/Component
# Architecture

by Sven Freiberg



# Übersicht
- Motivation
- Aufbau
- Fazit
- Beispiel



# Motivation


## Engine Design

* Vereinfachte Darstellung
* Logik in ```Update(dt)```
* Anzeige in ```Render()```
* Periodisch aufgerufen


## Traditionelle Architektur

* GO (Game Object) mit unterschiedlichen Ausprägungen


## Traditionelle Architektur

* GO (Game Object) mit unterschiedlichen Ausprägungen

![traditionell](/gfx/newfangled.png)


## Konsequenz

* Logik und Daten gemeinsam verwaltet
* Single Responsibility
* Problematisch bei Sprachen ohne Mehrfachvererbung


## Ableitung

```java
class Spaceship
extends GameObject
implements IRenderable,
		   ICollidable,
		   IControlable {
	// ...
	@Override void onRender (Context ctx) {
		// ...
	}
}
```


## Ansatz

* Vermeiden von Vererbung
* Definition von Objekten per Komposition


## Komposition

```java
class Spaceship
extends GameObject {
	private Renderable renderable;
	private Collidable collidable;
	private Controlable controlable;

	@Override void onUpdate (float dt) {
		renderable.onUpdate (dt);
		collidable.onUpdate (dt);
	}
}
```


## Probleme

* Wo sollen GOs verwaltet werden?
* Abhänigkeiten (tight cuppling) von Komponenten
* Überladungsparty wenn mehrere Ebenen
* Starre Architektur


## Probleme

* Designer werden sich kaum an Klassenstruktur halten wollen
* Anforderung werden mit Sicherheit geändert
* Meistens auch gravierendk (Prototyping)


## (Philosophischer) Ansatz

* Spiel ist Datenbank mit glitzernder Benutzeroberfläche



# Übersicht
- *Motivation*
- Aufbau
- Fazit
- Beispiel



# Aufbau


## Fokus

* Datengetrieben Architektur


## Ansatz

* Scott Bilas 2002 @ GDC
* Dungeon Siege
* Game Object System 


## Fokus

* Datengetrieben Architektur
* Näher an Designern
* Kein Software Ingenieur nötig
* Maximale Abstraktion von GOs
* Engine ist egal ob GO Monster oder Baum


## Elemente

* Grundelemente Elemente
	* Entities
	* Components
	* Systems
	* Events


## Entities

* Representation eines Game Objects
* Effektiv nur eine ID (ähnlich Datenbank)


## Entities

* Impelemntierung z.B. per Facade Pattern
* Erleichtert OOP Transition

```java
class Entity {
	private long id;
	private EntityManager mgr;

	//...
	public <T extends Data> void addData (final T someData) {
		mgr.addDataToEntity (this.id, someData);
	}
}
```


## Components/Data

* Beschreiben Ausprägung einer Entity
	* Position/Rotation
	* Lebenspunkte, Rüstung
	* Renderinformationen


## Components/Data

```java
class PhysicsComponent
extends Data {
	public int mass;
	public Vector3 velocity; 
}
```


## Systems/Processors

* Halt Logik verantwortlich für
	* Berechnung einer Komponente
	* Berechnung eine Gruppe von Komponenten



# Übersicht
- Motivation
- Aufbau
- *Fazit*
- *Beispiel*



# Fazit


### Pro
* Leicht erweiterbar
* Übersichtliche Abbildung Komplexer Kombinationen
* Zusammenstellen neuer Konstrukte aus bereits bestehenden
### Con
* Hoher initialer Aufwand
* Gewöhnen an datengetriebene Architektur
* Großer Overhead wenn starr datengetrieben



# Übersicht
- Motivation
- Aufbau
- Fazit
- *Beispiel*



# Beispiel


## Frameworks

beispiele von implementierungen
dungeon siege 1 engine, arthemis framework, yanecos, unity engine


## History

historie
dungeon siege
	ziele eher richtung script sprache um reibung zu designern zu verringern
arthemis && yanecos
	relative dünne schicht
unity
	???


## CODE !!?

codebeispiel? || livedemo?



# Referenzen

* Data-Driven Game Object System
	- Scott Bilas
	- http://scottbilas.com/files/2002/gdc_san_jose/game_objects_slides_with_notes.pdf
* Entity Systems are the future of MMOG development
	- Adam Martin
	- http://t-machine.org/index.php/2007/09/03/entity-systems-are-the-future-of-mmog-development-part-1/


# Referenzen

* Evolve your Hirachy (!)
	- Mick West
	- http://cowboyprogramming.com/2007/01/05/evolve-your-heirachy/
* Case Study: Bomberman Mechanics in an ECS
	- Philip Fortier
	- http://www.gamedev.net/page/resources/_/technical/game-programming/case-study-bomberman-mechanics-in-an-entity-component-system-r3159


# Referenzen

* Rogue Basins Wiki Entry
	- http://www.roguebasin.com/index.php?title=Entity_Component_System
* Wikipedia Entry
	- https://en.wikipedia.org/wiki/Entity_component_system
* Starcraft Screenshot
	- http://static.giantbomb.com/uploads/original/0/1468/184087-starcraft.png
