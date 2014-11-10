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
* Überladungsparty
* Starre Architektur


## Probleme

* Anforderung werden mit Sicherheit geändert
* Meistens auch gravierendk (Prototyping)


## (Philosophischer) Ansatz

* Datenbank mit glitzerndem Interface



# Übersicht
- *Motivation*
- Aufbau
- Fazit
- Beispiel



# Aufbau


## Fokus

architektur daten getrieben


## Elemente

wichtige elemente
entities, components, systems, events


## Entities

entities oder game objects
nur ids (ähnlich wie in datenbank)


## Components/Data

componeten sind daten bzw ausprägungen (position, rotation, lebenspunkte, ki-state, renderinformation)


## Systems/Processors

system verantwortlich für bearbeitung, update von logik daten bzw anzeigen von render daten



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
