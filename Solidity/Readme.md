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
