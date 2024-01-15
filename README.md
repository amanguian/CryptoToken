# Check your Balance

principal id:
dfx identity get-principal


Format and store it in a command line variable:
OWNER_PUBLIC_KEY="principal \"$( \dfx identity get-principal )\""

Check that step 3 worked by printing it out:
echo $OWNER_PUBLIC_KEY

Check the owner's balance:
dfx canister call token balanceOf "( $OWNER_PUBLIC_KEY )"


Check canister ID:
dfx canister id token


Save canister ID into a command line variable:
CANISTER_PUBLIC_KEY="principal \"$( \dfx canister id token )\""

Transfer half a billion tokens to the canister Principal ID:
dfx canister call token transfer "($CANISTER_PUBLIC_KEY, 500_000_000)"

# Deploy the Project to the Live IC Network
Create and deploy canisters:
dfx deploy --network ic

Check  live canister ID:
dfx canister --network ic id token

Save the live canister ID to a command line variable:
LIVE_CANISTER_KEY="principal \"$( \dfx canister --network ic id token )\""


Transfer  tokens to the live canister:
dfx canister --network ic call token transfer "($LIVE_CANISTER_KEY, 50_000_000)"


Get live canister front-end id:
dfx canister --network ic id token_assets


