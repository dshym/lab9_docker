# Dmytro Shymanskyi 93711 IIST6.3
## Laboratorium 9

### Uruchomienie projektu

1) `docker compose up -d` - uruchomienie kontenerów
2) otworzyć **localhost:8080**
3) do loginu używać: user: **root**, password: **root**

### Lista użytych poleceń

- `docker compose up -d` - uruchomić kontenery w tle
- `docker compose restart` - zrestartować kontenery
- `docker compose ps` - wyświelić listę kontenerów
- `docker compose stop` - zatrzymać kontenery
- `docker compose down -v` - Zatrzymaj i/lub zniszcz pojemniki i ich objętość

### Komentarze

**Nginx:

80:80 wskazuje, że chcemy zmapować port 80 naszej lokalnej maszyny (używany przez HTTP) na port kontenera.

**PHP:

Używamy sekcji *volumeny* aby zamontować folder src jako folder /var/www/php kontenera

Dodajemy Dockerfile dla php, ponieważ potrzebuje rozszerzenia pdo_mysql do odczytu z bazy danych MySQL.

Drugi wolumen wskazujący na folder lokalny, odnosi się do nazwanego wolumenu zdefiniowanego w sekcji, 
która znajduje się na tym samym poziomie co *services*.Taki wolumen jest nam potrzebny, ponieważ bez niego za każdym razem, gdy kontener usługi mysql jest niszczony, baza danych jest z nim niszczona. 
Aby było trwałe, zasadniczo mówimy kontenerowi MySQL, aby używał woluminu mysqldata do przechowywania danych lokalnie, przy czym lokalny jest domyślnym sterownikiem.

**PhpMyAdmin:

Mapujemy port 8080 maszyny lokalnej na port 80 kontenera. Wskazujemy, że kontener MySQL
powinien być uruchomiony i gotowy jako pierwszy za pomocą depend_on i ustawiamy hosta, z którym ma się łączyć phpMyAdmin za pomocą zmiennej środowiskowej
PMA_HOST



