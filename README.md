# uniclient2

Node.js util to watch your (or someone else) profit/loss on Uniswap market in real time. 

uniclient2.js is rewritten from scratch, using ethers.js instead of web3.js (so you have to install ethers.js). It reads logs from Ethereum node in batches, so it works with Infura and other similar services.

There's experimental fees calculation. I'm not 100% if it's done in a correct way. Fees are displayed as "Max profit", and calculated in ETH using last TOKEN/ETH ratio from the same exchange. Also total pool fees are calculated.

Edit file to add your ETH address and two nodes (which can can be the same) 

    const myAddress = ''; // put your address here
    
    let providerCurrent = new ethers.providers.JsonRpcProvider(''); //provider for current blocks, has to keep at least biteSize blocks
    let providerArchive = new ethers.providers.JsonRpcProvider(''); //provider for "old" blocks

You can also set `biteSize` constant to lower value if your node can't keep up with the requests volume. Default is too high for Infura.

Usage:

```./node uniswap2.js TOKEN```

Sample output:

![Sample output](https://i.imgur.com/eN0S8N6.png "Sample output")

IANAD (I'm not a developer), so use with care.
