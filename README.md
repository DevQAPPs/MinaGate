# MinaGate
Application for token gating and content access utilizing the privacy and lightweight aspects of the Mina Protocol.
---

MinaGate is a pioneering content access platform that leverages the Mina Protocol to offer privacy-centric token gating features, utilizing `o1js` for creating zero-knowledge proofs (zkProofs) to offer privacy-focused token gating solutions. With MinaGate, content creators can restrict access to their content securely and privately, ensuring only verified token holders can gain access.

## Features

- **Token Gating**: Restrict access to content based on NFT or specific token ownership using zkProofs.
- **Privacy-Preserving**: Utilize zero-knowledge proofs to verify token ownership without compromising user privacy.
- **Lightweight Integration**: Thanks to Mina Protocol's succinct blockchain, integration is lightweight without the need for heavy blockchain data handling.
- **Flexible Content Delivery**: Serve content from your preferred backend or decentralized storage without storing it on the blockchain.
- **User-Friendly Interface**: Simple and intuitive web interface for users to access gated content.
- **Creator Dashboard**: Content creators can manage their gated content and monitor access.

## How It Works

### For Content Creators

1. **Deploy zkApp**: Creators deploy a zkApp to the Mina Protocol, defining the token requirements for gating their content.
2. **Upload Content**: Content is uploaded to a preferred storage solution with a unique identifier linked in the zkApp.
3. **Set Access Rules**: Define which tokens or NFTs are required to access the content within the zkApp logic.

### For Users

1. **Access Request**: Users request access to the content through the MinaGate interface.
2. **zkProof Generation**: The user's wallet generates a zero-knowledge proof that they own the required token, without revealing any other information.
3. **Verification**: MinaGate verifies the proof using the zkApp smart contract.
4. **Content Unlocking**: Once verified, the user is granted access to the content.

## Getting Started

### Prerequisites

- Install [Node.js](https://nodejs.org/) (version 12.x or higher).
- Access to a Mina Protocol node or [datahub](https://mina.datahub.figment.io/) for blockchain interactions.
- A code editor like [VS Code](https://code.visualstudio.com/) for development.
- o1js installed globally or in your project


### Installation

1. **Clone the repository**

   ```sh
   git clone https://github.com/yourusername/minagate.git
   ```

2. **Install dependencies**

   Navigate to the cloned directory and install the required dependencies:

   ```sh
   cd minagate
   npm install
   npm install @o1labs/snarkyjs
   ```

3. **Environment Setup**

   Create a `.env` file in the root directory and fill in the necessary environment variables:

   ```
   MINA_NODE_ENDPOINT=https://yourminaendpoint.com
   PRIVATE_KEY=yourprivatekey
   PUBLIC_KEY=yourpublickey
   ```
   
4. **Write Your zkApp**

   Use `o1js` to create a zkApp for token gating:

   ```typescript
   // src/zkApp.ts
   import { SmartContract, method, Field, PublicKey } from '@o1labs/snarkyjs';

   class TokenGatingZkApp extends SmartContract {
     @method
     async checkTokenOwnership(proof: Field, ownerPublicKey: PublicKey) {
       // Logic to verify zero-knowledge proof for token ownership
     }
   }

   export default TokenGatingZkApp;
   ```

5. **Interact with zkApp**

   Create scripts or a web interface to interact with the zkApp using `o1js`:

   ```typescript
   // src/interact.ts
   import { Mina, Account, PrivateKey } from '@o1labs/snarkyjs';

   async function accessContent(userPrivateKey: PrivateKey) {
     const user = new Account(userPrivateKey);
     // Interact with zkApp to generate and verify proof
   }
   ```
6. **Run the Application**

   Start the development server:

   ```sh
   npm start
   ```

   This will launch the MinaGate interface at `http://localhost:3000`.

## Contribution

We welcome contributions from the community. If you wish to contribute to the codebase or documentation, please submit a pull request or open an issue to discuss your ideas.

## License

MinaGate is released under the [MIT License](LICENSE).

---
