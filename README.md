
# ZK SNARK Designer

This project implements a logical gate using the Circom programming language. The goal is to prove knowledge of inputs A (0) and B (1) that yield a 0 output. We achieve this by creating a circuit, compiling it, generating a proof, deploying a Solidity verifier contract to Sepolia, and verifying the proof.

## Description

The project focuses on demonstrating the capability of zero-knowledge proofs (ZKPs) in validating specific inputs without revealing them. Using Circom, we create a logical circuit, compile it, and generate a proof. The proof is then verified using a Solidity contract deployed on the Sepolia test network.

## Getting Started

### Installing

* Clone the repository from GitHub
* Navigate to the project directory

```sh
git clone https://github.com/yourusername/ZK-SNARK-Designer.git
cd ZK-SNARK-Designer
```

* Install the necessary dependencies

```sh
npm install
```

### Executing program

* Compile the Circom logic gate circuit

```sh
npx hardhat circom
```

* Deploy the verifier contract and generate the proof on the Sepolia test network

```sh
npx hardhat run scripts/deploy.ts --network sepolia
```

This script does the following:
1. Deploys the `LogicCircuitVerifier.sol` contract
2. Generates a proof from circuit intermediaries with `generateProof()`
3. Generates calldata with `generateCallData()`
4. Calls `verifyProof()` on the verifier contract with calldata

With these commands, you can compile a ZKP, generate a proof, deploy a verifier, and verify the proof 🎉

## Help

If you encounter any issues, you can run the following command to get help:

```sh
npx hardhat help
```

## Authors

Dominique Pizzie  
[@DomPizzie](https://twitter.com/dompizzie)

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.

## Circom Logic Gate Code

```text
circuits
└── LogicCircuit
    └── circuit.circom
```

## Hardhat Configuration

```ts
circom: {
  // (optional) Base path for input files, defaults to `./circuits/`
  inputBasePath: "./circuits",
  // (required) The final ptau file, relative to inputBasePath, from a Phase 1 ceremony
  ptau: "powersOfTau28_hez_final_12.ptau",
  // (required) Each object in this array refers to a separate circuit
  circuits: JSON.parse(JSON.stringify(circuits))
}
```

## Verify Proof

Call the `verifyProof()` method on the verifier contract and assert the output is true.
