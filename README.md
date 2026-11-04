# dattal.app — statický web (zásady súkromia + úvodná stránka)

Obsah tohto priečinka je celý web `https://dattal.app`:

- `index.html` — úvodná stránka (EN + SK, odkazy na zásady a podporu)
- `privacy/index.html` — zásady ochrany súkromia (EN + SK, prepínač jazyka; URL pre App Store Connect je `https://dattal.app/privacy/`)
- `CNAME` — vlastná doména pre GitHub Pages
- `.nojekyll` — GitHub Pages nemá spúšťať Jekyll

## Nasadenie cez GitHub Pages (zadarmo, HTTPS automaticky)

1. Na github.com založ **verejný** repozitár, napr. `dattal-site` (len tento priečinok, nie kód Dattalu).
2. Nahraj obsah tohto priečinka do koreňa repozitára (vrátane `CNAME` a `.nojekyll`).
3. Settings ▸ Pages ▸ Build and deployment: Source **Deploy from a branch**, Branch **main** / **(root)**, Save.
4. Settings ▸ Pages ▸ Custom domain: `dattal.app` → Save. Po overení DNS zaškrtni **Enforce HTTPS**
   (certifikát vystaví GitHub, trvá do hodiny).

## DNS na Websupporte (Admin ▸ Domény ▸ dattal.app ▸ DNS záznamy)

Zmaž pôvodný A záznam parkovacej stránky (37.9.175.133) a pridaj:

| Typ   | Názov | Hodnota                 |
|-------|-------|-------------------------|
| A     | @     | 185.199.108.153         |
| A     | @     | 185.199.109.153         |
| A     | @     | 185.199.110.153         |
| A     | @     | 185.199.111.153         |
| CNAME | www   | `<github-login>.github.io` |

MX záznamy (pošta) nechaj tak, ako ich nastavil Websupport.

Overenie: `dig +short A dattal.app` má vrátiť štyri adresy 185.199.*; potom
`https://dattal.app/privacy/` musí otvoriť zásady bez prihlásenia.

## dattal.sk

Stačí presmerovanie na `https://dattal.app` (Websupport: Admin ▸ Domény ▸ dattal.sk ▸ Presmerovanie).
GitHub Pages vie mať len jednu vlastnú doménu na repozitár, preto .sk nejde pripojiť rovnako.

## Aktualizácia zásad

Zdroj je tento priečinok (`Docs/site/privacy/index.html` v repe Dattalu). Po zmene skopíruj
súbor do repozitára webu a commitni — GitHub Pages ho zverejní do pár minút.
