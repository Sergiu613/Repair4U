# Plan de implementare

## Justificarea tehnologiilor alese

Pentru a dezvolta, am ales tehnologii cu care echipa noastră a mai lucrat în trecut

* **Frontend: React.js și CSS**
  * **Justificare:** Am ales React pentru a construi o interfață rapidă și interactivă, iar CSS pentru designul paginilor. Motivul principal este că toți am mai lucrat cu ele si suntem familiarizați cu modul în care funcționează

* **Backend: Node.js cu framework-ul Express**
  * **Justificare:** Ne permite să folosim JavaScript și pe server, nu doar pe interfață. Am ales acest stack deoarece avem deja experiență practică cu Node.js și Express din alte proiecte

* **Baza de Date: SQLite**
  * **Justificare:** Este o bază de date relațională foarte simplă, care se salvează într-un singur fișier și nu necesită configurarea unui server separat

## Strategia de versionare

* **`main`** conține doar codul testat, stabil și funcțional
* **`dev` (development)** branch-ul principal de lucru unde se integrează toate funcționalitățile noi
* **Branch-uri de tip Feature**: Fiecare membru va lucra pe branch-uri individuale derivate din `dev`
  * `feature/sergiu` (Sergiu)
  * `feature/damaris` (Damaris)
  * `feature/aaron` (Aaron)

## Repartizarea responsabilităților

* **Olar Sergiu Cătălin (Team Leader & Frontend):** 
  * Se ocupă de structura proiectului, wireframe-uri și interfața web (React + CSS)
  * Va gestiona stările din frontend și conectarea interfeței la API-urile create de backend
* **Melniciuc Damaris Daiana (Backend Developer):** 
  * Construiește serverul în Node.js/Express
  * Implementează sistemul de rutare și endpoint-urile principale (pentru utilizatori și comenzi de reparații)
* **Birdeanu Aaron (Database & Features):** 
  * Configurează baza de date SQLite și creează tabelele necesare
  * Dezvoltă logica pentru inventarul pieselor și funcționalitățile opționale (notificări, rapoarte)

## Prioritizarea activităților și planul de implementare
| Etapă | Funcționalitate | Descriere pe scurt | Prioritate |
| :--- | :--- | :--- | :--- |
| **1** | **Sistem Login și Roluri** | Crearea conturilor (Administrator, Angajat, Client) cu drepturi diferite de acces pe pagini | Maximă |
| **2** | **Creare Comandă Nouă** | Angajatul înregistrează dispozitivul defect, datele clientului și problema reclamată | Maximă |
| **3** | **Urmărire Status Reparație** | Clientul verifică online în ce stadiu este dispozitivul său ("În lucru", "Așteaptă piese") | Ridicată |
| **4** | **Gestiune Inventar Piese** | Administratorul poate adăuga, edita sau șterge piesele de schimb din baza de date | Ridicată |
| **5** | **Alerte de Stoc Limitat** | Sistemul atenționează vizual angajații când o piesă ajunge la o cantitate minimă | Medie |
| **6** | **Notificări prin E-mail** | Trimiterea unui mesaj automat clientului în momentul în care reparația este finalizată | Scăzută |
| **7** | **Rapoarte de Activitate** | Generarea unui istoric vizual cu numărul de reparații finalizate în ultima lună | Scăzută |