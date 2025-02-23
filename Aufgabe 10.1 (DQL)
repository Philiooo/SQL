-- Tabelle

DROP TABLE Produkte CASCADE CONSTRAINTS;
DROP TABLE Kunden CASCADE CONSTRAINTS;
DROP TABLE Bestellungen CASCADE CONSTRAINTS;
DROP TABLE Mitarbeiter CASCADE CONSTRAINTS;

CREATE TABLE Produkte (
    ProduktID INT PRIMARY KEY,
    Produktname VARCHAR(100) NOT NULL,
    Preis DECIMAL(10, 2) NOT NULL,
    Menge INT,
    Herstellungsdatum DATE,
    Ablaufdatum DATE
);

CREATE TABLE Mitarbeiter (
    MitarbeiterID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Eintrittsdatum DATE,
    ArbeitsstundenWoche INT,
    Jahrestage INT
);

CREATE TABLE Kunden (
    KundenID INT PRIMARY KEY,
    MitarbeiterID INT,
    Vorname VARCHAR(50) NOT NULL,
    Nachname VARCHAR(50) NOT NULL,
    Geburtsdatum DATE,
    Registrierungsdatum DATE,
    FOREIGN KEY (MitarbeiterID) REFERENCES Mitarbeiter(MitarbeiterID)
);

CREATE TABLE Bestellungen (
    BestellID INT PRIMARY KEY,
    KundenID INT,
    ProduktID INT,
    Bestelldatum DATE,
    Lieferdatum DATE,
    FOREIGN KEY (KundenID) REFERENCES Kunden(KundenID),
    FOREIGN KEY (ProduktID) REFERENCES Produkte(ProduktID)
);

-- Produkte
INSERT INTO Produkte VALUES (1, 'Laptop', 899.99, 50, TO_DATE('2023-05-01', 'YYYY-MM-DD'), TO_DATE('2026-05-01', 'YYYY-MM-DD'));
INSERT INTO Produkte VALUES (2, 'Smartphone', 499.99, 100, TO_DATE('2024-01-01', 'YYYY-MM-DD'), TO_DATE('2027-01-01', 'YYYY-MM-DD'));
INSERT INTO Produkte VALUES (3, 'Kopfhörer', 79.99, 200, TO_DATE('2022-11-15', 'YYYY-MM-DD'), TO_DATE('2025-11-15', 'YYYY-MM-DD'));
INSERT INTO Produkte VALUES (4, 'Tischlampe', 29.99, 150, TO_DATE('2023-03-10', 'YYYY-MM-DD'), TO_DATE('2026-03-10', 'YYYY-MM-DD'));
INSERT INTO Produkte VALUES (5, 'Maus', 19.99, 300, TO_DATE('2024-06-20', 'YYYY-MM-DD'), TO_DATE('2027-06-20', 'YYYY-MM-DD'));

-- Mitarbeiter
INSERT INTO Mitarbeiter VALUES (1, 'Max Mustermann', TO_DATE('2020-06-15', 'YYYY-MM-DD'), 40, 30);
INSERT INTO Mitarbeiter VALUES (2, 'Anna Schmidt', TO_DATE('2018-04-10', 'YYYY-MM-DD'), 35, 28);
INSERT INTO Mitarbeiter VALUES (3, 'John Doe', TO_DATE('2022-09-01', 'YYYY-MM-DD'), 45, 35);
INSERT INTO Mitarbeiter VALUES (4, 'Maria Müller', TO_DATE('2019-11-23', 'YYYY-MM-DD'), 40, 33);
INSERT INTO Mitarbeiter VALUES (5, 'Peter Becker', TO_DATE('2021-02-10', 'YYYY-MM-DD'), 38, 25);

-- Kunden
INSERT INTO Kunden VALUES (1, 1, 'Tom', 'Müller', TO_DATE('1990-05-15', 'YYYY-MM-DD'), TO_DATE('2023-07-01', 'YYYY-MM-DD'));
INSERT INTO Kunden VALUES (2, 1, 'Anna', 'Schulze', TO_DATE('1985-08-22', 'YYYY-MM-DD'), TO_DATE('2022-12-10', 'YYYY-MM-DD'));
INSERT INTO Kunden VALUES (3, 2, 'Sarah', 'Meyer', TO_DATE('1995-01-05', 'YYYY-MM-DD'), TO_DATE('2024-01-05', 'YYYY-MM-DD'));
INSERT INTO Kunden VALUES (4, 2, 'Michael', 'Schmitt', TO_DATE('1989-11-30', 'YYYY-MM-DD'), TO_DATE('2021-04-23', 'YYYY-MM-DD'));
INSERT INTO Kunden VALUES (5, 3, 'Lena', 'Becker', TO_DATE('1992-02-17', 'YYYY-MM-DD'), TO_DATE('2023-09-15', 'YYYY-MM-DD'));

-- Bestellungen
INSERT INTO Bestellungen VALUES (1, 1, 3, TO_DATE('2023-08-01', 'YYYY-MM-DD'), TO_DATE('2023-08-05', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (2, 2, 1, TO_DATE('2023-12-01', 'YYYY-MM-DD'), TO_DATE('2023-12-10', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (3, 3, 3, TO_DATE('2024-01-10', 'YYYY-MM-DD'), TO_DATE('2024-01-12', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (4, 4, 1, TO_DATE('2021-05-15', 'YYYY-MM-DD'), TO_DATE('2021-05-20', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (5, 5, 5, TO_DATE('2023-11-18', 'YYYY-MM-DD'), TO_DATE('2023-11-22', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (6, 1, 1, TO_DATE('2023-09-10', 'YYYY-MM-DD'), TO_DATE('2023-09-15', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (7, 1, 5, TO_DATE('2023-11-06', 'YYYY-MM-DD'), TO_DATE('2023-11-03', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (8, 3, 1, TO_DATE('2024-01-17', 'YYYY-MM-DD'), TO_DATE('2024-01-15', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (9, 4, 3, TO_DATE('2021-06-20', 'YYYY-MM-DD'), TO_DATE('2021-06-25', 'YYYY-MM-DD'));
INSERT INTO Bestellungen VALUES (10, 5, 3, TO_DATE('2023-10-05', 'YYYY-MM-DD'), TO_DATE('2023-10-08', 'YYYY-MM-DD'));


--SELECT Abfragen

--Aufgaben:    A) Alle Kunden, die Bestellungen für ein Produkt aufgegeben haben, und alle Kunden, die nach dem 1. Januar 2024 registriert wurden. (Ohne doppelte Einträge) (Ausgabe: Vorname, Nachname) 
               B) Alle Produktnamen, die sowohl bestellt wurden als auch Produktnamen, die mehr als 100 Produkte  auf Lager haben. (Ohne doppelte Einträge) (Ausgabe: Produktname) 
               C) Alle Produktnamen, die sowohl bestellt wurden als auch Produktnamen, die mehr als 100 Produkte  auf Lager haben. (Mit doppelten Einträgen) (Ausgabe: Produktname) 
               D) Alle Kunden, die nach dem 1. Januar 2023 registriert wurden, aber keine Bestellungen für Produkte mit einem Preis unter 50 Euro gemacht haben. (Ausgabe: Vorname, Nachname)
               E) Alle Mitarbeiter, die mehr als 30 Arbeitsstunden pro Woche haben und Bestellungen für Produkte mit einem Preis über 50 Euro bearbeitet haben. (Ausgabe: Name) 


--A)
SELECT Kunden.Vorname, Kunden.Nachname FROM Kunden
WHERE Kunden.KundenID IN (SELECT BestellID FROM Bestellungen)
UNION
SELECT Kunden.Vorname, Kunden.Nachname FROM Kunden
WHERE Registrierungsdatum < TO_DATE('01.01.2024', 'DD.MM.YYYY'); 

--B) 
SELECT Produkte.Produktname FROM Produkte
WHERE Produkte.ProduktID IN (SELECT BestellID FROM Bestellungen)
UNION
SELECT Produkte.Produktname FROM Produkte
WHERE Menge > 100;

--C)
SELECT Produkte.Produktname FROM Produkte
WHERE Produkte.ProduktID IN (SELECT BestellID FROM Bestellungen)
UNION ALL
SELECT Produkte.Produktname FROM Produkte
WHERE Menge > 100;

--D)
SELECT Kunden.Vorname, Kunden.Nachname FROM Kunden
WHERE Registrierungsdatum > TO_DATE('01.01.2024', 'DD.MM.YYYY')
MINUS
SELECT Kunden.Vorname, Kunden.Nachname FROM Kunden
JOIN Bestellungen ON Bestellungen.KundenID = Kunden.KundenID
WHERE ProduktID NOT IN (SELECT ProduktID FROM Produkte WHERE Produkte.Preis > 50);

--E) 
SELECT Mitarbeiter.Name FROM Mitarbeiter
WHERE Mitarbeiter.ArbeitsstundenWoche > 30
UNION
SELECT Mitarbeiter.Name FROM Mitarbeiter
JOIN Kunden ON Kunden.MitarbeiterID = Mitarbeiter.MitarbeiterID
JOIN Bestellungen ON Bestellungen.KundenID = Kunden.KundenID
JOIN Produkte ON Produkte.ProduktID = Bestellungen.ProduktID
WHERE Produkte.Preis > 50;
