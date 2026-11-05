# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a shipping quote
in dollars. Zones are `local` and `regional`; weights must be positive.

| Service    | Local base | Regional base | Surcharge |
|------------|------------|---------------|-----------|
| `standard` | $5.00      | $8.00         | —         |
| `express`  | $5.00      | $8.00         | +$7.00    |

All services add $1.50 per kg on top of the base. Unknown zones or services
raise `ValueError`.

The command-line entry point prints a quote for an order:

```
python -m warehouse.cli <weight_kg> <zone> [--service {standard,express}]
```

Example:

```
python -m warehouse.cli 3 regional --service express
# $19.50
```
