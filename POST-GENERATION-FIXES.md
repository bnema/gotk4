# Post-Generation Fixes

This file documents fixes that need to be applied after regenerating bindings.

## How to Apply

After regenerating the bindings, run:

```bash
git apply post-generation-fixes.patch
```

## Fixes Included

### 1. GSK BorderNode Colors - Double Pointer Bug

**File:** `pkg/gsk/v4/gsk.go`
**Line:** ~1433
**Issue:** Generator creates `src := &_cret` when `_cret` is already a pointer (`*C.GdkRGBA`), causing a double pointer error.
**Fix:** Change to `src := _cret`

**Root Cause:** This is a bug in the code generator that needs to be fixed upstream in `gir/girgen/`.

## TODO

- [ ] Fix the generator to handle array return types correctly
- [ ] Submit PR to upstream gotk4 repository
