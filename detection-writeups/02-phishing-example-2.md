# Phishing Analysis Lab 2: Cloud Storage Payment Scam

## Overview

In this lab, I analyzed a suspicious email claiming that a cloud storage account had been locked and that the recipient’s photos and videos would be removed. The email used urgency, payment-related pressure, and suspicious sender infrastructure to encourage the recipient to click a link and update payment details.

The purpose of this lab was to practice a SOC analyst phishing review workflow using email header information, authentication results, message content, and suspicious links.

---

## Objective

Determine whether the email was legitimate, spam, or phishing by reviewing:

* Sender information
* Email authentication results
* Message content
* Suspicious domains and links
* Social engineering indicators
* Email artifacts for further investigation

---

## Email Summary

| Field               | Observed Value                                                                                            |
| ------------------- | --------------------------------------------------------------------------------------------------------- |
| Claimed Service     | Cloud Storage                                                                                             |
| Sender Display Name | user                                                                                                  |
| Sender Address      | [zwkqrz@ptkiubckkpeeebtrqaisntvxzl.net](mailto:zwkqrz@ptkiubckkpeeebtrqaisntvxzl.net)                     |
| Subject             | user, Your Cloud Account has been locked... Your photos and videos will be removed!                   |
| Return-Path         | [Return@rth0r2h3ttttt.mooer5-pomme5.methinki.com](mailto:Return@rth0r2h3ttttt.mooer5-pomme5.methinki.com) |
| Reply-To            | [Reply@3guz1.dvg3fcw.uic.edu](mailto:Reply@3guz1.dvg3fcw.uic.edu)                                         |
| Sending IP          | 162.217.100.118                                                                                           |
| Received From       | slughin.com                                                                                               |
| SPF                 | PASS                                                                                                      |
| DKIM                | FAIL                                                                                                      |
| DMARC               | FAIL                                                                                                      |
| Observed Link       | storage.googleapis.com/hableeeeq/activeeed.html                                                           |
| Verdict             | Phishing                                                                                                  |

---

## Screenshot

![Cloud Storage Phishing Email Screenshot](../screenshots/cloud.png)

---

## Analysis

The email claimed that the recipient’s cloud account had been locked and warned that photos and videos would be removed. This is a common phishing tactic because it creates urgency and fear of data loss.

The sender appeared as:

```text
user <zwkqrz@ptkiubckkpeeebtrqaisntvxzl.net>
```

The sender domain was random-looking and did not match a known cloud storage provider. The Reply-To address also used a different domain:

```text
Reply@3guz1.dvg3fcw.uic.edu
```

This mismatch between the From address, Return-Path, and Reply-To address was suspicious and suggested the message was not from a legitimate cloud storage service.

The email authentication results showed:

```text
SPF: PASS
DKIM: FAIL
DMARC: FAIL
```

The SPF pass only showed that the sending server was authorized for the return-path domain. It did not prove the email was legitimate. The DKIM and DMARC failures were more concerning because they showed the message failed stronger sender verification and alignment checks.

The email body used a payment-update lure. The HTML content claimed there was a payment issue with a Cloud Storage Premium subscription and instructed the user to update payment details.

The observed link pointed to:

```text
storage.googleapis.com/hableeeeq/activeeed.html
```

Google Cloud Storage is a legitimate hosting service, but attackers can abuse it to host phishing pages or redirects. In this case, the link was suspicious because it appeared in an email with failed authentication and a payment-related phishing lure.

Another suspicious detail was the mismatch between the plain-text and HTML content. The plain-text section referenced unrelated “Top Stories of the Day,” while the HTML section contained the cloud storage payment warning. This type of mismatch can be used to confuse filters or hide the true purpose of the email.

---

## Phishing Indicators

| Indicator                | Evidence                                                      |
| ------------------------ | ------------------------------------------------------------- |
| Urgency / fear tactic    | Claimed account was locked and photos/videos would be removed |
| Payment lure             | Requested updated payment details                             |
| Suspicious sender domain | Used `ptkiubckkpeeebtrqaisntvxzl.net`                         |
| Sender mismatch          | From, Return-Path, and Reply-To used different domains        |
| Authentication failure   | DKIM failed and DMARC failed                                  |
| Suspicious hosted link   | Used `storage.googleapis.com` URL                             |
| Body mismatch            | Plain-text content did not match HTML phishing content        |

---

## Email Artifacts / Search Indicators

```text
zwkqrz@ptkiubckkpeeebtrqaisntvxzl.net
ptkiubckkpeeebtrqaisntvxzl.net
Return@rth0r2h3ttttt.mooer5-pomme5.methinki.com
rth0r2h3ttttt.mooer5-pomme5.methinki.com
Reply@3guz1.dvg3fcw.uic.edu
3guz1.dvg3fcw.uic.edu
162.217.100.118
slughin.com
storage.googleapis.com/hableeeeq/activeeed.html
QBHFE.XVZAAV.qmail@localhost.localdomain
```

These artifacts could be used to search email logs, mail security tools, or SIEM data for similar messages. They do not prove that an endpoint was compromised by themselves.

---

## Verdict

```text
Final Verdict: Phishing
Classification: Cloud Storage Impersonation / Payment Update Scam / Possible Credential or Payment Harvesting Attempt
```

The email was classified as phishing because it used a suspicious sender domain, failed DKIM and DMARC authentication, used mismatched sender infrastructure, created urgency around account/data loss, and directed the user to update payment information through a suspicious hosted link.

---

## Recommended Response

In a real SOC environment, the recommended actions would be:

* Report the email as phishing
* Do not click the link or reply to the sender
* Block or flag the sender domain and related domains
* Search for similar emails using the subject, sender, IP address, and observed URL
* Check whether any users clicked the link
* Investigate any users who submitted credentials or payment information

---

## Conclusion

This lab demonstrated a phishing investigation involving a fake cloud storage payment issue. The email attempted to pressure the recipient into updating payment details by claiming the account was locked and personal files could be removed.

Based on the failed authentication results, suspicious sender infrastructure, mismatched email content, and payment-related lure, the email was determined to be phishing.
