# 🎮 ELO Flow - Decentralized Poker on Flow Blockchain

A fully decentralized poker game built on the Flow blockchain, using verifiable random shuffling for each game, gasless transactions, and cross-chain data availability using Avail DA.

By posting game data onto Avail DA, players can access the game data on any compatible chain and enjoy skill-based matchmaking for any poker variant.

## 🌟 Features

- **Decentralized Gameplay**: Fully on-chain poker logic implemented in Cadence
- **Verifiable Random Shuffling**: Utilizing Flow VRF for provably fair card generation/distribution
- **Gasless Transactions**: Players can enjoy the game without worrying about gas fees
- **Multi-Platform Access**: Play through Web UI or Telegram Bot ([@elo_flow_bot](https://t.me/elo_flow_bot))

## 🏗 Architecture

### Smart Contracts (Cadence)
- Deck management and shuffling
- Game state management
- Player actions and betting logic
- Pot distribution and winning hand calculation

### Backend (SST + Hono + AWS Lambda)
- Gasless transaction processing (blind signing)
- Using [fcl-kms-authorizer](https://github.com/doublejumptokyo/fcl-kms-authorizer) to sign the transaction on AWS Lambda

### Frontend
- Vite + React + Typescript
- Telegram bot ([@elo_flow_bot](https://t.me/elo_flow_bot)) for mobile access
- Real-time game updates
- Wallet using [Flow-FCL](https://github.com/onflow/fcl-js)

## 🚀 Getting Started

### Prerequisites
- Flow CLI
- Node.js (v20+)
- Flow wallet

### Installation

1. Clone the repository

```bash
git clone https://github.com/marcuspang/eloflow
cd eloflow
```

2. Install dependencies

```bash
cd frontend
pnpm install
```

3. Configure environment variables

```bash
cp .env.example .env
```

4. Deploy smart contracts

```bash
flow project deploy
```

5. Start the backend

```bash
pnpm run dev
```

## 🎮 Playing the Game

### Web Interface
1. Visit [https://flowelo.vercel.app/](https://flowelo.vercel.app/)
2. Connect your Flow wallet
3. Join or create a game
4. Start playing!

### Telegram Bot
1. Search for [@elo_flow_bot](https://t.me/elo_flow_bot) on Telegram
2. Start a conversation with the bot
3. Follow the bot's instructions to connect your wallet and start playing

## 🔧 Technical Details

### Verifiable Random Function (VRF)
- VRF is used to generate the random seed for the card generation
- Then, the seed is used to generate card1 for the player, card2 is generated by dividing by 52
- For each subsequent player, the seed is divided by their position, i.e. seed / 4 if they are the 4th player

### Gasless Transactions
- By using a custom authorization function for the payer, we can generate a signed envelope for the transaction
- The signed envelope is returned to the client, and the user can simply proceed with the transaction as normal

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Flow blockchain team
- SST framework
- Hono framework
- Avail DA

## 📞 Contact

For questions and support, please:
- Open an issue
- Contact me via email

---
Built with ❤️ for the Flow ecosystem