---
author: elian
published_utc: 2019-06-20
---

# BTCPay Server RFP

Software Feature Proposal

## Motivation

As our community grows and more contractors around the world earn DCR it becomes a necessity to provide solutions that enable Decred users to spend their DCR as they please. Even though we are putting a critical emphasis on the store of value narrative, it is important to start thinking about the software solutions that can enable to close links in the Decred economy. Providing open-source infrastructure for this end is important in order to have these links ready when Decred grows and people want to integrate DCR as a payment solution and use DCR as a medium of exchange. Furthermore, BTCPay Server is the most decentralised solution for merchant points of sale aligning with Decred's ethos of decentralisation and open-source infrastructure.

## What

Integrate Decred into the BTCPay Server in order to facilitate Decred's merchant acceptance through the standard open-source infrastructure.

Quoting from its [README](https://github.com/btcpayserver/btcpayserver):

> BTCPay Server is a free and open-source cryptocurrency payment processor which allows you to receive payments in Bitcoin and altcoins directly, with no fees, transaction cost or a middleman.
> 
> BTCPay Server is a non-custodial invoicing system which eliminates the involvement of a third-party. Payments with BTCPay Server go directly to your wallet, which increases the privacy and security. Your private keys are never uploaded to the server. There is no address re-use, since each invoice generates a new address deriving from your xpubkey.
> 
> The software is built in C# and conforms to the invoice [API of BitPay](https://bitpay.com/api). It allows for your website to be easily migrated from BitPay and configured as a self-hosted payment processor.

## How

- Write up the RFP.
- Collect feedback from the community.
- Understand the process and details of the integration to calculate cost.
- BTCPay Server offers a comprehensive documentation and excellent support via their Mattermost chat. They have agreed to schedule a call with Decred devs in order to provide more details and guidance on how to set up. According to the BTCPay Server team their software is written in C# and utilizes Docker.
- The software implementing the proposal will be published in Decred's GitHub.

## Who

The who of this proposal is up for Decred community members that would want to take the development. One of the objectives of this proposal is to get more feedback from the devs at Decred in order to get an estimate.

## When

The expected time of competition will depend on the details of this RFP.

Looking at the Monero integration maybe we could think about the following expected time frames, two months of competition and 4 months maximum.

One of the objectives of this proposal is to get more feedback from the devs at Decred in order to get an estimate of hours and budget required.

## Resources

- https://github.com/btcpayserver/btcpayserver-doc/blob/master/docs/Altcoins.md
- https://docs.btcpayserver.org/Altcoins/
- https://docs.btcpayserver.org/FAQ/FAQ-Altcoin/
- https://github.com/btcpayserver/btcpayserver
- https://github.com/dgarage/NBXplorer
- https://github.com/MetacoSA/NBitcoin/tree/master/NBitcoin.Altcoins

Conversations about BTCPay Server integration at Decred's community:

- https://chat.decred.org/#/room/!MgQoetFiyjrHAywokv:decred.org/$15599002037879SAVVU:decred.org
- https://chat.decred.org/#/room/!MiucsxxSPQBpoidaHN:decred.org/$15589903183980CNTkS:decred.org
- https://chat.decred.org/#/room/!zefvTnlxYHPKvJMThI:decred.org/$pflwmNHTiXzkTQ48p3ycQeOxqoOWQsWUc_hgNfOh_3s
- https://twitter.com/marco_peereboom/status/1113874713753862145

Monero integration:

- https://www.reddit.com/r/Monero/comments/afunma/btcpayserver_integration_updates/
- https://repo.getmonero.org/monero-project/ccs-proposals/merge_requests/63
