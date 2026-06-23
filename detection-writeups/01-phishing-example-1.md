# Phishing Analysis Lab 1: Lowe's Rewards Impersonation

## Overview

In this lab, I analyzed a suspicious email that appeared to impersonate Lowe's Rewards. The email claimed the recipient could claim a free Kobalt tool set, but the sender details, authentication results, and message content showed signs of phishing.

The purpose of this lab was to practice a basic SOC analyst phishing review workflow.

---

## Objective

Determine whether the email was legitimate, spam, or phishing by reviewing:

* Sender information
* Email authentication results
* Suspicious domains
* Message content
* Social engineering indicators
* Indicators of compromise

---

## Email Summary

| Field               | Observed Value                                        |
| ------------------- | ----------------------------------------------------- |
| Claimed Brand       | Lowe's Rewards                                        |
| Sender Display Name | Lowe's-Rewards                                        |
| Sender Address      | [IseDdHeo@xyopihtnn.us](mailto:IseDdHeo@xyopihtnn.us) |
| Subject             | Claim Your Free Kobalt Tool Set             |
| Sender Domain       | xyopihtnn.us                                          |
| Related Domain      | cdcfa.com                                             |
| Observed Domain     | storage.googleapis.com                                |
| SPF                 | PASS                                                  |
| DMARC               | FAIL                                                  |
| Verdict             | Phishing                                              |

---

## Screenshot

![Lowe's Phishing Email Screenshot](../screenshots/lowes.png)

---

## Analysis

The email used the display name `Lowe's-Rewards`, but the actual sender address was:

```text
IseDdHeo@xyopihtnn.us
```

The domain `xyopihtnn.us` does not appear to be associated with Lowe's. The sender username also appeared randomly generated, which is common in spam and phishing campaigns.

The email subject was:

```text
Claim Your Free Kobalt Tool Set
```

This subject used a free reward lure to encourage the recipient to click. Since Kobalt tools are associated with Lowe's, the lure was designed to make the message appear more believable.

The email authentication results showed:

```text
SPF: PASS
DMARC: FAIL
```

The SPF pass only showed that the sending server was authorized for its own sending domain. The DMARC failure was more significant because it showed the message failed sender alignment checks.

The email also referenced the following domains:

```text
cdcfa.com
storage.googleapis.com
```

The related domain `cdcfa.com` did not match the claimed Lowe's identity. The `storage.googleapis.com` domain is a legitimate cloud-hosting service, but it can be abused to host phishing content or redirects.

Another suspicious artifact observed in the email body was:

```text
START NEGATIVE
```

This type of hidden or unusual text may indicate spam-filter evasion or content manipulation.

---

## Phishing Indicators

| Indicator                 | Evidence                                             |
| ------------------------- | ---------------------------------------------------- |
| Brand impersonation       | Claimed to be Lowe's Rewards                         |
| Sender mismatch           | Used `xyopihtnn.us` instead of a Lowe's domain       |
| Reward lure               | Claimed recipient could claim a free Kobalt tool set |
| Authentication issue      | SPF passed, but DMARC failed                         |
| Suspicious infrastructure | Referenced `cdcfa.com` and `storage.googleapis.com`  |
| Possible spam evasion     | `START NEGATIVE` artifact observed                   |

---


## Verdict

```text
Final Verdict: Phishing
Classification: Brand Impersonation / Reward Scam / Spam Filter Evasion
```

The email was classified as phishing because it impersonated Lowe's Rewards, used an unrelated sender domain, failed DMARC, included suspicious infrastructure, and used a free reward lure.

---

## Recommended Response

In a real SOC environment, the recommended actions would be:

* Report the email as phishing
* Block or flag the sender and related domains
* Search for similar emails using the sender, subject, and observed domains
* Review whether any users clicked the link
* Investigate any users who interacted with the message

---

## Conclusion

This lab demonstrated a basic phishing investigation workflow. By reviewing the sender, authentication results, domains, message content, and social engineering indicators, the email was determined to be a phishing attempt impersonating Lowe's Rewards.

I will unfortunately not be recieving a free Kobalt Tool set. 
