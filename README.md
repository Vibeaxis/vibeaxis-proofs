# VibeAxis Proofs — Public Ledger 🔏

**What this is:** our append-only ledger of content proofs for VibeAxis.  
Each post (or artifact) is canonicalized → hashed (SHA-256) → recorded here as a JSON entry.  
The git commit timestamp is the notarization.

**Live site:** https://vibeaxis.com/  
**Proof Stamp plugin:** https://github.com/vibeaxis/vax-proof-stamp  
**Wiki:** https://github.com/vibeaxis/vibeaxis-proofs/wiki

---

## Why this exists
Receipts beat vibes. When we say something, we can prove *when* we said it and whether it changed.  
This repo is that public evidence: human-readable, tool-friendly, and portable.

---

## Quick verify (no tools required)
- On any post at vibeaxis.com, use the **Proof** link from the Proof Stamp widget to view its proof.
- Or open this repo’s **ledger** folder, find the matching JSON, and compare the `sha256` to a hash of the post’s canonical text (any SHA-256 site works).

See **Wiki → Verify a Proof** for a click-by-click walkthrough.

---

## What’s in a ledger entry
A typical JSON file includes:

```json
{
  "version": "1",
  "id": "2025-10-11T14:32:00Z_vibeaxis-what-we-say",
  "source_url": "https://vibeaxis.com/p/what-we-say/",
  "content_canonical": {
    "encoding": "utf8",
    "normalization": "nfkc+whitespace-collapse"
  },
  "sha256": "…hex…",
  "created_at": "2025-10-11T14:32:07Z",
  "by": "vibeaxis-proof-stamp",
  "notes": "First publish"
}
We store hash + metadata, not the full content.

Directory layout (default)
markdown
Copy code
ledger/
  2025/
    10/
      20251011-1432_what-we-say.json
If your structure varies, the schema stays the same; only folders change.

How entries are created
Editors publish/update a post on vibeaxis.com.

The vibeaxis-proof-stamp plugin canonicalizes the text and computes a SHA-256.

A JSON proof is written to this repo (PR or direct commit).

Git history becomes the public audit trail.

Trust model (short)
Integrity: commit history + hashes

Timing: commit timestamps (optionally anchored elsewhere later)

Privacy: ledger stores hashes; content lives on vibeaxis.com

Full details: Wiki → Security & Threat Model

Links
Live site: https://vibeaxis.com/

Plugin: https://github.com/vibeaxis/vibeaxis-proof-stamp

Wiki: https://github.com/vibeaxis/vibeaxis-proofs/wiki

Releases: https://github.com/vibeaxis/vibeaxis-proofs/releases

Issues: https://github.com/vibeaxis/vibeaxis-proofs/issues
