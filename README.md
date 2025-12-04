## doc_userhb24

```
npx antora playbook.yml
```

### INTERLIS Syntax Highlighting

`https://github.com/edigonzales/antora-ui-default.git` clonen (importiert von `https://github.com/edigonzales/antora-ui-default.git`). Die Datei `highlight.bundle.js` anpassen und `highlightjs-interlis.js` erstellen (aus Prims-File von _modelfinder_). Bundle erstellen:

```
npm install
npx gulp bundle
```

Die Datei `build-ui.zip` in das Doku-Repo kopieren und im `playbook.yml` referenzieren, z.B.:

```
ui:
  bundle:
    url: ./build/ui-bundle.zip   
    snapshot: true
```

Das Bundle kann natürlich auch irgendwo online gestellt werden.

### PlantUML
https://chatgpt.com/c/6931a1c9-a5d0-8333-aee7-3dc223af345f