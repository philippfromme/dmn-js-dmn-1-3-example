# DMN 1.1 to 1.3 Migration Example

An example of using [dmn-js](https://github.com/bpmn-io/dmn-js) and [dmn-migrate](https://github.com/bpmn-io/dmn-migrate) to display both DMN 1.1 and DMN 1.3 diagrams.

## Migrating

This example uses dmn-js@8 which can only import DMN 1.3 diagrams. Therefore, DMN 1.1 diagrams have to be migrated to DMN 1.3 before they can be imported.

```javascript
const dmnModeler = new DmnModeler({
  container: '#canvas'
});

// (1) import DMN diagram
async function importXML(xml) {

  // (1.1) migrate to DMN 1.3 if necessary
  xml = await migrateTo13(xml);

  // (1.2) import DMN 1.3 diagram
  dmnModeler.importXML(xml, err => {
    if (err) {
      console.error(err);
    }
  });
}
```

## License

MIT