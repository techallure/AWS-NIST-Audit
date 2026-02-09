## Resolution & Verification
During the security assessment, the audit identified that the AWS Root user account was only protected by a single-factor password.

Root Cause Analysis: The Root user is the most privileged identity in the AWS environment. Without Multi-Factor Authentication (MFA), the account was vulnerable to a complete takeover if credentials were compromised. This lack of a "second factor" failed to meet the foundational security requirements of NIST CSF 2.0 (PR.AA-P1).

Final Action: Logged in as the Root user and assigned a Virtual MFA device (Time-based One-Time Password) via the IAM Security Credentials dashboard. This ensures that any future login attempts require both the password and a unique, time-sensitive code from a synchronized authenticator app.

Verification: Run: python3 -m prowler aws --checks iam_root_mfa_enabled Result: PASS
