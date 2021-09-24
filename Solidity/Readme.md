### Solidity Homework 
#### Assoicate Profit Split

In this homework we are working on setting up a basic contract to automate payments through the blockchain. This will split the payments evenly inbetween the employees and then return the remaining to the sender.
1. First We define the public variables
  - employee _one
  - employee _two
  - employee _3
2. Then we created a cunstructor that accepts these functions
3. We then create the balance function that returns the contracts current balance. This will always return zero because we will return the remained to sender
4. Next, we created the deposit function. This splits the payments evenly between the three employee's in this contract.
5. To deal with the remained we take the msg.value and subtract the amount * 3. 
6. Finally, we creat a callback function to handle errors and make sure that the deposit function executes properly.
<img src="https://user-images.githubusercontent.com/26451572/134608221-f4045ba3-c313-4f31-a093-fb4c29379d66.png" width="400" height="600" />
<img src="(https://user-images.githubusercontent.com/26451572/134608204-699b6901-b73c-4e90-85d4-487110bceb34.png"/>
<img src="https://user-images.githubusercontent.com/26451572/134608149-d029d429-eba9-4b2a-ac7f-6cb8f670956c.png"/>
<img src="https://user-images.githubusercontent.com/26451572/134608130-89426236-6175-44a6-b50c-0a9e78783929.png"/>
