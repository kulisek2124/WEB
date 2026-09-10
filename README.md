# Advokátní kancelář Mgr. Ondřej Mičaník — web

Nový web kanceláře (Ostrava-Poruba). Statická stránka bez závislostí — stačí ji nahrát na jakýkoli hosting nebo zapnout GitHub Pages.

## Co je v repozitáři

| Soubor | K čemu slouží |
|---|---|
| `index.html` | Celý web: prezentace, právní služby, odměna, objednání na konzultaci, časté dotazy, kontakt + interní část (`#intranet`, ukázkový kód `1234`) |
| `og-image.png` | Obrázek, který se zobrazí při sdílení odkazu (Facebook, WhatsApp, Messenger…) |
| `favicon.svg`, `apple-touch-icon.png` | Ikona webu v prohlížeči a na ploše telefonu |
| `robots.txt` | Povolení pro vyhledávače i AI asistenty (Google, Seznam, Bing, ChatGPT, Claude, Perplexity) |
| `sitemap.xml` | Mapa webu pro vyhledávače |
| `llms.txt` | Stručný popis kanceláře ve formátu, který čtou AI asistenti |
| `.nojekyll` | Říká GitHub Pages, aby soubory servírovalo tak, jak jsou |

Ve stránce jsou vložená **strukturovaná data** (schema.org `LegalService`, `FAQPage`, `WebSite`): Google z nich čte adresu, telefon, oblasti práva a odpovědi na časté dotazy a může je zobrazit přímo ve výsledcích.

## Jak web zveřejnit

### 1. GitHub Pages (zdarma)
Settings → Pages → Build and deployment → Source: **Deploy from a branch** → Branch **main**, složka **/ (root)** → Save.
Web pak běží na `https://kulisek2124.github.io/WEB/`.

### 2. Vlastní doména `micanik-advokat.cz`
1. U registrátora domény nastav DNS:
   - `A` záznamy pro `micanik-advokat.cz`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` pro `www` → `kulisek2124.github.io`
2. V repozitáři vytvoř soubor `CNAME` s obsahem `www.micanik-advokat.cz` (nebo ho zadej v Settings → Pages → Custom domain) a zaškrtni **Enforce HTTPS**.
3. Po přesměrování domény už `index.html` obsahuje správné kanonické adresy (`https://www.micanik-advokat.cz/`), nic dalšího není potřeba měnit.

## Aby byl web k nalezení (Google, Seznam, AI)

Nejvíc pomůže těchto pět kroků, v tomto pořadí:

1. **Firemní profil na Googlu** (business.google.com) — zapsat kancelář jako *Advokát*, adresu Slavíkova 6068/18, telefon, web, otevírací dobu, pár fotek. Tohle je pro místní vyhledávání („advokát Ostrava“) zdaleka nejdůležitější.
2. **Google Search Console** (search.google.com/search-console) — ověřit doménu a odeslat `sitemap.xml`.
3. **Firmy.cz** (Seznam) a **Mapy.cz** — přidat firmu se stejnými údaji jako na Googlu (název, adresa a telefon musí být všude úplně stejně).
4. **Bing Places** — Bing pohání vyhledávání v ChatGPT a Copilotu.
5. Odkaz na web uvést v **seznamu advokátů ČAK** (vyhledavac.cak.cz) v profilu advokáta.

## Co je potřeba doplnit před ostrým provozem
- Evidenční číslo ČAK a IČ (zatím jen v Nastavení interní části) — doplnit do patičky `index.html`.
- Fotografie kanceláře / portrét (do úvodu a do Firemního profilu na Googlu).
- **Objednávky a interní část** zatím ukládají data jen do prohlížeče návštěvníka. Aby objednávky z webu skutečně dorazily do kanceláře a intranet fungoval z více zařízení, je potřeba malý backend (databáze + přihlášení + e-mailové upozornění). Vhodný další krok: Supabase nebo Firebase + jednoduchá funkce pro odeslání e-mailu.
- Informace o zpracování osobních údajů (GDPR) jako samostatný text.

## Úpravy
Všechny texty, právní oblasti i časté dotazy jsou přímo v `index.html` (oblasti v poli `AREAS`, dotazy v sekci `#dotazy`). Barvy a písmo jsou definované na začátku `<style>` v proměnných `--accent`, `--ground` atd.
