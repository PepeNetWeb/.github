# PepeNet - The Decentralized Web, powered by Pepecoin (Scrypt POW)

PepeNet is internet infrastructure for creating .pepe domain names and securing them with HTTPS.

## The Namespace

The namespace-protocol repo defines the on-chain namespace which allows users to register/release names, pay their leases, and sell/trade their names.

Users can lease names using a P2PKH or P2SH (limited to standard n-of-m templates) wallet by issuing namespace opcodes via OP_RETURN.

There are 12 opcodes:

- COMMIT & CLAIM (Front-run proof name registration)
- RELEASE (Give up ownership of a name)
- RENEW (Pay rent on their name's lease)
- TRANSFER (Move a name to a different wallet address)
- SELL/RESERVE/SETTLE (Open market selling/purchasing of names)
- SELL_TO/PAY (Direct sell offers to address)
- AS (Change acting vin identity, for custodial multi-op_return operations)
- TRADE (Co-signed name swaps)

Names are leased for up to 1 year and renewed at any time (max 1 year). Leasing cost is tied to network fees using a coinbase fee oracle (coinbase value - 10,000 = network fees collected that block). A 1-Year lease is calculated as the approximate network costs of performing 13 transactions/year. All coin paid to leases is burned in provably unspendable OP_RETURN (not paid to anyone, returned to the commons as deflation). 

No UTXO set or block history pre-activation is necessary to index the namespace, which makes indexers very light.

