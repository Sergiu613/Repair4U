# Scenarii de Utilizare (Use Cases)

## 1. Crearea unei comenzi de reparație
- **Actor:** Angajat
- **Descriere:** Angajatul înregistrează dispozitivul și problema.
- **Precondiții:** Angajatul este autentificat în aplicație cu rolul de "Angajat".

**Flux principal:**
1. Angajatul accesează panoul de control (Dashboard) și apasă butonul "Comandă nouă".
2. Sistemul afișează un formular de introducere a datelor.
3. Angajatul completează datele clientului (nume, număr de telefon) și detaliile dispozitivului (model, descrierea problemei).
4. Angajatul apasă butonul "Salvează comanda".
5. Sistemul validează datele introduse.
6. Aplicația creează o comandă de reparație.

**Rezultat așteptat:** Comanda este salvată în baza de date cu un ID unic și statusul inițial (ex: "Preluat"), iar angajatul este redirecționat către lista de comenzi.

---

## 2. Actualizarea stadiului unei reparații
- **Actor:** Angajat
- **Descriere:** Angajatul actualizează stadiul reparației.
- **Precondiții:** Angajatul este autentificat și se află pe pagina cu lista de comenzi.

**Flux principal:**
1. Angajatul selectează o comandă activă din listă.
2. Sistemul deschide detaliile comenzii respective.
3. Angajatul modifică statusul din meniul derulant (ex: din "Preluat" în "În lucru" sau "Finalizat").
4. Angajatul apasă "Actualizează status".
5. Sistemul înregistrează modificarea în baza de date.

**Rezultat așteptat:** Statusul comenzii este schimbat cu succes, fiind pregătit pentru a fi vizualizat de către client în timp real.

---

## 3. Verificarea stadiului reparației
- **Actor:** Client
- **Descriere:** Clientul poate vedea progresul reparației.
- **Precondiții:** Clientul deține un ID de comandă valid primit la predarea dispozitivului.

**Flux principal:**
1. Clientul accesează pagina publică de urmărire a aplicației.
2. Clientul introduce ID-ul comenzii în câmpul de căutare.
3. Clientul apasă butonul "Verifică status".
4. Sistemul caută în baza de date ID-ul respectiv.
5. Sistemul afișează detaliile dispozitivului și stadiul actual al reparației.

**Rezultat așteptat:** Informațiile solicitate sunt afișate pe ecran corect, fără a permite accesul la datele altor clienți.

---

## 4. Adăugarea unei piese în inventar
- **Actor:** Administrator
- **Descriere:** Administratorul adaugă piese și actualizează stocurile.
- **Precondiții:** Utilizatorul este logat cu rolul de "Administrator".

**Flux principal:**
1. Administratorul navighează la secțiunea "Inventar".
2. Apasă butonul "Adaugă piesă nouă".
3. Completează formularul cu denumirea piesei, cantitatea inițială și limita minimă pentru alertă de stoc.
4. Apasă "Salvează".
5. Sistemul adaugă noua înregistrare în baza de date.

**Rezultat așteptat:** Piesa apare în tabelul de inventar cu cantitatea specificată.

---

## 5. Alertarea privind stocul redus
- **Actor:** Sistem (pe baza acțiunilor Administratorului/Angajatului)
- **Descriere:** Aplicația semnalează piesele care sunt pe terminate.
- **Precondiții:** O piesă din inventar ajunge la o cantitate egală sau mai mică decât limita setată anterior.

**Flux principal:**
1. Un angajat scade o piesă din stoc în urma finalizării unei reparații.
2. Sistemul verifică noua cantitate a piesei.
3. Sistemul detectează că stocul a atins limita minimă.
4. Sistemul generează o alertă vizuală pe Dashboard-ul Administratorului (sau un tag "Stoc epuizat" în lista de inventar).

**Rezultat așteptat:** Administratorul este informat vizual că trebuie să lanseze o nouă comandă de aprovizionare pentru acea piesă.

---

## 6. Crearea unui cont nou de utilizator
- **Actor:** Administrator
- **Descriere:** Administratorul gestionează conturile și rolurile.
- **Precondiții:** Administratorul este autentificat în sistem.

**Flux principal:**
1. Administratorul accesează secțiunea "Management Utilizatori".
2. Apasă pe "Adaugă utilizator".
3. Introduce datele noului membru (nume, adresă de e-mail, parolă temporară).
4. Selectează rolul corespunzător (ex: "Angajat" sau "Administrator").
5. Apasă "Creează cont".
6. Sistemul salvează utilizatorul, setând permisiunile corespunzătoare rolului.

**Rezultat așteptat:** Contul este activ, iar noul angajat se poate autentifica în platformă folosind credențialele generate, având acces limitat conform rolului.