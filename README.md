# Procurement Bid Conformance

ProcurementBidConformance stores mandatory criteria before bids are accepted. Bidders submit evidence while the tender is open; the issuer closes the tender before evaluating individual bids. Validators classify criteria as met, exception, or unknown and record RESPONSIVE, NON_RESPONSIVE, or INCOMPLETE. The contract does not rank bids or automatically award a tender.

## Repository

- Repository name: `procurement-bid-conformance-genlayer`
- Description: Evaluates individual procurement bids against fixed requirements without selecting a winner.
- Contract file: `procurement_bid_conformance.py`
- Runner dependency: pinned `py-genlayer:1jb45aa8ynh2a9c9xn3b7qqh8sm5q93hwfp7jqmwsfhh8jpz09h6`

## Intended workflow

See the public methods and state transitions in `procurement_bid_conformance.py`. The contract uses independent leader/validator execution for web evidence and writes persistent state only after the consensus call returns.

## Validation before deployment

Run from the repository root:

```bash
genvm-lint check procurement_bid_conformance.py
genvm-lint schema procurement_bid_conformance.py
pytest tests/direct/ -v
# Then run the configured integration tests against the target GenLayer environment.
```

Static syntax checks are not a substitute for GenVM lint, schema validation, or consensus integration tests.

## Scope and limitations

This contract evaluates the evidence submitted through its public interface. It does not guarantee the truth of an off-chain source, replace legal/professional review, or make an external system perform an action unless an integration is explicitly implemented.
