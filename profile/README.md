# PepeNet - The Decentralized Web, powered by Pepecoin 

PepeNet is internet infrastructure for creating ```.pepe``` domain names and securing them with HTTPS.


## PepeNet Desktop

The desktop app bundles the whole stack. It includes a p2p P2PKH wallet for interacting with the namespace/market, the DNS module for publishing DNS records, and TLS for securily visiting .pepe websites.

<img width="768" height="948" alt="image" src="https://github.com/user-attachments/assets/49bb097f-5f17-4f8e-936b-8fa5d3c3d35f" />



## The Namespace

The [namespace-protocol](https://github.com/PepeNetWeb/namespace-protocol) repo defines the on-chain namespace which allows users to register/release names, pay their leases, and sell/trade their names.

Users can lease names using a P2PKH or P2SH (limited to standard n-of-m templates) wallet by issuing namespace opcodes via OP_RETURN.

There are 12 opcodes:

- COMMIT & CLAIM (Front-run proof name registration)
- RELEASE (Give up ownership of a name)
- RENEW (Extend leases)
- TRANSFER (Move a name to a different wallet address)
- SELL/RESERVE/SETTLE (Open market selling/purchasing)
- SELL_TO/PAY (Direct sell offers)
- AS (Change acting vin identity, for custodial multi-op_return operations)
- TRADE (Co-signed name swaps)

Names are leased for up to 1 year and renewed at any time (max 1 year). Leasing cost is tied to network fees using a coinbase fee oracle (coinbase value - 10,000 = network fees collected that block). A 1-Year lease is calculated as the approximate network costs of performing 13 transactions/year. All coin paid to leases is burned in provably unspendable OP_RETURN (not paid to anyone, returned to the commons as deflation). 

No UTXO set or block history pre-activation is necessary to index the namespace, which makes indexers very light.
