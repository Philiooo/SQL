-- Tabellen
DROP TABLE Mitarbeiter CASCADE CONSTRAINTS;
DROP TABLE adoptiert CASCADE CONSTRAINTS;
DROP TABLE Adoptant CASCADE CONSTRAINTS;
DROP TABLE Tier CASCADE CONSTRAINTS;

CREATE TABLE Mitarbeiter(
    MitarbeiterID NUMBER PRIMARY KEY,
    Vorname VARCHAR2(30) NOT NULL,
    Nachname VARCHAR2(30) NOT NULL,
    Gehalt NUMBER NOT NULL,
    Geschlecht CHAR(1) NOT NULL,
    Aufgabenbereich VARCHAR2(50) NOT NULL
);

CREATE TABLE Adoptant(
    AdoptantID NUMBER PRIMARY KEY,
    Vorname VARCHAR2(30) NOT NULL,
    Nachname VARCHAR2(30) NOT NULL,
    LieblingsTierArt VARCHAR2(20) NOT NULL,
    Alter_in_Jahren NUMBER NOT NULL
);

CREATE TABLE Tier(
    TierID NUMBER PRIMARY KEY,
    Name VARCHAR2(30) NOT NULL,
    Geburtsdatum DATE NULL
);

CREATE TABLE adoptiert(
    AdoptantID NUMBER NOT NULL,
    TierID NUMBER NOT NULL,
    Datum DATE NOT NULL,
    MitarbeiterID NUMBER NOT NULL,
    CONSTRAINT pk_adoptiert PRIMARY KEY (AdoptantID, TierID)
);

ALTER TABLE adoptiert ADD CONSTRAINT fk_adopt_tier FOREIGN KEY (TierID) REFERENCES Tier(TierID);
ALTER TABLE adoptiert ADD CONSTRAINT fk_adopt_adoptant FOREIGN KEY (AdoptantID) REFERENCES Adoptant(AdoptantID);
ALTER TABLE adoptiert ADD CONSTRAINT fk_adopt_mitarbeiter FOREIGN KEY (MitarbeiterID) REFERENCES Mitarbeiter(MitarbeiterID);

INSERT INTO Mitarbeiter VALUES (1, 'Max', 'Mustermann', 47000, 'M', 'Verwaltung');
INSERT INTO Mitarbeiter VALUES (2, 'Anna', 'Schmidt', 57000, 'W', 'Geschäftsleitung');
INSERT INTO Mitarbeiter VALUES (3, 'Michael', 'Miller', 52000, 'D', 'Marketing');
INSERT INTO Mitarbeiter VALUES (4, 'Julia', 'Mayer', 48000, 'W', 'Tierpflege');
INSERT INTO Mitarbeiter VALUES (5, 'Felix', 'Schulz', 49000, 'M', 'Verwaltung');
INSERT INTO Mitarbeiter VALUES (6, 'Sophie', 'Wagner', 55000, 'W', 'Tierpflege');
INSERT INTO Mitarbeiter VALUES (7, 'David', 'Becker', 51000, 'M', 'Marketing');
INSERT INTO Mitarbeiter VALUES (8, 'Laura', 'Koch', 50000, 'D', 'Tierpflege');
INSERT INTO Mitarbeiter VALUES (9, 'Simon', 'Hoffmann', 53000, 'M', 'Verwaltung');
INSERT INTO Mitarbeiter VALUES (10, 'Lisa', 'Schneider', 56000, 'W', 'Tierpflege');


INSERT INTO Adoptant VALUES (1, 'Laura', 'Müller', 'Hund', 30);
INSERT INTO Adoptant VALUES (2, 'David', 'Wagner', 'Katze', 25);
INSERT INTO Adoptant VALUES (3, 'Sophie', 'Schulz', 'Vogel', 40);
INSERT INTO Adoptant VALUES (4, 'Felix', 'Becker', 'Hamster', 22);
INSERT INTO Adoptant VALUES (5, 'Emma', 'Hoffmann', 'Kaninchen', 28);
INSERT INTO Adoptant VALUES (6, 'Simon', 'Schneider', 'Hund', 35);
INSERT INTO Adoptant VALUES (7, 'Julia', 'Koch', 'Schildkröte', 45);
INSERT INTO Adoptant VALUES (8, 'Max', 'Mayer', 'Katze', 32);
INSERT INTO Adoptant VALUES (9, 'Lisa', 'Schmidt', 'Fisch', 20);
INSERT INTO Adoptant VALUES (10, 'Michael', 'Hoffmann', 'Papagei', 50);


INSERT INTO Tier VALUES (1, 'Buddy', TO_DATE('2018-05-15', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (2, 'Mia', TO_DATE('2017-08-20', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (3, 'Charlie', TO_DATE('2019-02-10', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (4, 'Luna', TO_DATE('2016-12-05', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (5, 'Rocky', TO_DATE('2020-03-25', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (6, 'Mia', TO_DATE('2018-07-18', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (7, 'Simba', TO_DATE('2017-11-30', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (8, 'Oscar', TO_DATE('2020-01-08', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (9, 'Charlie', TO_DATE('2018-09-12', 'YYYY-MM-DD'));
INSERT INTO Tier VALUES (10, 'Maxi', TO_DATE('2019-06-08', 'YYYY-MM-DD'));


INSERT INTO adoptiert VALUES (1, 5, TO_DATE('2022-01-10', 'YYYY-MM-DD'), 2);
INSERT INTO adoptiert VALUES (1, 4, TO_DATE('2022-03-05', 'YYYY-MM-DD'), 1);
INSERT INTO adoptiert VALUES (3, 3, TO_DATE('2022-02-20', 'YYYY-MM-DD'), 3);
INSERT INTO adoptiert VALUES (4, 6, TO_DATE('2021-08-15', 'YYYY-MM-DD'), 4);
INSERT INTO adoptiert VALUES (7, 8, TO_DATE('2022-05-03', 'YYYY-MM-DD'), 5);
INSERT INTO adoptiert VALUES (7, 10, TO_DATE('2021-12-01', 'YYYY-MM-DD'), 6);
INSERT INTO adoptiert VALUES (10, 2, TO_DATE('2022-04-18', 'YYYY-MM-DD'), 7);
INSERT INTO adoptiert VALUES (5, 3, TO_DATE('2022-09-16', 'YYYY-MM-DD'), 7);
INSERT INTO adoptiert VALUES (6, 8, TO_DATE('2022-12-06', 'YYYY-MM-DD'), 7);

COMMIT;

--SELECT Abfragen

--Aufgabe: A) Alle Tiernamen in der Tier-Tabelle, ohne Dopplungen (Ausgabe: Name) 
           B) Alle Mitarbeiter, aber der Gehalt ist verdoppelt (Ausgabe: MitarbeiterID, Vorname, Nachname, Gehalt)
           C) Die Gesamtzahl der adoptierten Tiere (Ausgabe: Anzahl) 
           D) Die Gesamtzahl der adoptierten Tiere, aber mehrmals adoptierte Tiere werden nur einmal gezählt (Ausgabe: Anzahl) 
           E) Alle Mitarbeiter, die männlich sind (Geschlecht = „M“) und über 40.000€, aber unter 50.000€ verdienen. Absteigend sortiert nach dem Gehalt. (Ausgabe: MitarbeiterID, Vorname, Nachname, Gehalt, Geschlecht, Aufgabenbereich) 
           F) Alle Aufgabenbereiche mit dem Durchschnittgehalt für die Mitarbeiter, die für diese zuständig sind. (Ausgabe: Aufgabenbereich, Durchschnittsgehalt) 
           G) Alle Aufgabenbereiche mit der Anzahl der Mitarbeiter, die für diese zuständig sind. Es sollen nur Aufgabenbereiche mit mehr als 2 Mitarbeitern aufgeführt werden und die Anzahl soll aufsteigend sortiert sein. (Ausgabe: Aufgabenbereich, Anzahl_der_Mitarbeiter)


--A)
SELECT DISTINCT Name 
FROM Tier;

--B)
SELECT MitarbeiterID, Vorname, Nachname, Gehalt*2 AS Gehalt
FROM Mitarbeiter;

--C)
SELECT COUNT(*) AS Anzahl_Adoptionen
FROM adoptiert;

--D) 
SELECT COUNT (DISTINCT TierID) AS Anzahl
FROM adoptiert;

--E)
SELECT MitarbeiterID, Vorname, Nachname, Gehalt, Geschlecht, Aufgabenbereich
FROM Mitarbeiter
WHERE Geschlecht = 'M' AND Gehalt BETWEEN 40000 AND 50000
ORDER BY Gehalt DESC;

--F)
SELECT Aufgabenbereich, AVG(Gehalt) AS Durchschnittsgehalt
FROM Mitarbeiter
GROUP BY Aufgabenbereich;

--G) 
SELECT Aufgabenbereich, COUNT(MitarbeiterID) AS Anzahl_der_Mitarbeiter
FROM Mitarbeiter
GROUP BY Aufgabenbereich
HAVING COUNT(MitarbeiterID) > 2
ORDER BY Anzahl_der_Mitarbeiter ASC;




