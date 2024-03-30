# Motoko-React Crypto Token

Welcome to the Motoko-React Crypto Token project! This repository contains the code for creating a cryptocurrency token using Motoko for the backend (smart contract) and React for the frontend user interface. This project aims to provide a simple example of how to create a decentralized application (dApp) for managing and interacting with a custom cryptocurrency token.

## Features

- **Smart Contract**: Utilizes Motoko to define the behavior and functionality of the cryptocurrency token.
- **Frontend Interface**: Developed with React to provide users with an intuitive interface for interacting with the token.
- **Tokenomics**: Define the specifications of the token, including its name, symbol, total supply, and additional features such as token burning or minting capabilities.
- **Blockchain Interaction**: Connects with the Internet Computer blockchain to deploy the smart contract and interact with it from the frontend.

## Getting Started

To get started with the project, follow these steps:

1. Clone this repository to your local machine.
2. Navigate to the project directory.
3. Install dependencies for both the backend and frontend:
   ```
   cd backend
   npm install
   cd ../frontend
   npm install
   ```
4. Deploy the smart contract to the Internet Computer blockchain using the provided scripts and configuration.
5. Start the frontend development server:
   ```
   cd ../frontend
   npm start
   ```

## Contributing

Contributions to this project are welcome! If you have any ideas for improvements or new features, feel free to open an issue or submit a pull request. Please ensure that your contributions adhere to the project's coding conventions and standards.


## Acknowledgements

- This project was inspired by the growing interest in blockchain technology and decentralized finance (DeFi).
- Special thanks to the DFINITY Foundation for developing the Internet Computer blockchain and providing resources for developers.

## Contact

If you have any questions or suggestions regarding this project, please feel free to contact the project maintainer(s):

- [Vaibhav](vaibhav1492.be21@chitkara.edu.in)






















# Check your Balance

1. Find out your principal id:

```
dfx identity get-principal
```

2. Save it somewhere.

e.g. My principal id is: 45fl2-dpjc3-wb2ye-nqzny-sxzur-4xcgs-v7krn-dju4r-x5lbl-4myb6-lae

3. Format and store it in a command line variable:

```
OWNER_PUBLIC_KEY="principal \"$( \dfx identity get-principal )\""
```

4. Check that step 3 worked by printing it out:

```
echo $OWNER_PUBLIC_KEY
```

5. Check the owner's balance:

```
dfx canister call token balanceOf "( $OWNER_PUBLIC_KEY )"
```

# Charge the Canister

1. Check canister ID:

```
dfx canister id token
```

2. Save canister ID into a command line variable:

```
CANISTER_PUBLIC_KEY="principal \"$( \dfx canister id token )\""
```

3. Check canister ID has been successfully saved:

```
echo $CANISTER_PUBLIC_KEY
```

4. Transfer half a billion tokens to the canister Principal ID:

```
dfx canister call token transfer "($CANISTER_PUBLIC_KEY, 500_000_000)"
```

# Deploy the Project to the Live IC Network

1. Create and deploy canisters:

```
dfx deploy --network ic
```

2. Check the live canister ID:

```
dfx canister --network ic id token
```

3. Save the live canister ID to a command line variable:

```
LIVE_CANISTER_KEY="principal \"$( \dfx canister --network ic id token )\""
```

4. Check that it worked:

```
echo $LIVE_CANISTER_KEY
```

5. Transfer some tokens to the live canister:

```
dfx canister --network ic call token transfer "($LIVE_CANISTER_KEY, 50_000_000)"
```

6. Get live canister front-end id:

```
dfx canister --network ic id token_assets
```

7. Copy the id from step 6 and add .raw.ic0.app to the end to form a URL.
   e.g. blah-blah-blah.raw.ic0.app
