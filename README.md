# Repair4U

## Descrierea proiectului
**Repair4U** este o aplicație web dedicată unui service de reparații pentru calculatoare și telefoane. Aceasta vine în sprijinul clienților care doresc să își repare dispozitivele. Aplicația ajută la organizarea și gestionarea comenzilor și a pieselor de schimb, oferind totodată clienților posibilitatea de a urmări stadiul reparației.

## Problema abordată
Service-urile de telefoane și calculatoare încă folosesc agende sau tabele Excel ca să țină evidența reparațiilor. Acest mod de lucru este învechit și poate duce la erori.

Din perspectiva clientului, problema este că își lasă dispozitivul în service și nu știe ce se mai întâmplă cu el. Astfel, ajunge să apeleze telefonic service-ul sau să meargă fizic pentru a afla stadiul reparației. Acest lucru înseamnă timp pierdut atât pentru clienți, cât și pentru angajați.

În plus, ca angajat, când notezi zeci de comenzi manual, e foarte ușor să uiți ce piese ai comandat, să încurci dispozitivele care trebuie reparate sau să întârzii reparațiile.

Aplicația Repair4U rezolvă exact aceste probleme. Mutăm toată organizarea în mediul online, transformăm munca angajaților într-una mai ușoară, iar clienților le oferim posibilitatea de a vizualiza stadiul reparației direct din aplicație.

## Obiective
1. **Preluarea și gestionarea comenzilor** într-o singură aplicație, ușor de folosit pentru angajați și clienți.
2. **Informarea rapidă a clienților** prin trimiterea constantă de e-mailuri cu stadiul reparației sau vizualizarea stadiului în cadrul aplicației
3. **Păstrarea evidenței stocurilor** pentru piesele de schimb, pentru a ști ce este disponibil și a primi alerte când stocurile sunt pe terminate
4. **Crearea mai multor roluri** (administrator, angajat, client), astfel încât fiecare persoană să aibă acces doar la anumite funcții

## Utilizatorii vizați
- Administrator
- Angajați
- Clienți

## Membrii echipei si responsabilitati
| Nume Prenume | Rol | Responsabilități |
| :--- | :--- | :--- |
| **Olar Sergiu Cătălin** | Team Leader & Frontend | Interfața web, Wireframes, Coordonare proiect |
| **Melniciuc Damaris Daiana** | Backend Developer | Logica serverului, API, Scenarii utilizare (Use-cases) |
| **Birdeanu Aaron** | Database & Backend | Modelul de date, Gestiune inventar, Cerințe tehnice |

## Funcționalități Propuse
**Obligatorii:**
* **Gestionarea comenzilor:** Angajatul înregistrează dispozitivul și problema și se creează automat o comandă de reparație
* **Urmărirea reparațiilor:** Angajatul actualizează stadiul lucrării, iar clientul poate vedea progresul acesteia
* **Gestionarea inventarului:** Administratorul adaugă piese și actualizează stocurile, aplicația semnalează piesele pe terminate
* **Gestionarea utilizatorilor:** Administratorul gestionează conturile și rolurile (acces restricționat per rol)

**Opționale:**
* Notificări prin e-mail la schimbarea stadiului reparației
* Rapoarte statistice despre comenzile finalizate și piesele utilizate

## Tehnologii Alese
* **Frontend:** React și CSS
* **Backend:** Node.js cu Express 
* **Bază de date:** SQLite 

## Documentație Proiect
* [Requirements](docs/requirements.md)
* [Use Cases](docs/use-cases.md)
* [Modelul de date](docs/data-model.md)
* [Arhitectura aplicației](docs/architecture.md)
* [Planul de implementare](docs/implementation-plan.md)
* [Wireframes](docs/wireframes/)