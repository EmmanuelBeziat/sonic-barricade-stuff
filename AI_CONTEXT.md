## Lyrics LRC files

**General**
- `[colors:0xFFFFFFFF]` and `[chordsColors:0xFF4CAF50]` must always be present
- All LRC timestamps must be `[MM:SS.mmm]` (two-digit minutes, two-digit seconds, three-digit millis).
- Hours are not used; do not accept `[H:MM:SS]` or `[M:SS.xx]`.
- Keep `[00:00.000]` title lines unchanged unless told otherwise.
- When asked to retime from a given timestamp, apply the offset to that line and every subsequent line, earlier lines unchanged.
- Preserve existing whitespace/indentation and ordering.

**Formatting invariants**
- Normalize `[1:01.10]` → `[01:01.100]`
- Normalize `[00:26.45]` → `[00:26.450]`
- Millisecond precision always 3 digits.
- One timestamp per line, always at column 1, wrapped in `[]`.

**Safety checks**
- No decreasing timestamps after normalization.
- No negative times after offsets.
- Reject/flag lines that lack a timestamp or have malformed brackets.