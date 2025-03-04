# Calculating with Reference to Parameter UUIDs in Norms

## Overview

In the JavaScript formulas for norm outputs (like B0 and B1), you can reference parameters using their IDs in the `values` object. Each parameter's ID is a UUID that you can find in the parameters table.

## Identifying Parameter IDs

Here's how to identify and use parameter IDs:

1. In the ParameterPanel, you can see each parameter's ID in the database
2. In the norm's output formula, reference parameters like this:

```javascript
// Example B0 formula using parameter UUIDs
values['123e4567-e89b-12d3-a456-426614174000'] + 
values['987fcdeb-51a2-3b4c-9d8e-765432109876']
```

## Best Practices for Readability

To make your formulas more readable and maintainable, consider these approaches:

### Option 1: Add comments mapping UUIDs to parameter codes

```javascript
// Parameters:
// Z1: 123e4567-e89b-12d3-a456-426614174000
// Z2: 987fcdeb-51a2-3b4c-9d8e-765432109876

values['123e4567-e89b-12d3-a456-426614174000'] + // Z1
values['987fcdeb-51a2-3b4c-9d8e-765432109876']   // Z2
```

### Option 2: Store IDs in variables at the top

```javascript
const Z1 = '123e4567-e89b-12d3-a456-426614174000';
const Z2 = '987fcdeb-51a2-3b4c-9d8e-765432109876';

values[Z1] + values[Z2]
```

## Finding Parameter IDs

You can find each parameter's ID by:

1. Looking at the parameters table in the admin interface
2. Using the browser dev tools to inspect the network requests
3. Checking the database directly

## Parameter ID Reference

For a complete reference of parameter IDs, please refer to the official documentation:

[DIN 50929-3 Parameter Reference](https://github.com/cavort-konzepte-gmbh/pv-corr-math/blob/main/norms/din-50929-3.md)

## Example of a Complete Formula

```javascript
// Parameter UUID references
const Z1 = '957468d4-f953-451a-b1e0-90bf1d04e836';
const Z2 = 'f47c0645-f9d4-4ca0-9eb1-a8cbf38d037e';
const Z3 = '0ee3b071-107a-416b-9e38-126cf82fd4a4';

// B0 calculation formula
return values[Z1] * 0.5 + values[Z2] * 0.3 + values[Z3] * 0.2;
```
