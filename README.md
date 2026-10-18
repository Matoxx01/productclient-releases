# ProductClient - Releases

Este repositorio publico existe solo para alojar los **instaladores** de escritorio de
**ProductClient**, el panel de gestion de ProductBiss para el dueño del negocio. No contiene codigo
fuente: el codigo de la aplicacion y del sitio web se mantiene en repositorios privados.

## Descargar

La forma recomendada de descargar es desde el sitio oficial, que siempre ofrece la ultima version
(pestana **ProductClient**):

**https://productbiss.cl/descargar/**

Tambien puede bajar el instalador desde la seccion **Releases** de este repositorio.

## Que se publica aqui

| Plataforma | Archivo | Ejemplo |
| --- | --- | --- |
| Windows (64 bits) | Instalador `.exe` | `ProductClient-1.0.0-x64.exe` |
| macOS | Imagen de disco `.dmg` | `ProductClient-1.0.0-arm64.dmg` |

Las versiones para **Android** e **iOS** no se publican aqui: se distribuyen por Google Play y App Store.

## Instalacion

**Windows.** Ejecute el instalador. Mientras no este firmado digitalmente, Windows puede mostrar
**"Windows protegio su PC"**: continue con **Mas informacion** y luego **Ejecutar de todas formas**.

**macOS.** Abra el `.dmg` y arrastre la aplicacion a **Aplicaciones**. Si la aplicacion aun no esta
firmada ni notarizada por Apple, macOS pedira confirmacion la primera vez: abra la app con clic
derecho y **Abrir**.

## Para quien publica una version

El sitio web lee estas releases automaticamente; no hay que tocar el sitio al publicar.

1. Compile el instalador de cada plataforma. El de macOS solo se puede compilar en un Mac.
2. Cree **una sola release** con el numero de version como etiqueta (`v1.0.0`) y adjunte ahi los dos
   archivos. Esa etiqueta es la version que ve el visitante:

   ```bash
   gh release create v1.0.0 \
     "release/ProductClient-1.0.0-x64.exe" \
     "release/ProductClient-1.0.0-arm64.dmg" \
     --repo Matoxx01/productclient-releases \
     --title "ProductClient 1.0.0" \
     --notes "Cambios de esta version"
   ```

   Si el Mac se compila despues, se puede agregar a la misma release:
   `gh release upload v1.0.0 archivo.dmg --repo Matoxx01/productclient-releases`.
3. Las **notas** aceptan Markdown y se muestran en la pagina de descargas.

Reglas que el sitio aplica:

- Para **Windows** muestra la release mas reciente que traiga un `.exe`, y para **macOS** la mas
  reciente que traiga un `.dmg`. Cada plataforma se resuelve por separado.
- Si una release trae mas de un archivo del mismo tipo, usa el primero. Mantenga **un solo `.exe` y un
  solo `.dmg`** por release.
- **Ignora** los borradores y las releases marcadas como *pre-release*.
- Los cambios pueden tardar hasta unos 15 minutos en verse, por la memoria cache del servidor.

---

(c) ProductBiss. Todos los derechos reservados.
