# FHI API Query Builder - Deployment Guide

## 📦 Hva du har

Du har nå en ferdig `index.html` fil som inneholder hele appen. Dette er en standalone HTML-fil som ikke trenger noen build-prosess eller dependencies.

## 🚀 Publiseringsalternativer

### 1. GitHub Pages (Anbefalt - Gratis og enkelt)

#### Steg-for-steg:

1. **Opprett et GitHub repository**
   - Gå til [github.com](https://github.com) og logg inn
   - Klikk på "New repository"
   - Gi det et navn, f.eks. `fhi-query-builder`
   - Velg "Public"
   - Klikk "Create repository"

2. **Last opp filen**
   
   **Alternativ A - Via GitHub web interface (enklest):**
   - I ditt nye repository, klikk "uploading an existing file"
   - Dra `index.html` inn i området
   - Klikk "Commit changes"

   **Alternativ B - Via Git kommandolinje:**
   ```bash
   git init
   git add index.html
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/DIN-BRUKER/fhi-query-builder.git
   git push -u origin main
   ```

3. **Aktiver GitHub Pages**
   - Gå til repository settings
   - Scroll ned til "Pages" i venstremenyen
   - Under "Source", velg "main" branch
   - Velg "/ (root)" som folder
   - Klikk "Save"

4. **Din app er nå live!**
   - Etter noen minutter vil appen være tilgjengelig på:
   - `https://DIN-BRUKER.github.io/fhi-query-builder/`

### 2. Netlify Drop (Enda enklere - ingen GitHub konto nødvendig)

1. Gå til [app.netlify.com/drop](https://app.netlify.com/drop)
2. Dra `index.html` inn i upload-området
3. Ferdig! Du får en URL som `https://random-name-123456.netlify.app`
4. (Valgfritt) Logg inn for å endre URL eller beholde siden permanent

### 3. Vercel (Rask og profesjonell)

1. Gå til [vercel.com](https://vercel.com)
2. Logg inn med GitHub
3. Klikk "Add New..." → "Project"
4. Importer ditt GitHub repository
5. Deploy! URL: `https://fhi-query-builder.vercel.app`

### 4. Cloudflare Pages (Gratis og raskt)

1. Gå til [pages.cloudflare.com](https://pages.cloudflare.com)
2. Logg inn
3. "Create a project" → "Connect to Git"
4. Velg ditt GitHub repository
5. Deploy!

### 5. Surge.sh (Via kommandolinje)

```bash
npm install -g surge
surge index.html
```

## 🔧 Oppdatering av appen

Når du vil gjøre endringer:

1. Rediger `index.html` lokalt
2. Test at den fungerer ved å åpne den i en nettleser
3. Last opp den nye versjonen:
   - **GitHub Pages**: Commit og push endringene
   - **Netlify**: Dra den nye filen til Netlify Drop igjen
   - **Vercel/Cloudflare**: Push til Git, auto-deployment kjører

## 🌐 Bruke eget domene

### For GitHub Pages:
1. I repository settings → Pages
2. Skriv inn ditt domene under "Custom domain"
3. Sett opp DNS hos din domeneleverandør:
   - Type: `CNAME`
   - Host: `www` (eller `@` for root)
   - Value: `DIN-BRUKER.github.io`

### For Netlify/Vercel/Cloudflare:
- Alle har enkle guides for å koble til eget domene i deres dashboards

## 📝 Tips

1. **Test lokalt først**: Åpne `index.html` i nettleseren din før du publiserer
2. **Bruk Git**: Hold versjonskontroll på koden din
3. **Gratis hosting**: Alle alternativene over er gratis for hobby-prosjekter
4. **HTTPS**: GitHub Pages, Netlify, og Vercel gir gratis HTTPS
5. **Zero configuration**: Ingen build-prosess nødvendig!

## 🐛 Feilsøking

### Siden vises ikke
- Sjekk at filen heter `index.html` (små bokstaver)
- Vent 2-3 minutter etter deployment
- Sjekk at GitHub Pages er aktivert i repository settings

### API fungerer ikke
- Åpne browser console (F12) for å se feilmeldinger
- Sjekk at du har internettforbindelse
- Verifiser at FHI API er oppe: https://statistikk-data.fhi.no/swagger/index.html

### Appen ser feil ut
- Tøm browser cache (Ctrl+Shift+R eller Cmd+Shift+R)
- Sjekk at hele `index.html` filen ble lastet opp korrekt

## 📧 Støtte

Hvis du trenger hjelp, sjekk:
- [GitHub Pages dokumentasjon](https://docs.github.com/en/pages)
- [Netlify dokumentasjon](https://docs.netlify.com/)
- [FHI API dokumentasjon](https://github.com/folkehelseinstituttet/Fhi.Statistikk.OpenAPI)

## ✨ Neste steg

Etter du har publisert appen, kan du:
- Legge til Google Analytics for å spore bruk
- Tilpasse fargene og designet
- Legge til flere features
- Dele linken med kollegaer!
