# Repository: wallet-balance-checker
# Description: A simple Web3 Ethereum wallet balance checker

# Install:
npm init -y
npm install ethers

# index.js
const { ethers } = require("ethers");

 provider = new ethers.JsonRpcProvider("https://cloudflare-eth.com");

async function checkBalance(wallet) {
  try {
    const balance = await provider.getBalance(wallet);
    console.log(`Wallet: ${wallet}`);
    console.log(`Balance: ${ethers.formatEther(balance)} ETH`);
  } catch {
    console.log("Invalid wallet address");
  }
}

const wallet = process.argv[2];

if (!wallet) {
  console.log("Usage: node index.js <wallet_address>");
  process.exit(1);
}

checkBalance(wallet);
