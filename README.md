# DL_CA_TWO
Distributed Ledgers - CA 2 - Solidity Project


Packaged Forward 

 

Variables:  

- buyer - wants to exchange currency 

- seller/market - holds the desired currency and will exchange 

- broker - intermediary, helps buyer access seller 

- start date - date to begin transactions 

- Spread - Fee can be paid upfront at a discount or with each transaction 

- base asset - held by the buyer before the transaction starts - foreign/local income 

- traded asset - desired asset received, at the end of the transaction, in trade for base asset held by the buyer 

- term - total number of transactions to be bundled 

- period - days between transactions (term * period = contract length in months) 

- quantity - amount per transaction 

- received or sent (is the fixed quantity to be received or sent) 

- Forward price per transaction 

 

This smart contract packages several forward contacts into a single product to stabilise long term currency exchange risk. 

The initial phase to write this contract is for a buyer to provide what currency they hold and what currency they want in exchange. They will also define what period of time they’d like to hedge their risk, how frequently they’d like to transact, and the fixed quantity of assets they’d either like to trade or receive. 

With that information, the program can go to the market and find the prices for all of those forwards, based on the dates defined by the start date/period, and package them together into a single product. 

If the terms are favourable and the buyer commits to the contract, then n number of transactions are written, where n is equal to the number defined in the ‘term’ of contract. 

For example, if John wants to send 1,000 TRY to his relatives every month and he earns Euros. He may decide he should hedge his exchange risk, so he can purchase a 6 month, 9 month, 1 year, 2 year, 5 year, etc... package where he will receive a guaranteed exchange rate every month, two weeks, or week, etc... so that he either knows exactly how much will be received every period, or if he wants a specific amount to be received each month, he will know exactly how much it will cost him for his relatives to receive 1,000 TRY. 

 

 

The writing of the smart contract will execute in a loop that does the following: 

For each iteration of creating a smart contract the loop should  

    - Multiply the period * iteration number and add it to the start date to define what date the iteration of the contract should execute 

    - It should then check the date of the transaction against the Forwards market for the base and traded exchange and return a price, based on the bid/ask or mid (which one is still to be determined) 

    - Define the buyer, seller, broker, base, traded, quantity, and whether the quantity is fixed on the send or receiving side of the transaction.  

    - Add the quantity sent and the quantity received and the rate to a list to be returned at the end of the transaction with some metrics to help illustrate the value of purchasing the product. 

    - Add the new transaction to the array of smart contracts 

    - If the fee (spread) is to be paid with each transaction, this loop will calculate the fee and create a transfer with each transaction to also pay the fee and add that smart contract to the array as well.  

    - If the fee is to be paid all at once, up front, then each loop will calculate the fee to create a sum which will receive a 15% discount at the end of the loop and add a single smart contract to execute immediately, assuming available funds. 

 

Each contract will have a date condition that checks to see if the maturity date on the contract matches the current date. If it does, then the contract will check the balance of the base account and if there are sufficient funds, execute, if not, it will continue to hold. 

 
