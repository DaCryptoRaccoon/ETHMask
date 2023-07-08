# ETHMask An Ethereum Transaction Mixing Tool

    :::::::::: ::::::::::: :::    ::: ::::    ::::      :::      ::::::::  :::    ::: 
    :+:            :+:     :+:    :+: +:+:+: :+:+:+   :+: :+:   :+:    :+: :+:   :+:  
    +:+            +:+     +:+    +:+ +:+ +:+:+ +:+  +:+   +:+  +:+        +:+  +:+   
    +#++:++#       +#+     +#++:++#++ +#+  +:+  +#+ +#++:++#++: +#++:++#++ +#++:++    
    +#+            +#+     +#+    +#+ +#+       +#+ +#+     +#+        +#+ +#+  +#+   
    #+#            #+#     #+#    #+# #+#       #+# #+#     #+# #+#    #+# #+#   #+#  
    ##########     ###     ###    ### ###       ### ###     ###  ########  ###    ### CLI v1.0
    -------------------------------------------------------------------------------------------------------------------
    Donations ETH: 0xE2f739D09e372a627c563C642321e51b9E64BcB3
    Donations BTC: 19Qz2mid5CsGQ49Zztrt8k2NhGGUMT1S8L
    Donations LTC: LTGNf2ANWQGZCXmu5NPACUhtCgNHHWCZVs
    -------------------------------------------------------------------------------------------------------------------

    Welcome to ETHMask!

    This command line interface enhances privacy by distributing funds through a chain of Ethereum addresses.

    Here's a quick guide on how to use it:

    Enter your wallet public key, private key, Etherscan API key and Infura API key into the .env file. All are required for the scripts to work correctly.

    The wallet public and private keys are used to send the funds to the new addresses generated by ETHMask.

    The default RPC endpoint is Infura, but it can be overridden by a custom RPC endpoint. There is also an optional proxy setting.

    
    MAIN COMMANDS:

    automated_mode <number_of_addresses>
                                An automated way to run the new_accounts and send_transactions commands, followed by the sweep script.
                                Run the automated mode for generating addresses, sending transactions, and running the consolidation script
                                The automated mode sets a random amount to send to each address at a random time delay between transactions.
                                It also checks on-chain for confirmation before sending the next transaction [TXID <Address> | Confirmed ✔].
                                After the automated mode is over, user will be asked if they want to run the consolidation script 
                                to send all funds to the Master address.
                                WARNING:
                                    Always double check that the master address is correct, as all funds will be sent there.
                                    Make certain that you know its private key.
                                    DO NOT MAKE A MISTAKE, OR YOU WILL LOSE ALL THE FUNDS!

    new_accounts <number>       Generates the specified number of new Ethereum accounts
                                For example, 'new_accounts 100' will create 100 new accounts.

    send_transactions           Prompts for a CSV file of accounts (generated by new_accounts) and sends transactions to those accounts

    
    OTHER COMMANDS:
    
    add_address_label <address> <label>     Assign a label to an Ethereum address in the address book
                                            The address book is a collection of addresses and their associated labels. 

    address_balance <address>   Display the balance in ether of a specific Ethereum address using the Etherscan API

    address_book                Display the list of addresses and their labels in the address book

    address_history <address>   View the transaction history of a specific Ethereum address using the Etherscan API
                                Details include transaction hash, sender, receiver and value.

    decrypt_private_key         Decrypt the encrypted private key using the passphrase
                                User will be prompted for the path to the encrypted private key JSON file, and the passphrase.
                                Encryption is handled by the w3.eth.account decrypt function.

    encrypt_private_key         Encrypt the private key using a passphrase, and save to a JSON file
                                User will be prompted for the private key.
                                Encryption is handled by the w3.eth.account.encrypt function.

    estimate_fee                Estimate the transaction fee based on the current gas price
                                This is done by retrieving the current gas price from the network and converting it to ether.

    exit                        Exit the shell

    generate_encrypted_key      Generate an encrypted private key with a passphrase and save to a JSON file
                                User will be prompted for a passphrase. Encryption is handled by the w3.eth.account.encrypt function.

    help <command>              Display help for the specified command                        
                                
    proxy <Proxy_URL>           Set the Proxy URL (optional)
                                For example, 'proxy http://127.0.0.1:9050' will set the Proxy URL to a local Tor proxy.

    remove_address_label <address>          Remove the label associated with the specified Ethereum address from the address book

    rpc <RPC_endpoint>          Set the RPC endpoint (optional)
                                For example, 'rpc https://mainnet.infura.io/v3/YOUR-PROJECT-ID' will set the RPC endpoint to the provided Infura address.

    switch_network              Switch to a different Ethereum network by configuring the RPC endpoint
                                User will be prompted for the new RPC endpoint.
                                The infura_endpoint attribute of the EthMixerCmd class will be updated.

ETHMask is a command-line interface (CLI) tool for mixing Ethereum transactions.

## Overview

ETHMask provides a simple and secure way to mix Ethereum transactions, allowing users to enhance their transaction privacy. It generates new Ethereum accounts and sends transactions to those accounts, making it difficult to trace the original sender.

However, it's important to note that ETHMask is not classified as a traditional mixer because it does not mix funds with any other user. Instead, it focuses on creating a chain of transactions within the user's control, making it harder to trace the source of funds. By sending transactions from the user's wallet address to newly generated addresses, ETHMask aims to increase privacy by obscuring the transaction history.

Here are some advantages and benefits of using ETHMask:

Enhanced Privacy: By using ETHMask, users can improve the privacy of their Ethereum transactions. The chain of transactions created by ETHMask makes it challenging to link the original sender to the final recipient, thus increasing privacy.

Obfuscation of Transaction History: ETHMask generates new Ethereum accounts for each transaction, making it difficult to trace the flow of funds. This can help prevent others from identifying the source of funds and associating it with specific addresses.

User Control: Unlike traditional mixers that rely on pooling funds with other users, ETHMask allows users to maintain full control over their funds. Users generate their own new accounts and control the transaction flow, eliminating the need to trust third parties with their funds.

Simplicity and Ease of Use: ETHMask provides a user-friendly command-line interface (CLI) that simplifies the process of generating new accounts and sending transactions. Users can easily interact with the script and initiate transactions without extensive technical knowledge.

Flexibility: ETHMask offers flexibility in terms of customizing transaction amounts and gas prices. Users can choose the percentage of the balance to be sent or specify a custom value, providing control over the transaction details.

It's important to note that while ETHMask can enhance privacy, it cannot provide complete anonymity. Transaction details, including addresses and amounts, are still recorded on the Ethereum blockchain. Additionally, users should be mindful of applicable legal and regulatory requirements when using ETHMask or engaging in cryptocurrency-related activities.

## Features

- Create new Ethereum accounts securely
- Send transactions to the generated accounts
- Customizable transaction amount based on percentage or custom value
- Integration with Infura for RPC endpoint
- Support for proxy configuration
- Consolidation script to further enhance privacy
- Automated mode
- Encrypt / Decrypt wallets

## Prerequisites

Before using ETHMask, make sure you have the following:

- Python 3.7 or higher installed
- Ethereum wallet addresses and their corresponding private keys stored in a CSV file
- Infura API key (sign up at [https://infura.io/](https://infura.io/))
- Etherscan API key (sign up at [https://etherscan.io/](https://etherscan.io/))
- Video Demo [ https://vimeo.com/manage/videos/842683100 ]

## Installation

1. Clone the ETHMask repository:

git clone https://github.com/your-username/ETHMask.git

Change into the project directory:

cd ETHMask

Install the required Python packages:

pip install -r requirements.txt

Create a .env file and add the following variables:

PRIVATE_KEY=<your-private-key>
WALLET_ADDRESS=<your-wallet-address>
INFURA_API_KEY=<your-infura-api-key>
ETHERSCAN_API_KEY=<your-etherscan-api-key>

Run ETHMask:

python ETHMask.py

Follow the prompts to execute the desired commands:
rpc <RPC_endpoint>: Set the RPC endpoint for Ethereum network connection.
proxy <Proxy_URL>: Set the Proxy URL for network connection (optional).
new_accounts <number>: Generate a specified number of new Ethereum accounts.
send_transactions: Send transactions to the generated accounts.

Examples

Generate 100 new Ethereum accounts:
new_accounts 100

Send transactions to the accounts:
send_transactions

Once you have created the accounts and sent the transactions it will as if you wish to run the sweep tool (yes/no)

If you select no you can run it when you are ready by executing the python script ETHSweeper.py at a later date.

# ETHSweeper After Stage 1

ETHSweeper is a script that automates the process of sweeping small amounts of Ethereum.
(ETH) from multiple addresses into a single "master" address.

## Overview

ETHSweeper reads from a CSV file containing Ethereum addresses and their private keys. It checks the balance of each address and, if the balance is sufficient to cover the gas fee for a transaction, it sends the balance (minus the gas fee) to the master address specified by the user.

The gas price is fetched from the Ethereum network at the time of each transaction, ensuring that the script always uses the current gas price.

## Features

- Sweep ETH from multiple addresses to a master address
- Dynamic gas price retrieval
- Support for multiple CSV files
- Calculation of ETH to USD conversion rate

How to Use:

The ETH Sweeper requires the same env file as ETHMixer.

Start the Ethereum Sweeper by running the script with a Python interpreter. The CLI will provide you with the following commands:

sweep: Sweeps all the Ethereum from addresses listed in a selected CSV file into a single "master" address.

exit: Exits the program.

## How It Works:
The sweep command prompts you for the master address, lists all CSV files in the ./Accounts directory, and asks you to select one. For each address, the command checks the balance. If it is sufficient to cover the gas fee, the command sends the balance (minus the gas fee) to the master address.

## Additional Information:
The Ethereum Sweeper is designed to run on Ethereum's Sepolia Testnet. Change the HTTP Provider URL in the Web3.HTTPProvider function if you want to use it on the Ethereum Mainnet or a different testnet.

Be cautious when entering the "master" Ethereum address as all the ETH from the other addresses will be transferred to it. Always double-check addresses before transferring funds and ensure that you never share your private keys.

## Help Me Fund More Projects

help me fund more cool projects like this for other chains like Bitcoin and Litecoin donations can be sent to the addresses below.
Thank you for the support 

    Donations ETH: 0xE2f739D09e372a627c563C642321e51b9E64BcB3
    Donations BTC: 19Qz2mid5CsGQ49Zztrt8k2NhGGUMT1S8L
    Donations LTC: LTGNf2ANWQGZCXmu5NPACUhtCgNHHWCZVs

## License
This project is licensed under the MIT License.

## Disclaimer

**ETHMask is experimental software, provided as-is and without any warranty. Use it at your own risk.**

ETHMask is an experimental script developed for educational and informational purposes only. It is not intended for use in production environments, and its use in real-world scenarios may carry inherent risks.

By using ETHMask, you acknowledge and accept all risks associated with its use. This includes, but is not limited to, the potential loss of funds, incorrect transactions, and security vulnerabilities.

The developers and contributors of ETHSweeper cannot be held responsible for any damages, losses, or liabilities incurred while using this software. It is your responsibility to thoroughly understand the script's functionality, review and validate the code, and take appropriate precautions to ensure the security of your private keys and funds.

Always exercise caution and use common sense when dealing with cryptocurrencies. Before using ETHMask, we recommend consulting with a qualified professional or conducting thorough research to understand the potential risks involved.

Please note that using this software may be subject to legal and regulatory restrictions in your jurisdiction. It is your responsibility to comply with applicable laws and regulations.
