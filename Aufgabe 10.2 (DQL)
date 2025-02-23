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

--Aufgaben:    A) Alle Produkte, die in Bestellungen enthalten sind. (Ausgabe: ProduktID, Produktname) 
               B) Alle Kunden, die mehr als zwei Bestellung aufgegeben haben. (Ausgabe: KundenID, Vorname, Nachname)
               C) Alle Mitarbeiter, deren Arbeitsstunden pro Woche größer sind als der Durchschnitt. (Ausgabe: MitarbeiterID, Name, Eintrittsdatum, ArbeitsstundenWoche) 
  	           D) Alle Kunden, die Produkte bestellt haben, deren Ablaufdatum nach dem 01.06.2026 liegt. (Ausgabe: KundenID, Vorname, Nachname, BestellID, ProduktID)
               E) Alle Mitarbeiter, die mindestens einen Kunden betreuen. (Ausgabe: MitarbeiterID, Name) 
               F) Alle Bestellungen, bei denen das Bestelldatum nach dem Lieferdatum liegt. (Ausgabe: BestellID, KundenID, ProduktID, Bestelldatum, Lieferdatum) 
               G) Alle Kunden, die Produkte bestellt haben, deren Preis größer als 500 € ist. (Ausgabe: KundenID, Vorname, Nachname) 
               H) Alle Produkte, die nach dem 01.01.2024 bestellt wurden und deren Preis größer als der Durchschnittspreis aller Produkte ist. (Ausgabe: ProduktID, Produktname, Preis) 

--A)
SELECT Produkte.ProduktID, Produkte.Produktname 
FROM Produkte
WHERE ProduktID IN (SELECT Bestellungen.ProduktID FROM Bestellungen);

--B)
SELECT Kunden.KundenID, Kunden.Vorname, Kunden.Nachname
FROM Kunden
WHERE KundenID IN (SELECT Bestellungen.KundenID FROM Bestellungen WHERE BestellID < 2);

--C)
SELECT Mitarbeiter.MitarbeiterID, Mitarbeiter.Name, Mitarbeiter.Eintrittsdatum, ArbeitsstundenWoche
FROM Mitarbeiter
WHERE Mitarbeiter.ArbeitsstundenWoche > (SELECT AVG(ArbeitsstundenWoche) FROM Mitarbeiter);

--D) 
SELECT Kunden.KundenID, Kunden.Vorname, Kunden.Nachname, Bestellungen.BestellID, Bestellungen.ProduktID
FROM Kunden
JOIN Bestellungen ON Kunden.KundenID = Bestellungen.KundenID
WHERE Bestellungen.ProduktID IN (SELECT ProduktID FROM Produkte WHERE Ablaufdatum > TO_DATE('01.06.2026','DD.MM.YYYY'));

--E)
SELECT Mitarbeiter.MitarbeiterID, Mitarbeiter.Name
FROM Mitarbeiter
WHERE MitarbeiterID IN (SELECT MitarbeiterID FROM Kunden);

--F)
SELECT Bestellungen.BestellID, Kunden.KundenID, Produkte.ProduktID, Bestellungen.Bestelldatum, Bestellungen.Lieferdatum
FROM Bestellungen
JOIN Kunden ON Kunden.KundenID = Bestellungen.KundenID
JOIN Produkte ON Produkte.ProduktID = Bestellungen.ProduktID
WHERE Bestelldatum > Lieferdatum;

--G)
SELECT Kunden.KundenID, Kunden.Vorname, Kunden.Nachname
FROM Kunden
WHERE KundenID IN (SELECT KundenID FROM Bestellungen 
                  JOIN Produkte ON Produkte.ProduktID = Bestellungen.ProduktID 
                  WHERE Preis > 500);

--H)
SELECT Produkte.ProduktID, Produkte.Produktname, Produkte.Preis
FROM Produkte
WHERE ProduktID IN (SELECT ProduktID FROM Bestellungen WHERE Bestelldatum > TO_DATE('01.01.2024', 'DD.MM.YYYY'))
AND Preis > (SELECT AVG(Preis) FROM Produkte);


