# Modelul de Date și API Endpoints

## 1. Structura bazei de date

Baza de date relațională conține urmatoarele tabele principale pentru a gestiona utilizatorii, comenzile de reparații și stocurile de piese.

### Tabelul: `Users`
Gestionează conturile și permisiunile de acces în aplicație.

| Câmp | Tip de date | Constrângeri | Descriere |
| :--- | :--- | :--- | :--- |
| `id` | INTEGER | PRIMARY KEY | Identificatorul unic al utilizatorului. |
| `nume` | TEXT | NOT NULL | Numele complet al utilizatorului. |
| `email` | TEXT | NOT NULL, UNIQUE | Adresa de e-mail folosită pentru autentificare. |
| `parola` | TEXT | NOT NULL | Parola contului (stocată sub formă de hash, nu în clar). |
| `rol` | TEXT | NOT NULL | Rolul utilizatorului (valori acceptate: `admin`, `angajat`, `client`). |

### Tabelul: `Orders`
Păstrează evidența tuturor reparațiilor preluate de service.

| Câmp | Tip de date | Constrângeri | Descriere |
| :--- | :--- | :--- | :--- |
| `id` | INTEGER | PRIMARY KEY | Identificatorul unic al comenzii. |
| `id_client` | INTEGER | FOREIGN KEY | Face legătura cu `id`-ul din tabelul `Users` (clientul căruia îi aparține dispozitivul). |
| `descriere_problema` | TEXT | NOT NULL | Detalii despre dispozitiv și defectul reclamat. |
| `status` | TEXT | NOT NULL | Stadiul reparației (ex: `Preluat`, `În lucru`, `Așteaptă piese`, `Finalizat`). |
| `data` | DATETIME | DEFAULT CURRENT_TIMESTAMP | Data și ora la care a fost creată comanda. |
| `udata` | DATETIME | DEFAULT CURRENT_TIMESTAMP | Data și ora la care a fost updatata comanda. |

### Tabelul: `Inventory` (Piese)
Ține evidența componentelor hardware disponibile în service.

| Câmp | Tip de date | Constrângeri | Descriere |
| :--- | :--- | :--- | :--- |
| `id` | INTEGER | PRIMARY KEY | Identificatorul unic al piesei. |
| `nume_piesa` | TEXT | NOT NULL | Denumirea componentei (ex: "Ecran iPhone 13", "Baterie Samsung"). |
| `id_categorie` | FOREIGN KEY | Face legătura cu `id`-ul din tabelul `Categorii` |
| `cantitate` | INTEGER | NOT NULL, DEFAULT 0 | Numărul de bucăți disponibile în stoc. |
| `limita_alerta` | INTEGER | NOT NULL | Pragul minim la care sistemul declanșează alerta de stoc redus. |

### Tabelul: `Categorii`
Ține evidența tipurilor componentelor hardware disponibile în service.

| Câmp | Tip de date | Constrângeri | Descriere |
| :--- | :--- | :--- | :--- |
| `id` | INTEGER | PRIMARY KEY | Identificatorul categoriei. |
| `categorie` | TEXT | NOT NULL | Denumirea categoriei (ex: "Laptop", "Smartwatch", "Smartphone", etc). |

---

## 2. Endpoint-uri

Backend-ul (Node.js + Express) expune următoarele rute pentru comunicarea cu interfața:

### 2.1 Preluarea tuturor comenzilor
- **Ruta:** `GET /api/orders`
- **Descriere:** Returnează lista completă a comenzilor de reparație din sistem.
- **Acces:** Doar pentru rolurile `admin` și `angajat`.
- **Răspuns de succes (200 OK):**
  ```json
  [
    {
      "id": 1,
      "id_client": 14,
      "descriere_problema": "Ecran spart iPhone 13",
      "status": "În lucru",
      "data": "2026-11-10T09:30:00Z"
      "update_data": "2026-11-10T09:30:00Z"
    }
  ]
  ```
### 2.2 Preluarea tuturor categoriilor
- **Ruta:** `GET /api/inventory/categories`
- **Descriere:** Returnează lista completă a categoriilor si id-urilor lor din sistem.
- **Acces:** Doar pentru rolurile `admin` și `angajat`.
- **Răspuns de succes (200 OK):**
  ```json
  [
    {
      "id": 3,
      "nume": "Laptop"
    }
  ]
  ```

### 2.3 Verificarea unei comenzi specifice
- **Ruta:** `GET /api/orders/:id`
- **Descriere:** Returnează detaliile și statusul actualizat pentru o singură comandă, pe baza ID-ului. 
- **Acces:** `client` (doar pentru comanda proprie), `angajat`, `admin`.

### 2.4 Adăugarea unei piese în inventar
- **Ruta:** `POST /api/inventory`
- **Descriere:** Adaugă o piesă nouă în tabelul `Inventory`.
- **Acces:** Doar pentru rolul `admin`.
- **Corp cerere (Body - JSON):**
  ```json
  {
    "nume_piesa": "Baterie Laptop Dell",
    "categorie": 3,
    "cantitate": 10,
    "limita_alerta": 2
  }
  ```

  ### 2.5 Adăugarea unei categorii
- **Ruta:** `POST /api/inventory/categories`
- **Descriere:** Adaugă o intrare nouă în tabelul `Categorii`.
- **Acces:** Doar pentru rolul `admin`.
- **Corp cerere (Body - JSON):**
  ```json
  {
    "nume_categorie": "Baterie Laptop Dell",
  }
  ```

### 2.6 Actualizarea statusului unei comenzi
- **Ruta:** `PUT /api/orders/:id/status`
- **Descriere:** Permite angajatului să modifice stadiul reparației (ex: din `În lucru` în `Finalizat`).
- **Acces:** Doar pentru rolul `angajat`.
- **Corp cerere (Body - JSON):**
  ```json
  {
    "status": "Finalizat"
  }
  ```
