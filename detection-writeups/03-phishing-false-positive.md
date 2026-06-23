# Phishing Analysis Lab 3: False Positive Phishing Investigation

## Overview

In this lab, I analyzed an email that was flagged or reported as suspicious due to common phishing-like characteristics, including urgency-based language, promotional links, and placement in the spam folder.

After reviewing the sender, authentication results, message content, and link structure, the email was determined to be a false positive. Although the message had traits that can appear suspicious, the evidence supported that it was a legitimate Rock 'n' Roll Running Series promotional email.

---

## Objective

Determine whether the reported email was phishing or a false positive by reviewing:

* Sender information
* Email authentication results
* Message content
* Link and domain usage
* Suspicious or phishing-like traits
* Final analyst verdict

---

## Email Summary

| Field               | Observed Value                                                          |
| ------------------- | ----------------------------------------------------------------------- |
| Claimed Brand       | Rock 'n' Roll Running Series                                            |
| Sender Display Name | Rock 'n' Roll Running Series                                            |
| Sender Address      | [global@engage.runrocknroll.com](mailto:global@engage.runrocknroll.com) |
| Subject             | Zachary, last chance to save $50                                        |
| Return-Path         | 42411547m.info.ironman.com                                              |
| Reply-To            | [global@engage.runrocknroll.com](mailto:global@engage.runrocknroll.com) |
| Sending IP          | 143.244.92.208                                                          |
| Sending Host        | bd77gwy.42411547m.info.ironman.com                                      |
| Email Platform      | HubSpot                                                                 |
| SPF                 | PASS                                                                    |
| DKIM                | PASS                                                                    |
| DMARC               | PASS                                                                    |
| Verdict             | False Positive / Legitimate Promotional Email                           |

---

## Screenshot

![False Positive Email Screenshot](../screenshots/run.png)

---

## Analysis

The email appeared to come from:

```text
Rock 'n' Roll Running Series <global@engage.runrocknroll.com>
```

The sender domain aligned with the claimed brand, and the Reply-To address matched the sender domain:

```text
global@engage.runrocknroll.com
```

The email authentication results showed:

```text
SPF: PASS
DKIM: PASS
DMARC: PASS
```

These results supported that the email was properly authenticated and aligned with the sender domain.

The subject line was:

```text
Zachary, last chance to save $50
```

This subject contained urgency and personalization, both of which can appear in phishing emails. However, in this case, the urgency was part of a normal promotional campaign for the Global Running Day sale.

The body of the email advertised race pricing, a sale deadline, and event-related promotional content. The email used marketing and tracking links through:

```text
email.runrocknroll.com
```

The message also referenced:

```text
mailtimers.com
```

This appeared to be related to marketing content, likely a countdown timer or campaign element. While third-party links should always be reviewed, this alone was not enough to classify the email as phishing.

Additional signs of legitimacy included the presence of unsubscribe links, preference management options, HubSpot abuse-reporting information, and a physical business address in the footer.

---

## Suspicious Traits Reviewed

| Trait                 | Finding                                             |
| --------------------- | --------------------------------------------------- |
| Urgency language      | “Last chance” and “ends tonight” were used          |
| Personalization       | Recipient name appeared in the subject              |
| Promotional links     | Links used `email.runrocknroll.com` tracking URLs   |
| Third-party content   | `mailtimers.com` appeared in the message            |
| Spam-folder placement | Message was treated as suspicious by mail filtering |
| Authentication        | SPF, DKIM, and DMARC all passed                     |
| Credential request    | No credential request observed                      |
| Payment request       | No payment update request observed                  |
| Attachment risk       | No suspicious attachment observed                   |

---

## Email Artifacts / Review Items

```text
global@engage.runrocknroll.com
engage.runrocknroll.com
42411547m.info.ironman.com
email.runrocknroll.com
mailtimers.com
143.244.92.208
bd77gwy.42411547m.info.ironman.com
1780531970526.2db04f6a-adb1-453b-adbf-add6514a1164@42411547m.info.ironman.com
Zachary, last chance to save $50
```

These artifacts could be used to search mail logs or email security tools if additional validation was needed. They are not indicators that an endpoint was compromised.

---

## Verdict

```text
Final Verdict: False Positive
Classification: Legitimate Promotional Email
```

The email was not classified as phishing. While it contained urgency-based marketing language and tracking links, the sender information, authentication results, unsubscribe options, and message content supported that the email was legitimate.

---

## Recommended Response

In a real SOC environment, the recommended actions would be:

* Close the report as a false positive
* Document the reason for the false positive determination
* Advise the user to navigate directly to the official website if they are uncomfortable clicking links
* Mark the message as not phishing if the email security platform supports analyst dispositioning
* Avoid blocking the sender unless additional malicious evidence is found

---

## Conclusion

This lab demonstrated how a SOC analyst reviews a suspected phishing email and determines whether it is malicious or a false positive.

Although the message contained some phishing-like traits, including urgency, personalization, and tracking links, the technical evidence supported legitimacy. The email passed SPF, DKIM, and DMARC checks, aligned with the claimed sender, and contained standard marketing email features.

The final determination was that the message was a false positive phishing report.
