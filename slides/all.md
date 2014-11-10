# Entity/Component
# Architecture

by sven freiberg



# Advanced Patterns


## Example - Parsing HTTP Headers

- Given a standard response headers, pull code and date out

```
HTTP/1.x 200 OK
Date: Sat, 28 Nov 2009 04:36:25 GMT
Expires: Sat, 28 Nov 2009 05:36:25 GMT
```

- `/(?:(HTTP)\/\d\.[a-z]|(Date|Expires):) (?(1)(\d+)|([A-Za-z ,\d:]+))/`



# Übersicht
- Motivation
- Aufbau
- Fazit
- Beispiel



# Motivation


## Engine Design

* Vereinfachte Darstellung
* Logik in `Update Loop`
* Anzeige in `Render Loop`


## Traditionelle Architektur
- 2 min

* GO (Game Object) mit unterschiedlichen Ausprägungen


## Traditionelle Architektur

![traditionell](/gfx/newfangled.png)


## Konsequenz
* Logik und Daten gemeinsam verwaltet
* Single Responsibility
* Problematisch bei Sprachen ohne Mehrfachvererbung


## Ableitung
- 2 min (4 min)

```java
class Spaceship
extends GameObject
implements IRenderable,
		   ICollidable,
		   IControlable {
	// ...
	@Override
	void onRender (Context ctx) {
		// ...
	}
}
```


## Ansatz

* Vermeiden von Vererbung
* Definition von Objekten per Komposition


## Komposition
- 2 min (6 min)

```java
class Spaceship
extends GameObject
implements IRenderable,
		   ICollidable,
		   IControlable {
	private
	Renderable renderable;
	private
	Collidable collidable;
	private
	Controlable controlable;

	@Override
	void onUpdate (float dt) {
		renderable.onUpdate (dt);
		collidable.onUpdate (dt);
	}
}
```


### Motivation
# Probleme
- 4 min (10 min)

* starr
* unflexible
* abhänigkeiten (tight cuppling)
* virtuelle funkionsüberladungsparty
* wo sollen objecte verwaltet werden?
* wer verwaltet was?


### Motivation
# Probleme
- 2 min (12 min)

spielearchitektur eher agil, anforderungen insbesonder in prototypenphase sehr wild


### Motivation
# Datenbank
- 2 min (14 min)

eigentlich ist spiel nur eine schöne representation von werten in einer datenbank



# Übersicht
- *Motivation*
- Aufbau
- Fazit
- Beispiel



# Aufbau


### Aufbau
## Fokus
- 2 min (16 min)

architektur daten getrieben


# Aufbau
# Elemente
- 2 min (18 min)

wichtige elemente
entities, components, systems, events


# Aufbau
## Entities
- 4 min (22 min)

entities oder game objects
nur ids (ähnlich wie in datenbank)


# Aufbau
## Components/Data
- 2 min (24 min)

componeten sind daten bzw ausprägungen (position, rotation, lebenspunkte, ki-state, renderinformation)


# Aufbau
## Systems/Processors
- 2 min (26 min)

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


# Beispiel
## Frameworks
- 2 min (28 min)

beispiele von implementierungen
dungeon siege 1 engine, arthemis framework, yanecos, unity engine


# Beispiel
## History
- 4 min (32 min)

historie
dungeon siege
	ziele eher richtung script sprache um reibung zu designern zu verringern
arthemis && yanecos
	relative dünne schicht
unity
	???


# Beispiel
## CODE !!?
- 4 min (36 min)
codebeispiel? || livedemo?
