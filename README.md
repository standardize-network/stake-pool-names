# stake-pool-names
Json files to map pool IDs and names for different Jörmungandr networks.

If you want to pull the JSON to your website, you can use NODEjs with axios. Code would look something like this:

```js
let pathToRawFile = 'https://raw.githubusercontent.com/standardize-network/stake-pool-names/master/stake-pools-official-nightly.json';

function getPoolnames() {
  let poolNames = await axios.get(pathToRawFile, {
    headers: {
      'Content-Type': 'application/json'
    }
  });
  console.log(poolNames.data);
}
```
