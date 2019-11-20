# stake-pool-names
Json files to map pool IDs and names for different Jörmungandr networks.

If you want to pull the JSON to your website, you can use NODEjs with axios. Code would look something like this:

```js
import axios from 'axios'

let pathToRawFile = 'https://raw.githubusercontent.com/standardize-network/stake-pool-names/master/stake-pools-official-nightly.json';

function getPoolNames() {
  let poolNames = await axios.get(pathToRawFile, {
    headers: {
      'Content-Type': 'application/json'
    }
  });
  console.log(poolNames.data);
};

getPoolNames();
```

## How Pool Metadata will be handled

**This is not yet implemented!**

### 4.2 Stake Pool Metadata
The stake pool registration certificate can contain a URL (up to **64** bytes), pointing to a JSON
object with the following content:

- A **Ticker** of 3-5 characters, for a compact display of stake pools in a wallet.
- A **Title/Name** of up to 50 characters.
- A Short **Textual Description**
- A URL to a **homepage** with additional information about the pool.
- A list of IP addresses and/or Domain Names of **public relay nodes** that the stake pool operator provides to contribute to the Cardano network.
- A set of **tags, keywords** that can be used to filter stake pools in the wallet UI. For example, a stake pool that gives their rewards to a charity might indicate this by using a “charity” tag. Other tags could specify the geographic location, or whether a pool is running on cloud infrastructure or a physcial server owned by the pool operator.

All characters in the metadata will be **UTF8** encoded. The metadata is restricted to have a size of
no more than **512** bytes.

## When your System is compromised

### 2.2.4 Mitigate Key Exposure

A node run by a stake pool will need to have some key that controls all the delegated stake, inorder to sign blocks. In case of an incident where the node is compromised, it should be possible for the stake pool operator to revoke the key, and replace it with a new one. This should not require any action by the delegators.

#### Source

[delegation_design_spec.pdf](https://www.adatainment.com/_downloads/docs/delegation_design_spec.pdf)
