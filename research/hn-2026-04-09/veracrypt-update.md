# VeraCrypt Project Update
**Source:** https://sourceforge.net/p/veracrypt/discussion/general/thread/9620d7a4b3/  
**HN Score:** 1212

## Summary

The VeraCrypt maintainer (Mounir IDRASSI) posted that Microsoft silently terminated his developer account — the one used to sign Windows drivers and the bootloader. No warning, no explanation, no appeal process. He reached out through multiple channels and got only automated responses.

The practical consequences:
- Cannot publish Windows updates for VeraCrypt (the majority platform)
- Linux and macOS updates can still be released
- The existing Windows release is signed with a 2011 CA that will expire later this year
- Once the 2011 EFI CA is revoked, system encryption (full disk) will break on Windows
- Non-system volumes (file containers, partitions) should continue working regardless

The maintainer says there are "positive signs" the issue will be resolved, but the situation is unresolved as of the post.

## Why It's Relevant

Peripheral to your direct work, but a notable story about platform dependency risk for open source projects. A single company (Microsoft) can effectively disable a widely-used security tool with no recourse. Worth a thought if any of your tooling depends on platform-controlled signing or certification.

## Key Takeaway

Open source sustainability + platform dependency risk. The real lesson isn't about VeraCrypt specifically — it's about what happens when critical infrastructure has a single point of failure controlled by a vendor.
