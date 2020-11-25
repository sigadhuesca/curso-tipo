# Instrucciones para publicar un libro con gitbook

Haz fork de este repo, ubicando la copia en la organización CATEDU.

## Añadiendo archivos

Crea una carpeta por cada capítulo y guarda en ellas los archivos .md que crees. Para que se generen debes enlazarlos en el archivo `SUMMARY.md`.

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

En el `FOOTER.md` concretamente las etiquetas `{{ book.title }}` y `{{ book.authors[0] }}`.

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