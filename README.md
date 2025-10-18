
# 🔒 Confidential Auction with Arcium Integration

A privacy-preserving auction platform for Solana built with **Anchor** and **Arcium**. This project demonstrates a confidential bidding process with encrypted data and secure winner selection using the Arcium network. Developed as a submission for the **Cypherpunk Hackathon**.

## 💡 Overview

This project solves the fundamental problem of **front-running** and **bid manipulation** in on-chain auctions. Instead of submitting transparent bids visible to everyone:

1.  **Bids are Encrypted:** Users submit bids as opaque `EncryptedData` accounts via the Arcium SDK.
2.  **Privacy is Maintained:** The Solana program stores these encrypted bytes, ensuring all bids remain confidential.
3.  **Secure Finalization:** An off-chain **Arcium Relayer** collects the encrypted data, performs the **secure comparison calculation** (finding the maximum bid) within the confidential Arcium environment, and posts the final, verifiable result back to the smart contract.

---

## ✨ Features

* **Confidential Bid Submission:** Bids are stored on-chain in an encrypted state (`Vec<u8>`).
* **Trusted Relayer Model:** Auction initialization requires a designated `arcium_relayer` key for secure result posting.
* **Result Verification:** Final winner and winning bid are posted securely, authenticated by the Relayer's signature.
* **Memory Management:** Includes instruction for closing `EncryptedData` accounts to refund rent to users.
* **MVP-Ready:** Provides a functional smart contract structure ready for client-side integration.

---

## 🛠️ Getting Started

Follow these steps to set up and run the project locally on a Solana development environment (Devnet/Localnet).

### Prerequisites

You must have the following tools installed:

* **Rust** and **Cargo**
* **Solana CLI** (configured to Devnet or Localnet)
* **Anchor CLI**
* **Node.js** (v18+) and **Yarn** or **npm** (for client-side application)

### Installation and Setup

1.  **Clone the repository:**

    ```bash
    git clone [https://github.com/YourAccount/Solana-arcium-auction.git](https://github.com/YourAccount/Solana-arcium-auction.git)
    cd Solana-arcium-auction
    ```

2.  **Build the Anchor Program:**

    Compile the smart contract to generate the necessary target files.

    ```bash
    anchor build
    ```

3.  **Deploy to Local Validator (Recommended for testing):**

    Start a local validator and deploy the program.

    ```bash
    solana-test-validator & 
    anchor deploy
    ```

4.  **Integration Note:**

    For a full demonstration, you will need to implement the **client-side logic** using the Arcium SDK to encrypt the bids before sending the `submit_encrypted_data` transaction.

---

## 📄 Project Structure

| Path | Description |
| :--- | :--- |
| `programs/mvp_auction/src/lib.rs` | The core Solana smart contract (Anchor program). |
| `tests/` | Placeholder for JavaScript/TypeScript unit tests. |
| `Anchor.toml` | Anchor configuration file. |
| `Cargo.toml` | Rust dependencies for the program. |
| `client_app/` | *(Suggestion: Place your JS/TS client code here)* |

---

## Authors

Smart contract developer  
[gb12345690](https://github.com/gb12345690)


---

## ⚖️ License

This project is licensed under the **[Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0))**.
