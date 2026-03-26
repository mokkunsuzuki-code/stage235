# Stage235: GitHub Verified Commit (GPG Identity Binding)

This stage binds a local GPG signing key to a GitHub account,
enabling GitHub to display **Verified** status for signed commits.

## Overview

Stage234 introduced real cryptographic signing using:

- Ed25519 keys for repository-level signing
- GPG keys for identity-based signing

Stage235 extends this by linking the GPG public key to GitHub,
so that signed commits can be verified on the GitHub platform itself.

## What This Enables

- GitHub **Verified** badge on commits
- Stronger commit authorship authenticity
- Public auditability of commit origin
- Platform-level identity binding for signed commits

## Verification Flow

Local commit signed with private GPG key  
↓  
GitHub receives the signed commit  
↓  
GitHub matches the signature to the registered public key  
↓  
**Verified** badge is displayed

## Requirements

- Local GPG key pair
- Public GPG key registered on GitHub
- Git configured to use the signing key
- Verified email address on GitHub matching the GPG identity

## Local Setup

### 1. Check the GPG key

```bash
gpg --list-secret-keys --keyid-format=long
2. Configure Git signing
git config --global user.name "Motohiro Suzuki"
git config --global user.email "mokkun.suzuki@gmail.com"
git config --global user.signingkey 395BFEB61D50FB25
git config --global commit.gpgsign true
3. Ensure GPG agent works
export GPG_TTY=$(tty)
Export Public Key
gpg --armor --export 395BFEB61D50FB25 > gpg_pubkeys/stage235_github_public.asc

Register the exported public key on GitHub:

Settings → SSH and GPG keys → New GPG key

Create a Signed Commit
git commit -S -m "Stage235: GitHub Verified commit (GPG identity binding)"
git push
Expected Result

On GitHub, the commit should display:

Verified

Verification Notes
Verified means GitHub successfully verified the commit signature
This is a strong proof of commit authenticity on the platform
It is not an absolute real-world identity guarantee
Private keys must never be committed
Stage Progression
Stage233 → External signature verification structure
Stage234 → Real cryptographic signing with Ed25519 and GPG
Stage235 → GitHub platform-level verified commit identity
Security Model Extension

The system now binds:

Claim
↓
Evidence
↓
Manifest
↓
Signature
↓
GitHub Verified Identity

This connects cryptographic proof with platform-level identity verification.

License

MIT License

© 2025 Motohiro Suzuki