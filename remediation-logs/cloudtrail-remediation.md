## Resolution & Verification
After enabling Multi-Region logging, the initial Prowler re-scan still showed a 'FAIL'. 

**Root Cause Analysis:** The trail was global, but "Read" management events and "KMS" event logging were disabled to save on costs. While this saved money, it created a compliance gap under NIST CSF 2.0 (Continuous Monitoring).

**Final Action:** Updated the Event Selector to include 'All' Read/Write management events and included KMS activity.

**Verification:**
Run: `python3 -m prowler aws --checks cloudtrail_multi_region_enabled_logging_management_events `
Result: **PASS**
