# Jak věci fungují

Články s interaktivními modely. Každý článek je samostatná stránka ve vlastní složce, společné jsou jen `style.css` a `feedback.js`.

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
