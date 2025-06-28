# PumpSwap SDK

A Web3 SDK for integrating with PumpSwap decentralized exchange on Solana.

## Installation

```bash
npm i pump-swap-core-v1
# or
yarn add pump-swap-core-v1
```

## Usage

### Buy Instruction Example

```javascript
const buyTx = new Transaction()
    .add(
        createAssociatedTokenAccountIdempotentInstruction(payer.publicKey, user_base_token_account, payer.publicKey, base_mint),
        createAssociatedTokenAccountIdempotentInstruction(payer.publicKey, user_quote_token_account, payer.publicKey, NATIVE_MINT),
        SystemProgram.transfer({
            fromPubkey: payer.publicKey,
            toPubkey: user_quote_token_account,
            lamports: Number(quote_amt),
        }),
        createSyncNativeInstruction(user_quote_token_account)
    );
    
buyTx.add(
    await pSwap.getBuyInstruction(base_amt, quote_amt, {
        pool,
        baseMint: base_mint,
        quoteMint: NATIVE_MINT,
        baseTokenProgram: TOKEN_PROGRAM_ID,
        quoteTokenProgram: TOKEN_PROGRAM_ID,
        user: payer.publicKey
    })
)
```

## Examples

Check out the example files in the `src/example` directory for more transaction examples and usage patterns.

## Development Status

This SDK is currently being upgraded and improved. Check the latest releases for updates.
