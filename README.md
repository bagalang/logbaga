# logbaga

Structured **JSON lines** on stderr (Track **C3**).

This repository is the package. The compiler and `std` stay in the baga
language monorepo. Check this tree out as `app-product/logbaga` there
(git submodule) so path deps and `-I app-product` keep working.

## Checkout

Inside a baga language clone:

```bash
git submodule update --init app-product/logbaga
# or, first time from a fresh baga tree without the submodule recorded:
git clone git@github.com:bagalang/logbaga.git app-product/logbaga
```

`sandak.toml` keeps `std = { path = "../../std" }`. `fmrbaga` and
`cloudbaga` still depend on `../logbaga`. `tests/log_test.baga` stays
in baga.

```baga
log_info("server up")?
log_info_req("handled", "r-42")?
log_error("boom")?
```

Fields: `ts` (wall ms), `level`, `msg`, optional `req_id`.
Uses `std/json` `json_escape` for safe string values.
