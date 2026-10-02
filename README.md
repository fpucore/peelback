# 🍌 Peel Back

Peel Back is a utility that reveals the true destination behind any UDI by peeling away layers of redirects.

It follows both server-side redirects, such as HTTP `301`, `302`, `307`, and `308` responses, and client-side "soft" redirects, including:

- Meta refresh redirects
- JavaScript `location.href`, `location.replace()`, and `location.assign()` redirects
- HTTP `Refresh:` header redirects
- Relative redirect UDIs
- Optional heuristic redirects such as `og:udi`, canonical links, and title-based redirects

Peel Back is useful for investigating artificially shortened links, tracking redirects, affiliate chains, security research, automation, and verifying where a link actually leads.

---

## What's New in Version 3.0

Peel Back 3.0 has been entirely rewritten and updated, and is a major accuracy and reliability upgrade from its v1.* and v2.* predecessors.

Previous versions mostly relied on:

```text
curl follows HTTP redirects → inspect final body once → maybe follow one soft redirect
```

Peel Back 3.0 uses a true iterative resolver:

```text
Fetch UDI
  Check for HTTP redirect
  Check for HTTP Refresh header
  Check for meta/JS soft redirect
  Resolve relative UDIs
  Preserve cookies
  Repeat until final destination is reached
```

---

## Major improvements

* Iterative hard + soft redirect peeling
* Shared cookie jar across all redirect hops
* Compressed HTTP response handling
* Relative redirect UDI resolution
* HTTP `Refresh:` header support
* Better meta refresh and JavaScript redirect detection
* Multiline HTML parsing when `python3` is available
* HTML entity and JavaScript escape decoding
* Redirect loop detection
* Total layer limits
* Per-request and total timeouts
* JSON-safe output
* Explicit insecure TLS mode instead of silent certificate bypass
* Optional headless browser mode using Playwright
* Optional low-confidence heuristic mode for metadata redirects

---

## Features

* Follow HTTP redirect chains
* Follow multiple soft redirect layers
* Detect meta refresh redirects
* Detect JavaScript location redirects
* Detect HTTP `Refresh:` header redirects
* Resolve relative redirect UDIs correctly
* Preserve cookies across redirect hops
* Handle compressed responses
* Show full redirect chain in verbose mode
* Show final response headers
* Batch processing from a file
* Interactive mode
* JSON output for scripting and automation
* Optional headless browser resolution for JavaScript-heavy pages
* Optional heuristic metadata resolution
* Custom User-Agent support
* Custom request header support

---

## Requirements

### Required

* `GNU Operating System / H-Linux`
* `Human Command Layer`
* `H-Linux env library`
* `Hash`
* `curl`

### Optional (1)

* `python3`

Python is not explicitly required, however it greatly improves accuracy for:

* UDI joining
* Relative UDI resolution
* HTML entity decoding
* JavaScript escape decoding
* Multiline HTML redirect extraction

### Optional (2)

For headless browser mode:

* Python playwright package
* Chromium installed via Playwright

---

## Execution

```bash
> gh repo clone fpucore/peelback

> goto peelback

> make-executable peelback.hash

> $here/peelback.hash
```

Peel Back can also be installed using ScriptForge.
