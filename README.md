# Jak věci fungují

Články s interaktivními modely.

## Co kde je

- `index.html` je rozcestník se všemi tématy.
- `clanky/<název>/index.html` jsou články. Každý je samostatná stránka s vlastním stylem a skriptem.
- `style.css` a `feedback.js` jsou společné pro rozcestník i články.
- `api/` jsou funkce pro zpětnou vazbu, `admin/` její administrace.
- `scripts/` je server pro lokální zkoušení.

Články dřív ležely přímo v kořeni webu. Staré adresy (`/zamek/`) přesměrovává `vercel.json` na nové (`/clanky/zamek/`).

Web běží na Vercelu na adrese <https://jak-veci-funguji.vercel.app>. Každý commit do větve `main` se nasadí sám. Vedle stránek jsou ve složce `api/` dvě funkce, které přijímají zpětnou vazbu čtenářů a ukládají ji jako soubory JSON do úložiště Vercel Blob. Stránka `admin/` odpovědi po zadání hesla zobrazí.

## Nastavení na Vercelu

1. Projekt je připojený k tomuhle repozitáři, **Root Directory** je prázdný.
2. V levém menu projektu Storage: úložiště **Blob** s přístupem **Private**, připojené k projektu.
3. V levém menu projektu Environment Variables: `ADMIN_PASSWORD` (aspoň 8 znaků).
4. Po změně nastavení znovu nasadit (Deployments → Redeploy), jinak se neprojeví.

## Lokální zkoušení

```bash
npm run dev
```

Web i funkce běží na `http://localhost:8787`, odpovědi se ukládají do složky `.data`. Heslo do administrace si server vezme ze souboru `.env.local` (`ADMIN_PASSWORD=…`).
