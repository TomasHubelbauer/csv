# CSV

A quick function for generating CSV:

```js
function toCsv(/** @type {any[]} */ array) {
  const keys = array.reduce((a, c) => {
    const keys = Object.keys(c);
    for (const key of keys) {
      if (!a.includes(key)) {
        a.push(key);
      }
    }

    return a;
  }, []);

  const data = array.map(i => keys.map(k => i[k] !== undefined ? `"${i[k]}"` : '').join(',')).join('\n');
  return keys + '\n' + data + '\n';
}
```
