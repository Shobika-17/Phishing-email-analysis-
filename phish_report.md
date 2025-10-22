# Phishing Analysis Report — sample.eml

**File analyzed:** sample.eml  
**Date analyzed:** 2025-10-22

## 1. Summary
**Verdict:** HIGH RISK — phishing attempt.
This message impersonates a bank, uses urgent language to force action, contains a mismatched link that points to a suspicious domain, and includes an attachment.

## 2. Sender & Header Analysis
- **From:** Your Bank - Support <support@bank-secure.com>
- **Return-Path:** <bounce@malicious.example.com>
- **Received hops:** mail.malicious.example.com (203.0.113.45), [192.0.2.55]
- **Subject:** Urgent: Verify Your Account Now to Avoid Suspension
- **Message-ID:** <20251022091527.12345@mail.malicious.example.com>

**Notable header anomalies / indicators**
- From address domain (`bank-secure.com`) does not match Return-Path domain (`malicious.example.com`).
- Mail originated from IPs `203.0.113.45` and `192.0.2.55` (not related to the bank).
- No DKIM-Signature or Authentication-Results header present in the raw headers (cannot confirm SPF/DKIM/DMARC pass).

## 3. Links & Domains
Links extracted from the message:
- http://malicious-verify.example.com/login?uid=ABC123
- https://www.yourbank.com/verify
- http://malicious-verify.example.com/login?uid=ABC123">https://www.yourbank.com/verify</a></p>

**Mismatch example (critical):**
- Visible text: `https://www.yourbank.com/verify`  
  Actual href: `http://malicious-verify.example.com/login?uid=ABC123`

This is classic link-masking: the anchor text shows a legitimate bank URL while the real link goes to a malicious domain.

## 4. Attachments
- `invoice.zip` — provided in the message as base64 (placeholder). Treat as malicious. Do NOT download or open on an unisolated machine.
- If you need to analyze the attachment, upload it to VirusTotal or examine it in an isolated VM—do not execute.

## 5. Content / Language Indicators
- Urgent / threatening phrasing: "Failure to verify within 24 hours will result in permanent suspension"
- Calls to action: "verify your identity immediately"
- Tone is designed to create panic and prompt clicking links.

## 6. Risk Assessment & Recommendations
**Risk level:** HIGH

**Immediate recommendations**
1. Do not click any links or open attachments.
2. Delete this email.
3. Block the sending domain(s) and the malicious URL at your email gateway/firewall.
4. Report the phishing attempt to the organization's security team and to your email provider.
5. If credentials were entered on the linked site, immediately change passwords and enable multi-factor authentication.
6. If attachment was opened accidentally, run a malware scan and consult IT/security.

## 7. Evidence files (included)
- headers.txt
- body.txt
- links.txt
- sample.eml

---

*This report was generated from the provided `sample.eml`. The screenshots included are generated visual summaries of the analysis and are not captures from third-party websites.*
