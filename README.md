Download Link: https://assignmentchef.com/product/solved-comp302-assignment6-program-which-mimics-transactions-done-on-a-bank-account
<br>



<strong>[Question 1.  </strong>In class, we have shown you a program which mimics transactions done on a bank account. We will now develop an extended version of this example. For this we have first defined a data-type for transactions:

type transaction = Withdraw of int | Deposit of int | CheckBalance | ChangePassword of string | Close

We have added two new transactions to the example done in class.

In class, we defined a function make-account which generates a bank account when given an opening balance.

In this exercise, you are asked to modify this code and generate a password-protected bank account. Any transaction on the bank account should only be possible, if one provides the right password. For this, implement the function makeProtectedAccount with the arguments and types shown below.

val makeProtectedAccount : int * string -&gt; string * transaction -&gt; unit = &lt;fun&gt;

This function takes in the opening balance as a first argument and the password as a second, and will return a function which when given the <em>correct </em>password and a transaction will perform the transaction. One crucial difference to be noted right away is that in the new code I want you to <strong>print the balance on the screen </strong>instead of returning it as a value.

Here are some examples.

# let zoe = makeProtectedAccount(1000, “BiologyRocks”);; val zoe : string * transaction -&gt; unit = &lt;fun&gt;

# let elisa = makeProtectedAccount(500, “ArtsStudentsArePoor”);; val elisa : string * transaction -&gt; unit = &lt;fun&gt;

# let alison = makeProtectedAccount(2500, “MathIsTheBest”);; val alison : string * transaction -&gt; unit = &lt;fun&gt;

# elisa(“ArtsStudentsArePoor”, Withdraw 100);;

The new balance is: 400.- : unit = ()

# alison(“MathIsTheBest”, Deposit 200);;

1

The new balance is: 2700.- : unit = ()

# zoe(“BiologyRocks”, CheckBalance);; The balance is: 1000.- : unit = ()

# zoe(“BiologySucks”, Withdraw 100);;

Incorrect password.- : unit = ()

# zoe(“BiologyRocks”, Withdraw 1500);;

Insufficient funds.- : unit = ()

# elisa(“ArtsStudentsArePoor”, ChangePassword “CSwillMakeMeRich”);;

Password changed.- : unit = ()

# elisa(“ArtsStudentsArePoor”, Deposit 100);;

Incorrect password.- : unit = ()

# elisa(“CSwillMakeMeRich”, Deposit 200);;

The new balance is: 600.- : unit = ()

# alison(“MathIsTheBest”, Close);;

Account successfully closed.- : unit = () # alison(“MathIsTheBest”, CheckBalance);; Account closed.- : unit = ()