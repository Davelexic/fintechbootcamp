# Proof of Authority Testnet

In this assignment I walked through how to set up a basic testnet including setting up two nodes, connecting a wallet and testing a transaction.

## Part One
1. The first step will be to set up two nodes. One will be doing the mining, or validations, the other will be talking to the outside world through a custom port. Initially we will have to download the tools necessary to create our testnet. With [Go Ethereum](https://geth.ethereum.org/) tools we will be able to create a proof of work network or a proof of authority network. For this exercise, we will be creating a proof of authority testnet, the the steps are essentially the same.
2. Once you have Geth tools downloaded you will navigate to the installed library using bash or your command terminal. Proof of Authority is used for private network and you need pre approved addresses prior to the genesis block being developed. So we will first create two nodes. In Geth tools run:
   *  ./geth --datadir node1 account new
   *  ./geth --datadir node2 account new
3. Make sure that you write down the addresses that are given for both nodes as they will be important.
    ![example node](2021-08-21-21-28-28.png)
4. With your nodes created its time to create your network along with your genesis block. In the Geth library, run the command:
 - `./puppeth` and follow the question prompts
 - Choose `Proof of Authority`
 - Paste both of your node address in for the sealer addresses
 - Then the again for the pre-funded addresses
 - Follow the rest of the prompts to your choosing
- once you are finished navigate to the `Manage exsisting genesis` and the export your genesis configuration
  * example configuration
![](2021-08-21-21-37-31.png)
5. Now we need to initalize the nodes with the genesis file
- In the Geth library run:
    - `./geth --datadir node1 init networkname.json`
    - `./geth --datadir node2 init networkname.json`
6. Next we can have the nodes begin mining
   - Using seperate terminals navigate to the the geth library and then run:
   -   *  `./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock`
        *  `./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock`
![example](2021-08-21-21-44-17.png)
### you are now up and running

## Testing on MyCrypto

1. Open My Crypto and then click on `change network`
2. Click `Add Custom Node` then add your network information
3. Use `ETH` as your currency
4. click `Save and Use Custom Node`
![](2021-08-21-21-54-26.png)
5. You're now a millionaire 
![](2021-08-21-21-55-06.png)
1. Now with your network connected you can test a transaction
![](2021-08-21-21-56-18.png)
![](2021-08-21-21-57-13.png)
