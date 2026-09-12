# Repo de extensiones para Tachiyomi 0.15.3 (extensions-lib 1.4)

Espejo mantenido de forma independiente del catalogo de extensiones que **todavia**
funciona en Tachiyomi 0.15.3, despues de que Keiyoushi migrara su repo a
`extensions-lib 1.6` y dejara de servir a los clientes 1.4.

## Como anadirlo en la app

Ajustes -> Buscar -> Repos de extensiones -> Anadir, y pegar la URL **base**
(sin `/index.min.json` al final):

```
https://raw.githubusercontent.com/Romano454/tachiyomi-ext-lib14/main
```

La app compone sola `<base>/index.min.json`, `<base>/apk/<archivo>.apk` y
`<base>/icon/<paquete>.png`.

## Por que existe

El `index.min.json` clasico de Keiyoushi devuelve hoy solo dos entradas ficticias
("Outdated App" y "Update to Mihon 0.20.1+"). Su indice real vive en `index.json`,
en un formato v2 que Tachiyomi 0.15.3 no entiende, y la mayor parte del catalogo ya
migro a `extensions-lib 1.6`, que el cargador de 0.15.3 rechaza
(`LIB_VERSION_MIN = 1.4`, `LIB_VERSION_MAX = 1.5`).

Este repo reexpone en formato v1 las extensiones que siguen en lib 1.4.

## Los APK no estan recompilados

Se copian **tal cual** desde las releases oficiales de Keiyoushi, con su firma
original intacta. Eso es deliberado: una firma distinta hace que Android rechace la
instalacion sobre una extension ya presente con
`INSTALL_FAILED_UPDATE_INCOMPATIBLE`. Manteniendo la firma original, las
actualizaciones se instalan encima sin desinstalar nada.

Las extensiones que reconstruyamos nosotros (correcciones de dominio, fuentes
recuperadas del historial) si van firmadas con clave propia, y esas **si** exigen
desinstalar la version anterior antes de instalarlas.

## Credito

Todo el codigo de las extensiones es de sus autores originales y de los
colaboradores de [keiyoushi/extensions-source](https://github.com/keiyoushi/extensions-source).
Este repo solo reempaqueta el indice; no reclama autoria alguna.
