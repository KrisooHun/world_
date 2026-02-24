**Repository**: Verziókövetés alatt álló állományok halmaza.
**Fork**: Egy repository másolata más hozzáférési jogosultságokkal.
**Branch**: Egy repositoryn belüli fejlesztési ág.
**Commit**: Változtatások atomi egysége.
**A lokális repository és a remote repository összekapcsolása (egy út a sok közül):**

1. Létrehozzuk a felhőben pl. github-on a remote repository-t.
2. Klónozzuk azt a számítógépünk egy üres könyvtárjába: git clone url-cím
3. Klónozás után be kell lépni a klónozott könyvtárba: cd ujKonyvtar
4. Konfigurálnunk kell mappa szinten a git-et!
5. Létre kell hozni a projekthez szükséges állományokat, és el kell kezdeni (vagy folytatni) a fejlesztést.
6. Egy komolyabb feladat elvégzése után: git add .
7. Majd commit-olni kell: git commit -m „Message”
8. Szinkronizálni kell a lokális repositoryt és a remote repositoryt, majd fel kell tölteni a lokális repository-t a github-ra: git pull && git push

---

**Fontosabb parancsok**
A lista tartalmazza a **helyi (local)** és a **távoli (remote)** repository-val kapcsolatos parancsokat is.

---

## 🔧 **Helyi (local) műveletek**

### `git init`

- **Repo inicializálása** egy mappában (új `.git` mappa jön létre).
  
  ```bash
  git init
  ```

---

### `git status`

- Megmutatja a változások állapotát: mely fájlok módosultak, melyek nincsenek hozzáadva.
  
  ```bash
  git status
  ```

---

### `git add <fájl>` vagy `git add .`

- Fájl(ok) **hozzáadása a staging area-hoz** (előkészítés commithoz) snapshot készül.
  
  ```bash
  git add index.ts
  git add .  # Összes változtatás hozzáadása
  ```

---

### `git commit -m "Üzenet"`

- A staging area tartalmának **mentése (commit)** a repository történetébe. 

- A másodiknál az összes snapshot mentésre kerül a lokális adatbázisban (repository-ban)
  
  ```bash
  git commit my_file.txt -m "az első mentés"
  git commit -m "minden mentve"
  ```

---

### `git log`

- Az előző commitok listája.
  
  ```bash
  git log
  ```

---

### `git diff`

- Megmutatja a változtatásokat a munkakönyvtár és a staging area között.
  
  ```bash
  git diff
  git diff my_file.txt
  ```

---

## 🌐 **Távoli (remote) repository-val való kommunikáció**

### `git pull`

- **Frissíti a helyi repository-t** a távoli repository legfrissebb verziójára (fetch + merge).
  
  ```bash
  git pull
  ```

---

## 🚀 `git push` – Feltöltés távoli repóba

```bash
git push
```

## Egyszerre is kiadhatóak a parancsok:

```bash
git pull && git push
```

---

### `git clone <URL>`

- Egy távoli repository **lemásolása (klónozása)** a gépedre.
  
  ```bash
  git clone https://github.com/felhasznalo/projekt.git
  ```

---

## 🌿 **Branch-kezelés**

### `git branch`

- Meglévő branchek listázása, aktuális branch kiemelve.
  
  ```bash
  git branch
  ```

---

### `git branch <uj-branch>`

- Új branch létrehozása.
  
  ```bash
  git branch develop
  ```

- Új branch létrehozása **és** átváltás rá.
  
  ```bash
  git checkout -b develop
  git switch -c develop
  ```

---

### `git checkout <branch>`

- Átváltás egy másik branch-re.
  
  ```bash
  git checkout develop
  git switch develop
  ```

---

### `git merge <branch>`

- Egy másik branch változásainak **összeolvasztása** az aktuális branch-be.
  
  ```bash
  git merge develop
  ```

---

## 📌 Gyakori workflow (összefoglalás)

```bash
git clone <repo-url>            # Klónozás
git checkout -b uj-funkcio      # Új branch
# fejlesztés...
git add .                       # Módosítások hozzáadása
git commit -m "valami"          # Commit
git push -u origin new-branch   # Feltöltés a GitHubra
```

---

## ⚙️ `git config` – Konfigurációs beállítások

A `git config` segítségével állíthatod be a Git működését globálisan vagy projekt-szinten.

### 🔹 Név és e-mail beállítása (ez jelenik meg a commitokban)

```bash
git config --global user.name "Neved"
git config --global user.email "email@pelda.hu"
```

- `--global`: minden git projektre vonatkozik

- Ha csak egy adott projektre akarod megadni:
  
  ```bash
  git config user.name "Projekt Neved"
  git config user.email "projekt@email.hu"
  ```

---

### 🔹 Alapértelmezett szövegszerkesztő beállítása (pl. VS Code)

```bash
git config --global core.editor "code --wait"
```

---

### 🔹 Meglévő konfigurációk listázása

```bash
git config --list
```

---

### 🔹 Egy adott beállítás lekérdezése

```bash
git config user.name
```

---

### A git használatának bevált főbb lépései:

1. Üres remote repo létrehozása a github-on

2. git clone url-cím

3. Belépés a könyvtárba (cd klónozottKönyvtár) és git config ...

4. Fejlesztés, kódolás

5. git add, git commit, git pull && git push
   
   ### Hitelesítés több felhasználó esetén Windows-on
   
   A hitelesítési problémák elkerülése érdekében használjuk a **GitHub Personal Access Tokens** (PAT) azonosítást. A diákok létrehozhatnak saját PAT-t a GitHub-fiókjukban, és ezt használhatják a GitHub-on történő hitelesítéshez.
   
   #### 3. **Git Credential Cache Kikapcsolása
   
   ```bash
   git config --global --unset credential.helper ""  vagy
   git config --global --unset credential.helper
   ```
   
   #### Hogyan kapcsolhatod vissza?
   
   Futtasd a következő parancsot, hogy újra engedélyezd a Credential Manager-t:
   
   ##### Windows esetén:
   
   ```bash
   git config --global credential.helper manager
   ```
   
   Ez utasítja a Git-et, hogy a **Windows Credential Manager**-t használja a hitelesítési adatok tárolására.

---

#### Hogyan ellenőrizheted, hogy mi a jelenlegi beállítás?

Futtasd a következőt:

```bash
git config --global credential.helper
```

##### Kimenet:

- **`manager`**: A Credential Manager használatban van.
- **`""` (üres)**: A Credential Manager nincs használatban, minden parancsnál újra kéri a hitelesítési adatokat.

---

### PAT létrehozása Github-on:

Github:
Settings/Developer settings/Personal access token/Tokens (classic) --> Generate new token --> Generate new token (classic)
Másolni egy jegyzettömbbe, és eltenni biztonságos helyre (Github-on is egy privát projektben)

### Meghívó küldése a projektben való együttműködésre:

A meghívó a projekt sorában --> settings/collaborators --> Find collaborator
Meghívó érkezik a meghívotthoz.
You can accept or decline this invitation. Ide kattintani (linkre), és Accept -re, hogy elfogadd.
Innentől jogosult vagy a push-olásra!
A "cica" fejre kattintva látni fogod a projektjeid között a megosztottat is (más színű az ikonja)...  
A megosztó is egy más színű ikonnal látja a megosztott projektet.

### .gitignore fájlba azokat a neveket (mappanév, fájlnév) írjuk, amelyeket nem akarunk verziókövetésben részesíteni

```bash
# config.c fájlt nem követi
config.c
# a .txt kiterjesztésű fájlokat nem követi
*.txt
# a lib mappa tartalmát nem követi
lib/
# node_modules mappa tartalmát nem követi
node_modules
```
