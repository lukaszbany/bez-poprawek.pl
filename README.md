# bez-poprawek.pl

Strona wizytówka „Bez Poprawek” (usługi hydrauliczne, Heating Systems sp. z o.o.). Statyczny HTML w `public/`.

- **Serwer:** VPS 192.109.241.30 (ten sam co heatingsystems.pl), Apache, katalog `/var/www/bez-poprawek.pl/public`, bez PHP.
- **Wgrywanie:** każdy push na `master` zmieniający `public/` → GitHub Actions (`.github/workflows/deploy.yml`) → rsync na serwer
  w ok. pół minuty. Ręcznie: zakładka Actions → „Wgranie bez-poprawek.pl” → Run workflow.
- **Konfiguracja serwera** (vhost, certyfikat, konto deploy): repozytorium `heatingsystems.pl-nowa`, katalog `serwer/`
  (`strona-dodaj.sh`, `strona-wgrywanie.sh`).

## Lokalnie

Wystarczy otworzyć `public/index.html` w przeglądarce. Adresy na serwerze są bez końcówki (`/polityka-prywatnosci`
→ `polityka-prywatnosci.html`), stare adresy `*.php` przekierowują na nowe (301).

## Historia

Do 11.2026 strona działała w Dockerze (PHP 7.2 + Apache za nginx) na VPS 185.238.73.18. Pliki `.php` nie zawierały kodu PHP,
więc po przeniesieniu mają końcówkę `.html`. Nieużywany `contact.php` (formularza nie było na stronie) został usunięty.
