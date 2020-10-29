# Polkadotting

Playing around with [Substrate](https://substrate.io) and [Polkadot](https://polkadot.network) while following their [tutorials](https://substrate.dev/en/tutorials).

## Useful commands

```sh
# Start a Nix shell
nix-shell

# Compile Rust code
cargo build --release

# Start a Substrate node in development mode
./target/release/node-template --dev --tmp

# Purge old chain data
./target/release/node-template purge-chain --base-path /tmp/<directory> --chain local

# Start Alice's and Bob's nodes
./target/release/node-template \
  --base-path /tmp/alice \
  --chain local \
  --alice \
  --port 30333 \
  --ws-port 9945 \
  --rpc-port 9933 \
  --node-key 0000000000000000000000000000000000000000000000000000000000000001 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator

./target/release/node-template \
  --base-path /tmp/bob \
  --chain local \
  --bob \
  --port 30334 \
  --ws-port 9946 \
  --rpc-port 9934 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWEyoppNCUx8Yx66oV9fJnriXwCcXwDDUA2kj6vnc6iDEp

# Export chain spec
./target/release/node-template build-spec --disable-default-bootnode --chain local > customSpec.json

# Convert chain spec to raw chain spec
./target/release/node-template build-spec --chain=customSpec.json --raw --disable-default-bootnode > customSpecRaw.json

# Key generation via Substrate
~/.cargo/bin/subkey generate --scheme sr25519
~/.cargo/bin/subkey inspect --scheme ed25519 <mnemonic>

# Check dependency resolution
cargo check -p node-template-runtime

# Build for production release
cargo build --release -p node-template-runtime

# Build and run
cargo run -- --dev --tmp

# Install node dependencies
yarn install

# Start the frontend
yarn start
```
