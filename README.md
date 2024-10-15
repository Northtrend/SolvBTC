# Interact with SolvBTC

## 1. Getting Reserve Status

To retrieve the SolvBTC reserve status, you can interact with the smart contract and check the balance of Bitcoin-backed reserves.

Solidity Example:

```
function getReserveBalance(address solvBTC) public view returns (uint256) {
    return solvBTC.balance;
}
```
JavaScript Example (Web3.js):

```
const reserveBalance = await web3.eth.getBalance(solvBTCAddress);
console.log(`SolvBTC Reserve: ${reserveBalance}`);
```
## 2. Minting Vouchers

Minting vouchers requires interaction with the SolvBTC contract, passing the amount of BTC you want to mint.

Solidity Example:

```
function mintVoucher(address solvBTC, uint256 amount) public {
    solvBTC.mint(msg.sender, amount);
}
```
JavaScript Example (Ethers.js):

```
const solvBTCContract = new ethers.Contract(solvBTCAddress, abi, provider);
await solvBTCContract.mint(signer.address, amount);
```
## 3. Redeeming Vouchers

Users can redeem vouchers back into BTC by calling the redeem function.

Solidity Example:

```
function redeemVoucher(address solvBTC, uint256 amount) public {
    solvBTC.redeem(msg.sender, amount);
}
```
JavaScript Example (Web3.js):

```
await solvBTCContract.methods.redeem(amount).send({ from: userAddress });
```
## 4. Getting Voucher Info

Retrieve details of the voucher, such as balance or expiration.

Solidity Example:

```
function getVoucherInfo(address voucher) public view returns (uint256, uint256) {
    return (voucher.balance, voucher.expiration);
}
```
JavaScript Example (Ethers.js):

```
const voucherInfo = await solvBTCContract.voucherInfo(voucherId);
console.log(`Voucher Balance: ${voucherInfo[0]}, Expiration: ${voucherInfo[1]}`);
```
5. Transferring Vouchers

Users can transfer their vouchers to other users.

Solidity Example:

```
function transferVoucher(address to, uint256 amount) public {
    solvBTC.transfer(to, amount);
}
```
JavaScript Example (Web3.js):

```
await solvBTCContract.methods.transfer(toAddress, amount).send({ from: userAddress });
```
This guide covers basic interactions with SolvBTC: checking reserves, minting, redeeming, and transferring vouchers. Adjust the contract ABI and addresses to your environment.
