# DocumentOnChain

DocumentOnChain is a blockchain-backed document verification app built around Polygon, Web3.js, MetaMask, and IPFS. It allows authorized issuers to upload document fingerprints, verify whether a document exists on-chain, and remove hashes when needed.

## What It Does

- Connects a MetaMask wallet to the application
- Uploads document files and stores their IPFS CID
- Writes document hashes to a Solidity smart contract on Polygon
- Verifies whether a document has been registered on-chain
- Lets the contract owner manage authorized exporters
- Supports document deletion for authorized issuers

## Stack

- Solidity smart contract
- Web3.js
- MetaMask wallet integration
- Polygon network
- IPFS via Pinata
- HTML, CSS, Bootstrap, and vanilla JavaScript

## Repository Structure

- `Contract/Verfication.sol`: smart contract for document and exporter management
- `js/App.js`: wallet, contract, upload, verification, and admin logic
- `upload.html`: document upload flow
- `verify.html`: document verification flow
- `delete.html`: document deletion flow
- `index.html`: admin/exporter management dashboard

## Local Setup

1. Install dependencies:

```bash
npm install
```

2. Configure IPFS upload credentials in `js/config.js`.

3. Serve the project from the repository root with a local static server. Example:

```bash
npx serve .
```

4. Open one of the entry pages in your browser:

- `upload.html`
- `verify.html`
- `delete.html`
- `index.html`

5. Connect MetaMask and switch to the network expected by the contract configuration.

## Configuration

The project reads upload credentials from `js/config.js`.

```js
window.APP_CONFIG = {
  pinataApiKey: "YOUR_PINATA_API_KEY",
  pinataSecretApiKey: "YOUR_PINATA_SECRET_API_KEY",
};
```

## Notes

- This repository is prepared as a portfolio project, so live API secrets are not committed.
- The current frontend uploads directly from the browser to Pinata. For a production deployment, that should move behind a backend or signed upload flow rather than exposing write credentials client-side.
- The contract source is included for review, but deployment and ownership assumptions depend on the configured on-chain address inside `js/App.js`.
