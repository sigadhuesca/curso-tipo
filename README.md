# Instrucciones para publicar un libro con gitbook

**Si estás actualmente** en la url https://github.com/catedu/curso-tipo/ clica en el botón verde arriba a la derecha "Use this template" y sigue los siguientes pasos. Si no creas este repositorio bajo el usuario `catedu` deberás [añadir un `PERSONAL_TOKEN_GITBOOK_ACTION`](https://docs.github.com/en/actions/reference/encrypted-secrets) para que la integración contínua funcione.

**Si estás ya en el repo** pasa al siguiente apartado.

## Añadiendo archivos

Crea una carpeta por cada capítulo y guarda en ellas los archivos .md que crees. [Aquí](https://markdown.es/sintaxis-markdown/) tienes una guía del formato Markdown. Para que se generen debes enlazarlos en el archivo `SUMMARY.md`. Puedes seguir el ejemplo prepoblado que ya viene con este repo.

## Editando FOOTER

Para cambiar los datos del footer hay que tocar dos archivos: `book.json` y `FOOTER.md`.

```js
// book.json
"variables": {
    "title": "__________",
    "authors": [
      "_____________",
      "________________"
    ],
    "collaborators": [
      {
        "name": "_________",
        "edited": "_____________"
      }
    ]
  },
```

En el `FOOTER.md` concretamente las etiquetas sólo habría que tocar `{{ book.authors[0] }}` si tuviéramos más de un autor.

## Integración contínua

En el archivo `.github/workflows/gitbook-action.yml`, da nombre al libro que quieres que se genere **sin especificar la extensión**.

```yml
  ...
    source_dir: .
    gitbook_pdf: true
    gitbook_pdf_name: <nombre-del-libro-sin-extension>
    gitbook_epub: true
    gitbook_epub_name: <nombre-del-libro-sin-extension>
    gitbook_mobi: true
    gitbook_mobi_name: <nombre-del-libro-sin-extension>
```

### ¡Y ya estás listo para publicar! 📣 📡

Cada vez que hagas push a la rama `master` volverá a generar los archivos estáticos en la rama gh-pages, quedando la versión web actualizada del libro publicada en la url https://`<nombre-de-la-cuenta>`.io/`<nombre-del-repo>` y las versiones en formato epub, pdf y mobi en las url https://github.com/`<nombre-de-la-cuenta>`/`<nombre-del-repo>`/raw/gh-pages/mybook/`<nombre-del-libro-sin-extension>`.`<formato>`
    
Por ejemplo, esta plantilla está disponible en formato web en https://catedu.github.io/curso-tipo/ y las versiones descargable quedan publicadas en las siguientes urls:
* https://github.com/catedu/curso-tipo/raw/gh-pages/mybook/curso-tipo.epub
* https://github.com/catedu/curso-tipo/raw/gh-pages/mybook/curso-tipo.mobi
* https://github.com/catedu/curso-tipo/raw/gh-pages/mybook/curso-tipo.pdf

## ¡Atención!

La generación de la versión actualizada tras cada push puede tardar hasta 15 minutos.
