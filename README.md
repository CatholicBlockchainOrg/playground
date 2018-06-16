
# playground
A place for us to learn, experiment, and try things out

## projects

### Casino Ethereum
The tutorial for this project can be found [here](https://medium.com/@merunasgrincalaitis/the-ultimate-end-to-end-tutorial-to-create-and-deploy-a-fully-descentralized-dapp-in-ethereum-18f0cf6d7e0e)
This tutorial leads you through creating a fully functional dApp. In it you'll create a contract and deploy it on the Ropsten network, build a front-end  React application that interacts directly with that contract, and deploy the front-end on IPFS. Its pretty cool and great for getting experience building dApps.

#### Tutorial Errata

That being said. There were some challenges. The tutorial was updated in March, but still has quite a few sections that are out of date(understandable with how fast things are moving). Here were the issues I found. This was all found running Node V8 and building the front-end with Webpack 4.12. 

Note, the code in the casino-ethereum folder should work. It contains all the modifications mentioned below besides the ones that can not be controlled(i.e. installing webpack).

##### Errata
- *Finding the Contract Interface*
This has moved in the remix IDE. It is now under *Compile* tab. After clicking compile there is a *Details* button(The contract name should be to the left in a dropdown). Click *Details* and a screen should popup. Scroll down to the WEB3DEPLOY section. Find the line beginning with **var casinoContract...** The right hand side has the interface defined.

- *Building the front-end*
  -  Make sure webpack is installed
```npm i -g webpack webpack-cli```
  - Make sure the babel presets es-2015 and stage-2 have been install
```npm i --save-dev babel-preset-2015 babel-preset-stage-2```
  - Update the webpack.config.js file. First, find the *loader* property under modules. The loader property is no longer valid in Webpack 4. Its should be changed to *rules*. Next, remove the entry for *json-loader* under *rules*. It should be the last entry. It does not work(and isn't needed) for Webpack 4+. If its left the Webpack build will not work. The build will complain when it tries to transpile the json files in the *web3* module.  

