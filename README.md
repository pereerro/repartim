# 🩰 A repartir sardanes!

Aplicació web interactiva de fitxer únic (*Single-File WebApp*) dissenyada per aprendre, entrenar i agilitzar el **càlcul mental del repartiment de sardanes** a contrarellotge.

Pots jugar-hi directament des de qualsevol navegador a través de GitHub Pages:  
👉 **[https://pereerro.github.io/repartim/](https://pereerro.github.io/repartim/)**

---

## 🎯 Com funciona el joc?

El joc planteja rondes ràpides de **60 segons** on es presenten les dades d'una tirada en curs:
* **Tira:** Nombre total de compassos de la tirada.
* **Pas:** Número de compàs dins la sèrie en què ens trobem.
* **Portem:** Nombre de compassos acumulats fins al moment.

L'objectiu del dansaire/repartidor és deduir la quantitat exacta de compassos restants fins al canvi i escollir la fórmula de tancament adient (*un dos*, *un tres*, *un quatre*, *un dos i un tres*, *3 dosos i un 3*, etc.) per cloure la tirada amb estil i, quan calgui, a la mateixa banda d'inici.

---

## 🧗 Nivells de Dificultat

L'aplicació compta amb 5 nivells d'aprenentatge progressiu:

* **🟢 Nivell A (Llargs sense banda):** Càlcul directe de l'acabament sense tenir en compte el costat de sortida.
* **🟡 Nivell B (Llargs amb banda):** Cal que la tirada acabi obligatòriament a la banda d'inici (aplicant la regla de compensació de dosos).
* **🟠 Nivell C (Llargs amagant números):** Les dades de la tirada desapareixen de la pantalla al cap de 3 segons. Entrena la memòria de treball i la concentració (pots tornar a consultar les dades a canvi d'una penalització de punts).
* **🔴 Nivell D (Llargs expert):** A més de triar la combinació d'acabament, en una segona fase cal calcular i indicar el compàs exacte del darrer canvi on s'ha de «dir» o cantar la sortida.
* **💀 Nivell E (Llargs mestre):** Per a repartidors consolidats. Les opcions es mostren barrejades aleatòriament, sense numeració de drecera de teclat i amb valors trampa al pas de dir en canvi.

---

## 🛠️ Característiques Tècniques

* **Arquitectura d'un sol fitxer:** Tot el funcionament (HTML5, CSS responsive i JavaScript modular ES6) està integrat dins un únic arxiu `index.html`. No requereix compiladors, Node.js ni eines de *build*.
* **Perfils locals i pseudònims:** Generador automàtic de noms d'usuari aleatoris (*Dansaire_Àgil_123*), assignació de comarca catalana i registre de millors marques personals a `localStorage`.
* **Rànquing Global (Top 100):** Connexió amb **Google Firebase Firestore** per consultar la classificació mundial i enviar les noves marques si entren al Top 100.
* **Seguretat i Integritat:** Integració amb **Firebase App Check** i **Google reCAPTCHA v3** per protegir el servei d'accessos fraudulents.
* **Privacitat i Mode Local:** Inclou bàner de consentiment. Si es rebutgen els serveis externs, el joc continua sent plenament funcional en mode local sense connectar-se al núvol.
* **Accessibilitat:** Dreceres de teclat (tecles de l'1 al 8) per respondre sense ratolí i selector de tema Clar / Fosc.

---

## 🚀 Desplegament Local o en Servidor (Docker)

En ser un fitxer estàtic pur, es pot allotjar en qualsevol servidor web (Apache, Nginx, Caddy) o executar com a contenidor Docker.

Exemple de `docker-compose.yml` amb Nginx Alpine:

```yaml
services:
  sardanes-web:
    image: nginx:alpine
    container_name: sardanes-web
    restart: unless-stopped
    ports:
      - "8080:80"
    volumes:
      - ./:/usr/share/nginx/html:ro
