## Resolution & Verification
After initial deployment, the audit identified that public access blocks were not enforced at the global account level.

Root Cause Analysis: While individual S3 buckets had various permission sets, the lack of an account-level override meant that the environment was susceptible to "configuration drift" and accidental data exposure through human error.

Final Action: Updated the S3 Global Configuration to "Block all Public Access." This implementation ensures that even if a bucket policy or ACL is misconfigured to be public, the account-level guardrail will automatically override and block the access.

Verification: Run: python3 -m prowler aws --checks s3_account_level_public_access_blocks Result: PASS
