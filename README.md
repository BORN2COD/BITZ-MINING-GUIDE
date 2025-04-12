# BITZ-MINING-GUIDE
$BITZ — First ePOW (Eclipse Proof-of-Work) commodity token anyone can mine with just a CPU or a VPS.

---

## 📌 INTRODUCTION

Bitz is a decentralized commodity token on the Eclipse network. It introduces a new mining model using Eclipse’s infrastructure.

- ✅ Anyone can mine on Eclipse
- ✅ Max supply — 5,000,000
- ✅ Not pre-mined
- ✅ ZERO team or insider allocations
- ✅ Not related to $ES (Grass snapshot already taken)

---

## ⚙️ REQUIREMENTS

Before you begin:

- A VPS or Ubuntu system (20.04+ recommended) or WSL
- Backpack or Eclipse-compatible wallet
- 0.005+ ETH on Eclipse

---

## ⚒️ SETUP ENVIRONMENT

### 1. Update and Install Base Tools
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl nano build-essential -y
```

### 2. Install Screen (for background mining)
```bash
sudo apt install autoconf make gcc libutempter-dev libpam0g-dev libncurses5-dev -y
curl -O https://ftp.gnu.org/gnu/screen/screen-4.9.1.tar.gz
```
```bash
tar -xzf screen-4.9.1.tar.gz
cd screen-4.9.1
./configure
make
sudo make install
```
**Verify installation:**
```bash
screen --version
```

### 3. Install Rust
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
**When prompted, press 1 to proceed.**
```bash
source $HOME/.cargo/env
```

### 4. Install Solana CLI
```bash
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
```bash
source $HOME/.bashrc
```
**Check version:**
```bash
solana --version
```
> If Solana isn’t found, reboot the system:
```bash
reboot
```

---

## 🔗 CONFIGURE RPC FOR ECLIPSE
Connect to the Eclipse Mainnet:
```bash
solana config set --url https://mainnetbeta-rpc.eclipse.xyz/
```

---

## 🔐 WALLET SETUP

### 1. Generate New Solana Keypair
```bash
solana-keygen new
```
**Save your passphrase safely.**

### 2. Export Private Key for Backpack
```bash
cat ~/.config/solana/id.json
```
**Copy the key (list of numbers) and import it into the Backpack Wallet under "Private Key".**

### 3. Fund Wallet
Transfer at least 0.005 ETH to your Eclipse wallet address.

---

## 🧰 INSTALL BITZ CLI
Compile and install the miner:
```bash
cargo install bitz
```

---

## 🏗️ START MINING

### 1. Launch Miner in Screen
```bash
screen -S bitzminer
```

### 2. Start Mining
```bash
bitz collect
```
**To use multiple cores:**
```bash
bitz collect --cores 4
```

### 3. Run in Background
- Detach screen: `Ctrl + A + D`
- Reattach: `screen -r bitzminer`
- List sessions: `screen -ls`
- Stop miner: `Ctrl + C`
- Kill screen: `screen -XS bitzminer quit`

---

## 💰 CLAIM REWARDS
```bash
bitz claim
```

## 📈 CHECK WALLET STATUS
```bash
bitz account
```

---

## 🔒 FINAL NOTES
- Always backup your `id.json` and mnemonic
- Fund your wallet before mining begins
- Can run on 1vCPU + 1GB RAM VPS

---

Stay updated at [Maverick 🦅](https://x.com/PhaResearcher)

You're ready to mine $BITZ! ⚡
