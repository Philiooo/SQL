--Tabellen

DROP TABLE Tierheim_Mita CASCADE CONSTRAINTS;
DROP TABLE adoptiert CASCADE CONSTRAINTS;
DROP TABLE Adoptant CASCADE CONSTRAINTS;
DROP TABLE Tier CASCADE CONSTRAINTS;

CREATE TABLE Tierheim_Mita(
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
ALTER TABLE adoptiert ADD CONSTRAINT fk_adopt_mitarbeiter FOREIGN KEY (MitarbeiterID) REFERENCES Tierheim_Mita(MitarbeiterID);

INSERT INTO Tierheim_Mita VALUES (1, 'Max', 'Mustermann', 47000, 'M', 'Verwaltung');
INSERT INTO Tierheim_Mita VALUES (2, 'Anna', 'Schmidt', 57000, 'W', 'Geschäftsleitung');
INSERT INTO Tierheim_Mita VALUES (3, 'Michael', 'Miller', 52000, 'D', 'Marketing');
INSERT INTO Tierheim_Mita VALUES (4, 'Julia', 'Mayer', 48000, 'W', 'Tierpflege');
INSERT INTO Tierheim_Mita VALUES (5, 'Felix', 'Schulz', 49000, 'M', 'Verwaltung');
INSERT INTO Tierheim_Mita VALUES (6, 'Sophie', 'Wagner', 55000, 'W', 'Tierpflege');
INSERT INTO Tierheim_Mita VALUES (7, 'David', 'Becker', 51000, 'M', 'Marketing');
INSERT INTO Tierheim_Mita VALUES (8, 'Laura', 'Koch', 50000, 'D', 'Tierpflege');
INSERT INTO Tierheim_Mita VALUES (9, 'Simon', 'Hoffmann', 53000, 'M', 'Verwaltung');
INSERT INTO Tierheim_Mita VALUES (10, 'Lisa', 'Schneider', 56000, 'W', 'Tierpflege');


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
INSERT INTO adoptiert VALUES (2, 1, TO_DATE('2022-11-15', 'YYYY-MM-DD'), 6);
INSERT INTO adoptiert VALUES (10, 2, TO_DATE('2022-04-18', 'YYYY-MM-DD'), 7);
INSERT INTO adoptiert VALUES (5, 3, TO_DATE('2022-09-16', 'YYYY-MM-DD'), 7);
INSERT INTO adoptiert VALUES (6, 8, TO_DATE('2022-12-06', 'YYYY-MM-DD'), 7);

COMMIT;

--SELECT Abfragen

--Aufgaben:    A) Alle Adoptanten, die ein Tier bei einem Mitarbeiter aus dem Aufgabenbereich „Verwaltung“ adoptiert haben. (Ausgabe: Vorname, Nachname) 
               B) Alle Tiere, die mindestens zweimal adoptiert wurden. (Ausgabe: Name) 
               C) Alle Aufgabenbereiche, bei denen das Durchschnittsgehalt unter dem Durchschnittsgehalt aller Aufgabenbereiche liegt. (Ausgabe: Aufgabenbereich, Durchschnittsgehalt) 
               D) Alle Adoptanten, die mehr Adoptionen durchgeführt haben als der Durchschnitt aller Adoptanten. (Ausgabe: Vorname, Nachname, Anzahl_Adoptionen) 
               E) Der Mitarbeiter, der die meisten Tier vermittelt hat. Verwenden Sie den ALL-Operator. (Ausgabe: Vorname, Nachname, Vermittlungen) 

--A)
SELECT Adoptant.Vorname, Adoptant.Nachname
FROM Adoptant
WHERE AdoptantID IN (SELECT AdoptantID FROM adoptiert 
                    WHERE MitarbeiterID IN (SELECT MitarbeiterID FROM Tierheim_Mita 
                                            WHERE Aufgabenbereich = 'Verwaltung'));

--B)
SELECT Tier.Name
FROM Tier
WHERE TierID IN (SELECT TierID FROM adoptiert 
                GROUP BY TierID HAVING COUNT(*) >= 2);
                
--C)
SELECT Tierheim_Mita.Aufgabenbereich, AVG(Gehalt) AS Durchschnittsgehalt
FROM Tierheim_Mita
GROUP BY Tierheim_Mita.Aufgabenbereich
HAVING AVG(Gehalt) < (SELECT AVG(Gehalt) FROM Tierheim_Mita);

--D)
SELECT Vorname, Nachname, (SELECT COUNT(*) FROM adoptiert 
WHERE adoptiert.AdoptantID = Adoptant.AdoptantID) AS Anzahl_Adoptionen
FROM Adoptant
WHERE (SELECT COUNT(*) FROM adoptiert 
WHERE adoptiert.AdoptantID = Adoptant.AdoptantID) > (SELECT AVG(Adoptionen) FROM (SELECT COUNT(*) AS Adoptionen FROM adoptiert GROUP BY AdoptantID));

--E)
SELECT Vorname, Nachname, (SELECT COUNT(*) FROM adoptiert WHERE adoptiert.MitarbeiterID = Tierheim_Mita.MitarbeiterID) AS Vermittlungen FROM Tierheim_Mita
WHERE (SELECT COUNT(*) FROM adoptiert WHERE adoptiert.MitarbeiterID = Tierheim_Mita.MitarbeiterID) >= ALL 
      (SELECT COUNT(*) FROM adoptiert GROUP BY MitarbeiterID);
