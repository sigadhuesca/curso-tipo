# Instrucciones para publicar un libro con gitbook

Haz fork de este repo

# Editando FOOTER

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

En el archivo `.github/workflows/gitbook-action.yml`, da nombre al libro que quieres que se genere.

