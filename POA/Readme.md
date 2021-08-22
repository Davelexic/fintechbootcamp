# Proof of Authority Testnet

In this assignment I walked through how to set up a basic testnet including setting up two nodes, connecting a wallet and testing a transaction.

## Part One
1. The first step will be to set up two nodes. One will be doing the mining, or validations, the other will be talking to the outside world through a custom port. Initially we will have to download the tools necessary to create our testnet. With [Go Ethereum](https://geth.ethereum.org/) tools we will be able to create a proof of work network or a proof of authority network. For this exercise, we will be creating a proof of authority testnet, the the steps are essentially the same.
2. Once you have Geth tools downloaded you will navigate to the installed library using bash or your command terminal. Proof of Authority is used for private network and you need pre approved addresses prior to the genesis block being developed. So we will first create two nodes. In Geth tools run:
   *  ./geth --datadir node1 account new
   *  ./geth --datadir node2 account new
3. Make sure that you write down the addresses that are given for both nodes as they will be important.
    <img src= 'https://user-images.githubusercontent.com/26451572/130343050-cc3d5860-2ca7-48db-b3e4-c0f6c2755c78.png' width="700" height="100" />
4. With your nodes created its time to create your network along with your genesis block. In the Geth library, run the command:
 - `./puppeth` and follow the question prompts
 - Choose `Proof of Authority`
 - Paste both of your node address in for the sealer addresses
 - Then the again for the pre-funded addresses
 - Follow the rest of the prompts to your choosing
- once you are finished navigate to the `Manage exsisting genesis` and the export your genesis configuration
  * example configuration
<img src= 'https://user-images.githubusercontent.com/26451572/130343060-cff3ab7d-63d6-4116-876a-c9ffb8eccbe4.png' width="700" height="600" />
5. Now we need to initalize the nodes with the genesis file
- In the Geth library run:
    - `./geth --datadir node1 init networkname.json`
    - `./geth --datadir node2 init networkname.json`
6. Next we can have the nodes begin mining
   - Using seperate terminals navigate to the the geth library and then run:
   -   *  `./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock`
        *  `./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock`
<img src='https://user-images.githubusercontent.com/26451572/130343044-377beb22-faf5-457d-8157-3a0b1aad8ce7.png' width="1000" height="500" />

### you are now up and running

## Testing on MyCrypto

1. Open My Crypto and then click on `change network`
2. Click `Add Custom Node` then add your network information
3. Use `ETH` as your currency
4. click `Save and Use Custom Node`
<img src='https://user-images.githubusercontent.com/26451572/130343075-cbfd57df-c011-4a0f-b3d3-00eed1c68e95.png' width="400" height="400" />
5. You're now a billionaire!
<img src='https://user-images.githubusercontent.com/26451572/130343077-0498f5f2-0522-4f16-a8e3-b754ec22e4df.png' width="300" height="400" />
7. Now with your network connected you can test a transaction

<p float="left">
  <img src='https://user-images.githubusercontent.com/26451572/130343081-77af1f0d-495c-46e5-92ea-7ec8d415178e.png' width="300" height="400" />
   <img src="https://user-images.githubusercontent.com/26451572/130343089-c78a0bd0-20e9-4e2f-aeb1-9d27539432de.png" width="500" height="400" />
</p>
