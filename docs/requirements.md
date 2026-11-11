
## Cerințe funcționale

| ID | Cerință | Prioritate |
| :--- | :--- | :--- |
| CF-01 | Sistemul trebuie să permită autentificarea utilizatorilor cu e-mail și parolă și să aplice rolurile de administrator, angajat și client | High |
| CF-02 | Sistemul trebuie să permită angajatului să creeze o comandă de reparație cu datele clientului, tipul dispozitivului, marca, modelul și descrierea problemei | High |
| CF-03 | Sistemul trebuie să genereze un identificator pentru fiecare comandă și să permită angajaților să consulte, să caute și să filtreze comenzile după identificator, client sau status | High |
| CF-04 | Sistemul trebuie să permită angajatului să actualizeze statusul unei comenzi. Statusurile urmărite sunt: „Primită”, „În diagnosticare”, „În așteptare piese”, „În reparație”, „Finalizată” și „Predată” | High |
| CF-05 | Sistemul trebuie să permită clientului să consulte statusul și progresul comenzii sale folosind identificatorul comenzii | High |
| CF-06 | Sistemul trebuie să permită administratorului să adauge, să modifice și să șteargă piese de schimb și să actualizeze stocul și limita minimă pentru fiecare piesă | High |
| CF-07 | Sistemul trebuie să permită angajatului să înregistreze piesele folosite la o comandă, iar stocul disponibil trebuie actualizat corespunzător | High |
| CF-08 | Sistemul trebuie să semnaleze vizual piesele al căror stoc a ajuns la limita minimă sau a scăzut sub aceasta | Medium |
| CF-09 | Sistemul trebuie să permită administratorului să gestioneze conturile utilizatorilor și rolurile acestora, inclusiv dezactivarea unui cont | High |
| CF-10 | Opțional, sistemul poate trimite clientului o notificare prin e-mail când se schimbă statusul reparației | Low |
| CF-11 | Opțional, sistemul poate genera rapoarte despre comenzile finalizate și piesele utilizate | Low |

## Cerințe nefuncționale

| ID | Cerință | Prioritate |
| :--- | :--- | :--- |
| CNF-01 | Interfața trebuie să fie responsive și să poată fi utilizată pe desktop și pe telefon | High |
| CNF-02 | Parolele trebuie stocate ca hash-uri, nu în text | High |
| CNF-03 | Backend-ul trebuie să valideze identitatea și rolul utilizatorului la fiecare operație protejată | High |
| CNF-04 | Frontend-ul trebuie să comunice cu backend-ul prin cereri HTTP/REST și răspunsuri JSON | High |
| CNF-05 | Aplicația trebuie să folosească tehnologiile stabilite pentru proiect | Medium |