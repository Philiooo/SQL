DROP TABLE Mitarbeiter CASCADE CONSTRAINTS;

CREATE TABLE Mitarbeiter (
    MitarbeiterID INT PRIMARY KEY,
    Vorname VARCHAR(50),
    Nachname VARCHAR(50),
    Geburtsdatum DATE,
    Eintrittsdatum DATE,
    Abteilung VARCHAR(50),
    Gehalt DECIMAL(10, 2),
    Arbeitszeit INT -- in Stunden pro Woche
);

INSERT INTO Mitarbeiter VALUES (1, 'Anna', 'Müller', TO_DATE('1985-05-15', 'YYYY-MM-DD'), TO_DATE('2010-06-01', 'YYYY-MM-DD'), 'Marketing', 45000.00, 40);
INSERT INTO Mitarbeiter VALUES (2, 'Max', 'Schmidt', TO_DATE('1990-08-25', 'YYYY-MM-DD'), TO_DATE('2015-03-14', 'YYYY-MM-DD'), 'IT', 55000.00, 45);
INSERT INTO Mitarbeiter VALUES (3, 'Clara', 'Meier', TO_DATE('1982-12-30', 'YYYY-MM-DD'), TO_DATE('2012-07-23', 'YYYY-MM-DD'), 'Finanzen', 60000.00, 40);
INSERT INTO Mitarbeiter VALUES (4, 'Peter', 'Klein', TO_DATE('1995-02-10', 'YYYY-MM-DD'), TO_DATE('2020-01-20', 'YYYY-MM-DD'), 'HR', 40000.00, 40);
INSERT INTO Mitarbeiter VALUES (5, 'Eva', 'Schneider', TO_DATE('1988-07-05', 'YYYY-MM-DD'), TO_DATE('2018-09-12', 'YYYY-MM-DD'), 'Marketing', 47000.00, 35);
INSERT INTO Mitarbeiter VALUES (6, 'John', 'Doe', TO_DATE('1992-01-17', 'YYYY-MM-DD'), TO_DATE('2021-02-28', 'YYYY-MM-DD'), 'IT', 52000.00, 50);
INSERT INTO Mitarbeiter VALUES (7, 'Lena', 'Fischer', TO_DATE('1993-11-22', 'YYYY-MM-DD'), TO_DATE('2016-11-01', 'YYYY-MM-DD'), 'Finanzen', 62000.00, 40);

COMMIT;

--SELECT Abfragen

--Aufgaben:    A) Geben Sie nur den Vornamen, Nachnamen und das Gehalt der Mitarbeiter aus. 
               B) Geben Sie Vorname, Nachname und das monatliche Gehalt der Mitarbeiter aus.
               C) Geben Sie Vornamen, Nachnamen sowie die Länge des Vor- und Nachnamen der Mitarbeiter aus. 
               D) Geben Sie den Name der Abteilung, sowie die Summe der Gehälter pro Abteilung aus.
               E) Geben Sie die Gesamtanzahl der Mitarbeiter der Firma aus. 
               F) Geben Sie den Vorname, Nachname und das Jahr aus, indem der Mitarbeit der Firma beigetreten ist. 
               G) Geben Sie Vorname, Nachname, Geburtsdatum und das Alter des Mitarbeiters aus. 

--Aufgabe A
SELECT Vorname, Nachname, Gehalt 
FROM Mitarbeiter;

--Aufgabe B
SELECT Vorname, Nachname, Gehalt/12 AS Monatliches_Gehalt 
FROM Mitarbeiter;

--Aufgabe C
SELECT Vorname, Nachname, LENGTH(Vorname) AS Länge_Vorname, LENGTH(Nachname) AS Länge_Nachname 
FROM Mitarbeiter;

--Aufgabe D
SELECT Abteilung,SUM(Gehalt) AS Gehalt_pro__Abteilung
FROM Mitarbeiter
GROUP BY Abteilung;

--Aufgabe E
SELECT COUNT(MitarbeiterID) AS Anzahl_Mitarbeiter 
FROM Mitarbeiter;

--Aufgabe F
SELECT Vorname, Nachname, EXTRACT(YEAR FROM Eintrittsdatum) AS Eintrittsjahr
FROM Mitarbeiter;

--Aufgabe G
SELECT Vorname, Nachname, Geburtsdatum, (MONTHS_BETWEEN(SYSDATE, Geburtsdatum)/12) AS Age
FROM Mitarbeiter;


