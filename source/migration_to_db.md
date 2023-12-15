# Migrar información de Captura en Campo a Edición en oficina

Note: 

```
create extension postgis;
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
```

1. Dirigase en la barra de herramientas a `Base de datos` -> `Model Baker` -> `Import/Export Wizard`
2. Clic en `Export data from existing database`
3. En la interfaz que se despliega clic en los `tres puntos`, seleccione el archivo con extensión .gpkg que va a exportar.
4. Clic en `Siguiente`.
5. En la interfaz que se despliega clic en los `tres puntos`, nombre y seleccione el lugar donde deseá guardar el archivo con extensión .xtf.
6. Clic en `Siguiente`.
7. Clic en `Run all the ili2db sessions`.
8. Cuando el proceso termina clic en `Finalizar`.
9. Dirigase en la barra de herramientas a `Base de datos` -> `Model Baker` -> `Import/Export Wizard`
10. Clic en `Choose data files and models to import or generate a new database`
11. En la interfaz que se despliega clic en los `tres puntos`, seleccione el archivo con extensión .xtf que va a importar y clic en el simbolo suma de color verde.
12. Clic en `Siguiente`.
13. Seleccione en el menú desplegable la opción `PostGIS`.
14. Ingrese los parametros de conexion de la base de datos.
15. Clic en `Siguiente`.
16. Verifique lo modelos a ser creador en la base de datos y el sistema de referencia.
17. Clic en `opciones avanzadas.`
18. En la opción Pre-script, realice clic en los `tres puntos` y seleccione el archivo `insert_ctm12_pg.sql`.
19. Clic en `Aceptar`
17. Clic en `Siguiente`.
18. Clic `Run all the ili2db sessions`.
19. Clic en `Siguiente`.
20. Seleccione los archivos a importar y clic en `Siguiente`.
21. Clic `Run all the ili2db sessions`.
22. Clic en `Siguiente`.
23. Clic en `Generar`.
24. Clic en `Finalizar`.


