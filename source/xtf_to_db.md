# Importar XTF a Base de datos PostgreSQL

<div class="warning">
<p class="admonition-title">WARNING</p>
<p>Recuerda installar las siguientes extensiones en tu base de datos.</p>
</div>

```
CREATE EXTENSION IF NOT EXISTS "postgis";
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
```

<a class="" data-lightbox="XTF to DB" href="_static/xtf_to_db.gif" title="XTF to DB" data-title="XTF to DB"><img src="_static/xtf_to_db.gif" class="align-center" width="1024px" alt="XTF to DB">
</a>

1. Dirigase en la barra de herramientas a `Base de datos` -> `Model Baker` -> `Import/Export Wizard`
2. Clic en `Choose data files and models to import or generate a new database`
3. En la interfaz que se despliega clic en los `tres puntos`, seleccione el archivo con extensión .xtf que va a importar y clic en el simbolo suma de color verde.
4. Clic en `Siguiente`.
5. Seleccione en el menú desplegable la opción `PostGIS`.
6. Ingrese los parametros de conexion de la base de datos.
7. Clic en `Siguiente`.
8. Verifique lo modelos a ser creador en la base de datos y el sistema de referencia.
9. Clic en `opciones avanzadas.`
10. En la opción Pre-script, realice clic en los `tres puntos` y seleccione el archivo `insert_ctm12_pg.sql`.
11. Clic en `Aceptar`
12. Clic en `Siguiente`.
13. Clic `Run all the ili2db sessions`.
14. Clic en `Siguiente`.
15. Seleccione los archivos a importar y clic en `Siguiente`.
16. Clic `Run all the ili2db sessions`.
17. Clic en `Siguiente`.
18. Clic en `Generar`.
19. Clic en `Finalizar`.


