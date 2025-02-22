-- Tabelle
DROP TABLE Studierende CASCADE CONSTRAINTS;
DROP TABLE Kurse CASCADE CONSTRAINTS;
DROP TABLE Aufgaben CASCADE CONSTRAINTS;
DROP TABLE Einreichungen CASCADE CONSTRAINTS;

CREATE TABLE Studierende (
    student_id INT PRIMARY KEY,
    vorname VARCHAR(50) NOT NULL,
    nachname VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    matrikelnummer VARCHAR(20) NOT NULL UNIQUE
);

CREATE TABLE Kurse (
    kurs_id INT PRIMARY KEY,
    kurs_name VARCHAR(100) NOT NULL,
    dozent VARCHAR(100) NOT NULL
);

CREATE TABLE Aufgaben (
    aufgabe_id INT PRIMARY KEY,
    kurs_id INT NOT NULL,
    aufgabe_titel VARCHAR(255) NOT NULL,
    aufgabe_beschreibung VARCHAR(255),
    abgabedatum DATE,
    FOREIGN KEY (kurs_id) REFERENCES Kurse(kurs_id)
);

CREATE TABLE Einreichungen (
    aufgabe_id INT NOT NULL,
    student_id INT NOT NULL,
    einreichung_zeitstempel TIMESTAMP NOT NULL,
    PRIMARY KEY (aufgabe_id, student_id),
    FOREIGN KEY (aufgabe_id) REFERENCES Aufgaben(aufgabe_id),
    FOREIGN KEY (student_id) REFERENCES Studierende(student_id)
);

INSERT INTO Studierende VALUES (1, 'Max', 'Mustermann', 'max.mustermann@email.de', '123456');
INSERT INTO Studierende VALUES (2, 'Anna', 'Schmidt', 'anna.schmidt@email.de', '123457');
INSERT INTO Studierende VALUES (3, 'Peter', 'Martin', 'peter.martin@email.de', '123458');

INSERT INTO Kurse VALUES (1, 'Datenbanken', 'Dr. Hans Meyer');
INSERT INTO Kurse VALUES (2, 'Algorithmen und Datenstrukturen', 'Prof. Dr. Anna Fischer');
INSERT INTO Kurse VALUES (3, 'Software Engineering', 'Dr. Martin Müller');
INSERT INTO Kurse VALUES (4, 'Künstliche Intelligenz', 'Prof. Dr. Julia Becker');
INSERT INTO Kurse VALUES (5, 'Webentwicklung', 'Dr. Klaus Schulz');

INSERT INTO Aufgaben VALUES (1, 1, 'Datenbankentwurf', 'Erstelle ein ER-Diagramm.', TO_DATE('2024-12-20', 'YYYY-MM-DD'));
INSERT INTO Aufgaben VALUES (2, 2, 'Sortieralgorithmus', 'Implementiere Sortieralgorithmen.', TO_DATE('2024-12-22', 'YYYY-MM-DD'));
INSERT INTO Aufgaben VALUES (3, 3, 'Projektplanung', 'Erstelle einen Projektplan.', TO_DATE('2024-12-25', 'YYYY-MM-DD'));
INSERT INTO Aufgaben VALUES (4, 4, 'Neural Network Training', 'Trainiere ein neuronales Netz.', TO_DATE('2024-12-28', 'YYYY-MM-DD'));
INSERT INTO Aufgaben VALUES (5, 1, 'Datenbankentwurf 2', 'Erstelle ein Relationenmodell.', TO_DATE('2024-12-30', 'YYYY-MM-DD'));

INSERT INTO Einreichungen VALUES (1, 1, TO_TIMESTAMP('2024-12-19 15:30:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO Einreichungen VALUES (2, 2, TO_TIMESTAMP('2024-12-21 16:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO Einreichungen VALUES (3, 3, TO_TIMESTAMP('2024-12-23 14:45:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO Einreichungen VALUES (4, 2, TO_TIMESTAMP('2024-12-27 13:00:00', 'YYYY-MM-DD HH24:MI:SS'));
INSERT INTO Einreichungen VALUES (5, 1, TO_TIMESTAMP('2024-12-29 17:15:00', 'YYYY-MM-DD HH24:MI:SS'));

COMMIT;

--SELECT Abfragen

--Aufgaben:    A)Alle Aufgaben, wo das Abgabedatum nach dem 20.12.2024 liegt. (Ausgabe: Aufgabe_ID, Aufgabe_Titel, Abgabedatum) 
               B) Alle Studierenden, wo der Nachname mit dem Buchstaben „M“ anfängt. (Ausgabe: Student _ID, Nachname) 
               C) Alle Dozenten, welche keine Professoren sind. (Ausgabe: Dozent, Kurs_Name) 
               D) Alle Aufgaben, welche die Dozenten Dr. Meyer und Dr. Müller gestellt haben. (Ausgabe: Aufgabe_ID, Aufgabe_Titel, Dozent)
               E) Wie viele Tage ist noch Zeit, bis die Aufgabe Datenbankentwurf 2 fällig ist? (Ausgabe: Aufgabe_Titel, Verbleibende_Tage) 
               F) Wie viele Einreichungen gab es nach 12:00:00 am 23.12.2024, je Kurs? (Ausgabe: Kurs_Name, Anzahl_Einreichungen) 
               G) Alle Einreichungen von dem Student mit der ID 2, welche nach dem 22.12.2024 liegen. (Ausgabe: Aufgabe_ID, Aufgabe_Titel, Student_ID, Einreichung_Zeitstempel) 
               H) Wie viele Tage, Stunden und Minuten liegen zwischen dem Abgabedatum der Aufgabe mit der ID 1 und der Einreichung des Studenten mit der ID 1? Tipp: Nutzen Sie die EXTRACT-Funktion! (Ausgabe: Differenz_in_Tagen, Differenz_in_Stunden, Differenz_in_Minuten) 
               I) Die Anzahl an Aufgaben, die der Student mit der ID 1 in dem Kurs Datenbanken eingereicht hat. (Ausgabe: Anzahl_Aufgaben)

--A) 
SELECT aufgabe_id, aufgabe_titel, abgabedatum
FROM Aufgaben
WHERE abgabedatum > TO_DATE('20.12.2024', 'DD.MM.YYYY');

--B)
SELECT student_id, Nachname
FROM Studierende
WHERE Nachname LIKE 'M%';

--C)
SELECT dozent, kurs_name
FROM Kurse
WHERE dozent NOT LIKE 'Prof%';

--D) 
SELECT Aufgaben.aufgabe_id, Aufgaben.aufgabe_titel, Kurse.dozent
FROM Aufgaben
JOIN Kurse ON Kurse.kurs_id = Aufgaben.kurs_id
WHERE Kurse.dozent IN ('Dr. Hans Meyer', 'Dr. Martin Müller');

--E)
SELECT Aufgaben.aufgabe_titel, (EXTRACT(DAY FROM abgabedatum) - EXTRACT(DAY FROM SYSDATE)) AS Verbleibende_Tage
FROM Aufgaben
WHERE Aufgaben.aufgabe_titel = 'Datenbankentwurf 2';

--F)
SELECT Kurse.kurs_name, COUNT(*) AS Anzahl_Einreichungen
FROM Kurse
JOIN Aufgaben ON Aufgaben.kurs_id = Kurse.kurs_id
JOIN Einreichungen ON Einreichungen.aufgabe_id = Aufgaben.aufgabe_id
WHERE Einreichungen.einreichung_zeitstempel > TO_DATE('23.12.2024 12:00', 'DD.MM.YYYY HH24:MI')
GROUP BY Kurse.kurs_name;

--G)
SELECT Aufgaben.aufgabe_id, Aufgaben.aufgabe_titel, Studierende.student_id, Einreichungen.einreichung_zeitstempel
FROM Einreichungen
JOIN Studierende ON Studierende.student_id = Einreichungen.student_id
JOIN Aufgaben ON Aufgaben.aufgabe_id = Einreichungen.aufgabe_id
WHERE Einreichungen.einreichung_zeitstempel > TO_DATE('22.12.2024', 'DD.MM.YYYY') AND Studierende.student_id = 2;

--H)
SELECT  EXTRACT(DAY FROM(Aufgaben.abgabedatum - Einreichungen.einreichung_zeitstempel)) AS Differenz_in_Tagen,
        EXTRACT(HOUR FROM(Aufgaben.abgabedatum - Einreichungen.einreichung_zeitstempel)) AS Differenz_in_Stunden,
        EXTRACT(MINUTE FROM(Aufgaben.abgabedatum - Einreichungen.einreichung_zeitstempel)) AS Differenz_in_Minuten
FROM Aufgaben
JOIN Einreichungen ON Einreichungen.aufgabe_id = Aufgaben.aufgabe_id
JOIN Studierende ON Studierende.student_id = Einreichungen.student_id
WHERE Aufgaben.aufgabe_id = 1 AND Studierende.student_id = 1;

--I)
SELECT COUNT(Aufgaben.aufgabe_id) AS Anzahl_Aufgaben
FROM Aufgaben
JOIN Kurse ON Kurse.kurs_id = Aufgaben.kurs_id
JOIN Einreichungen ON Einreichungen.aufgabe_id = Aufgaben.aufgabe_id
JOIN Studierende ON Studierende.student_id = Einreichungen.student_id
WHERE Studierende.student_id = 1 AND Kurse.kurs_name = 'Datenbanken';
