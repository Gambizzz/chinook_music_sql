# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


EXO 2 - CHINOOK MUSIC, QUESTIONS/RÉPONSES (2.2.3)
Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?
SELECT COUNT(*) FROM albums;
--> 347

Qui est l'auteur de la chanson "White Room" ?
SELECT artist FROM tracks WHERE title='White Room';
--> Eric Clapton

Quelle chanson dure exactement 188133 milliseconds ?
SELECT title FROM tracks WHERE duration=188133;
--> Perfect de Alanis Morissette

Quel groupe a sorti l'album "Use Your Illusion II" ?
SELECT artist FROM albums WHERE title='Use Your Illusion II';
--> Guns N Roses

Combien y a t'il d'albums dont le titre contient "Great" ?
SELECT * FROM albums WHERE title LIKE 'Great%';
SELECT COUNT(*) FROM albums WHERE title LIKE 'Great%';
--> 9

Supprime tous les albums dont le nom contient "music".
DELETE FROM albums WHERE title LIKE 'Music%';

Combien y a t'il d'albums écrits par AC/DC ?
SELECT * FROM albums WHERE artist = (SELECT artist FROM albums WHERE artist = "AC/DC");
SELECT COUNT(*) FROM albums WHERE artist='AC/DC';
--> 2

Combien de chanson durent exactement 158589 millisecondes ?
SELECT COUNT(*) FROM tracks WHERE duration=158589;
--> 0

Afficher tous les titres de AC/DC.
SQL :
SELECT title FROM tracks WHERE artist LIKE 'AC/DC%';
SELECT COUNT(*) FROM tracks WHERE artist LIKE 'AC/DC%';

Console :
Track.where(artist: "AC/DC")

Afficher tous les titres de l'album "Let There Be Rock".
Console :
Album.where(title:"Let There Be Rock")

Calcule le prix total de cet album ainsi que sa durée totale.
SELECT SUM(price) FROM tracks WHERE album = (SELECT album FROM albums WHERE title = "Let There Be Rock");
--> 549,45
SELECT SUM(milliseconds) FROM tracks WHERE album = (SELECT album FROM albums WHERE title = "Let There Be Rock");
--> 153084768 milliseconds

Calcule le coût de l'intégralité de la discographie de "Deep Purple".
SELECT SUM(price) FROM tracks WHERE album IN (SELECT album FROM albums WHERE artist = (SELECT artist FROM tracks WHERE artist = "Deep Purple"));
--> 549,45

Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist.
--> Pas fait