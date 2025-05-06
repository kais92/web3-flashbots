## [3.0.0] – 2025-05-06

### Breaking Changes
- Renamed all `.rawTransaction` properties to `.raw_transaction` (Web3.py v7 naming).
- Completely refactored middleware for Web3.py v7: now a class-based middleware using `wrap_make_request`.
- Overhauled `FlashbotProvider`:
  - Replaced internal Web3 HTTP utils with `requests.post`.
  - Switched to EIP-191 signing via `eth_account.messages.encode_defunct`.
  - Removed deprecated imports from `eth_account._utils`.

### Added
- Official compatibility with Web3.py v7 (7.x series).
- New helper `get_transaction_type()` to detect legacy, access list, and EIP-1559 tx types.
- Expanded tests covering `_parse_signed_tx` for legacy, EIP-2930 (type=1), and EIP-1559 (type=2) transactions.

### Fixed
- Ensured numeric RLP fields (bytes) are converted to `int`.
- Added recovery of `chainId` for legacy transactions signed under EIP-155.
- Updated examples (`examples/simple.py`) to use `.raw_transaction` and new middleware/provider APIs.

