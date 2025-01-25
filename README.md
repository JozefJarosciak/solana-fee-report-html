# Solana Fee Report (Browser-Based)

This is a browser-based tool for analyzing priority fees (and compute units) in Solana transactions, built using ideas from Jack Levin's Solana Transaction Inspector](https://github.com/jacklevin74/solana_fee_report).

**Live Demo:**  
[https://xen.pub/solana-fee-report.html](https://xen.pub/solana-fee-report.html)

## Overview

- **Fetches Solana blocks** using your preferred RPC endpoint (Helius recommended).
- **Analyzes transactions** for priority fees, skipping voting transactions.
- **Calculates** maximum, average, median, and 95th percentile fee data.
- **Also calculates** compute units used in the transactions.
- **Stores** results in your browser's IndexedDB for convenient reference.
- **Displays** results in an interactive table (with pagination, sorting, and filtering).

## Why This Tool?
- Investigate how often high priority fees appear in blocks.
- Get an idea of compute unit usage over recent blocks.
- Compare fee data across multiple batches of Solana blocks.

## Quick Start

1. **Clone or download** this repository.
2. **Open** the `solana-fee-report.html` (or use the [live demo link](https://xen.pub/solana-fee-report.html)) in your browser.
3. **Configure** your settings:
    - **RPC Endpoint URL**: Provide your own RPC endpoint; e.g., Helius free RPC:  
      `https://mainnet.helius-rpc.com/?api-key=YOUR_API_KEY`
      > **Note**: Public endpoints like `https://api.mainnet-beta.solana.com` often block these requests.
    - **Number of Block Batches** (e.g., 2)
    - **Blocks per Batch** (e.g., 5)
    - **Delay** (seconds) between batch fetches
4. **Click "Start Analysis"** to begin fetching and analyzing.

Or just use https://xen.pub/solana-fee-report.html

## Important Notes

- **Use your own RPC endpoint** when testing to avoid rate limits or blocked requests.
- It **works great** with the [Helius Labs RPC](https://helius.xyz) (they offer a free API key).
- Data is stored in your browser's IndexedDB and displayed in the "Stored Block Data" section.
- No server-side code is needed—everything runs in your browser.

## Options & Features

1. **RPC Endpoint URL**
    - Input any URL for a Solana RPC (e.g., `https://mainnet.helius-rpc.com/?api-key=...`).

2. **Number of block batches**
    - Defines how many groups of blocks will be fetched and analyzed in one run.
    - Example: 2 means you will fetch 2 separate “batches”.

3. **Blocks per batch**
    - Each batch fetches a certain number of blocks (e.g., 5).
    - The script moves backward from the latest slot, covering `(batchSize * numSamples)` blocks total.

4. **Delay (seconds) between fetches**
    - If you want to avoid RPC rate limits or slow things down, add a delay.
    - Example: 1 means each block request will wait 1 second before the next.

5. **Table for Stored Data**
    - **Pagination**: Shows 20 entries per page.
    - **Filtering**: Type a slot or ID in the “Filter” box to narrow down results.
    - **Sorting**: Click any column header (ID, start_slot, fee data, etc.) to sort ascending/descending.

## Credits & License

- Built upon [@mrJackLevin's Solana Transaction Inspector](https://github.com/jacklevin74/solana_fee_report).
- **License**: MIT. Feel free to fork and modify.
- Created by community members and shared as-is, with no guarantees.

Enjoy analyzing Solana fees! If you have any questions or issues, please feel free to open an issue or contribute a PR.
