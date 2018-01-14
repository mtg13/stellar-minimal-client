# stellar-minimal-client

Download the code here: https://github.com/mtg13/stellar-minimal-client

Access the client here: https://mtg13.github.io/stellar-minimal-client/

Some of this README shamelessly copied from [minimalist-ripple-client](https://github.com/jatchili/minimalist-ripple-client).

## What is this?

This is a browser based client to access the Stellar network. To learn more about Stellar, visit [the Stellar website](https://www.stellar.org/how-it-works/stellar-basics/)

## You're asking for my secret key! Can I trust you?

We can make software more trustworthy either by making its components more trustworthy, or by eliminating as many components as possible. This client takes the latter approach.

What, then, do you still have to trust?

1. That GitHub will deliver the code faithfully (If you download it and run it locally, this is a one-time event)
2. That the SSL infrastructure is secure
3. That your computer/browser setup is trustworthy
4. That stellar-sdk is trustworthy (Compare the code [included here](https://github.com/mtg13/stellar-minimal-client/blob/master/index.html#L70-L89) with that [published by Stellar](https://github.com/stellar/bower-js-stellar-sdk); you should find that they're identical)
5. That the code I wrote (~250 lines) is trustworthy

Points #1-3 apply equally to any web application hosted on GitHub; #4 applies to any that uses stellar-sdk. As for #5: I encourage you to read the code. If there's a backdoor in there, it'll very quickly be found.

Also: If I were trying to steal from you, I'm doing a really bad job of it. It's very easy to figure out what my real name is

## How-to guide


### Where is my secret stored? How it is transmitted?

**Your secret is not stored anywhere** that persists once the window is closed\*. You ***MUST*** store it somewhere else - like in a text file and/or on paper - or else you'll lose access to your account!!!

Transactions are signed locally using stellar-sdk. Assuming that stellar-sdk is secure, your secret will never leave your computer.

\*Note: Depending on your browser, this may not be a cryptographically secure guarantee, since data might persist in memory even after the browser is closed. As a web developer I can't really do much about that. However, I can suggest that you use [Tor Browser](https://www.torproject.org/download/download), which does its best to clean up after itself on exit.

### What do buttons in the "Generate Address" section do?

The "Generate Address" button will ask the stellar-sdk to create a new account address and a secret key for you. You ***MUST*** store both of these somewhere - like in a text file and/or on paper. Without this information, any XLM stored in your account is ***LOST FOREVER***!!

Once you have stored your account address and secret somewhere, you may use the "Clear Address" button to erase them from the page.

### What does the "Get Address Balance" button do?

The "Get Address Balance" button will query the Stellar network to retrieve the information in the specified address. If the account is created and contains the minimum XLM balance (20 XLM as of 13 JAN 2018), the balances associated with the account is displayed in the text box underneath. The "native" asset denotes the XLM token. If not, an error will be displayed indicating that the account does not exist.

### How do I use the "Transfer XLM" functionality?


***You must have your account secret in order to transfer***

Enter your source address, source secret, destination address and amount and click on the "Execute Transfer" button. This will transfer the specified amount from the source address to the destination address. ***There will be no other confirmations***. If the destination account does not exist yet, you will receive a prompt letting you know that it will be created for you if you choose. In this case, you can choose to abort the operation. Please make sure to transfer the minimum amount required to create a new account (20 XLM as of 13 JAN 2018).

If the transaction is successful, a transaction ID will be displayed in the textbox underneath. You may look up this transaction using a [stellar explorer](https://stellarchain.io/).

Network fees (100 stroops (0.00001 XLM) as of 13 JAN 2018) are deducted from the source account. This is mandated by the network - read more here: https://www.stellar.org/developers/guides/concepts/fees.html

***If you are transferring to an account owned by you, please make sure you know the account secret key! Your XLM will be lost without it***

The "memo" field is used to provide additional information associated with the transaction. This field is also used by some exchanges (eg. Bittrex) in order to identify your account. You may leave this blank if you don't need to use it.

### How do I transfer XLM from an exchange when my account doesn't exist?

As far as I can tell, exchanges create an account for you when you attempt to transfer your XLM to an account that doesn't exist yet. You can generate an address using this tool and use that as a destination at an exchange. That should create the account for you. I have tested this with Bittrex.

## Contributing

### Are you going to keep updating this?

Only if there are major issues or reasonable feature requests. Feel free to make contributions using pull requests.

### I want to add a feature or report a bug.

Feel free to make contributions using a pull request. Create an issue on github to report a bug.

## Miscellaneous

### Why is this so ugly? Why does it violate every principle I learned in UI design class?

This client isn't designed to be pretty, or usable. It's supposed to be *small*. Besides, unstyled `<h2>` and `<button>` elements have a certain quaint charm to them, don't they?

### Why don't you include this FAQ in the client itself?

Because then it wouldn't be minimalist.

### Why not just include a link?

What if I move the FAQ somewhere else? If the client gets translated, do I have to translate this page also? What if someone is running it locally and accidentally clicks the link, thereby revealing their IP address to GitHub? So much to think about...
