# Contracts

## Snapshot Testing

This workspace uses Soroban SDK's built-in test snapshots to prevent unintentional regressions in emitted events and ledger storage keys. 

When you run tests, the SDK automatically records the state of the `Env` and saves it to JSON files in the `test_snapshots/` directory of each contract.

### Updating Snapshots

If you intentionally change a contract's emitted events or storage schema, the test snapshots will change. To update the snapshots, simply run the tests locally:

```bash
cargo test --workspace
```

Then, commit the updated `.json` files in the `test_snapshots/` directories to your branch.

```bash
git add "*/test_snapshots/*"
git commit -m "Update test snapshots"
```

The CI workflow will automatically verify that the snapshots match the committed schemas and will fail if there are uncommitted changes.
