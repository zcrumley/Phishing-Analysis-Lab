# Phishing Analysis Labs

## Overview

This repository contains a series of phishing email analysis labs focused on reviewing suspicious and user-reported emails. The purpose of these labs was to practice analyzing email artifacts, reviewing sender details, inspecting links and domains, and documenting findings in a clear investigation format.

The labs include confirmed phishing emails as well as a false-positive investigation. This helps show that email analysis is not just about identifying malicious messages, but also about using evidence to determine whether an email is phishing, suspicious, legitimate, or unwanted marketing.


## Objective

The objective of these labs was to practice the workflow of a SOC analyst reviewing user-reported emails.

Each lab focused on:

* Reviewing the email subject, sender, and message body
* Analyzing email headers and authentication results
* Inspecting links and domains
* Identifying suspicious indicators
* Determining whether the email was phishing, suspicious, spam, or legitimate
* Writing a concise investigation report with a final verdict


## Labs Included

This lab series includes three phishing email investigations:

| Lab   | Focus                                          | Verdict                     |
| ----- | ---------------------------------------------- | --------------------------- |
| Lab 1 | Lowe’s brand impersonation email               | Phishing                    |
| Lab 2 | Cloud storage file-sharing email               | Phishing       |
| Lab 3 | Rock 'n' Roll Running Series promotional email | False Positive |

Each lab follows the same investigation format and documents the email summary, analysis, indicators, verdict, recommended response, and conclusion.


## Analyst Workflow

The same basic workflow was used for each investigation:

1. Review the reported email
2. Identify the sender, subject, and message purpose
3. Review the email body for urgency, impersonation, or suspicious language
4. Analyze email authentication results such as SPF, DKIM, and DMARC
5. Inspect links and destination domains without directly opening suspicious content
6. Identify phishing indicators or reasons the message may be legitimate
7. Assign a final verdict
8. Document the findings and recommended response

## Skills Demonstrated

These labs demonstrate the following SOC analyst skills:

* Phishing email triage
* Email header analysis
* SPF, DKIM, and DMARC review
* URL and domain inspection
* Brand impersonation detection
* Identification of phishing indicators
* False-positive analysis
* Security documentation
* Safe handling of suspicious emails

## Tools and Techniques Used

The analysis was performed manually using common phishing investigation techniques, including:

* Gmail original message/header review
* Email authentication review
* Manual URL inspection
* Domain comparison
* Message body review
* Indicator extraction
* Markdown documentation

No malicious links were intentionally clicked, and no attachments were opened or executed.

## Report Format

Each lab follows a consistent format:

```markdown
# Phishing Email Analysis Lab

## Overview
Brief summary of the reported email and why it was reviewed.

## Objective
Purpose of the investigation.

## Email Summary
Basic details such as sender, subject, recipient, and message theme.

## Analysis
Review of the sender, message body, links, authentication results, and suspicious traits.

## Indicators
Relevant artifacts or evidence that supported the final verdict.

## Verdict
Final classification of the email.

## Recommended Response
Suggested SOC analyst response or remediation step.

## Conclusion
Short summary of what was learned from the investigation.
```


## Key Takeaways

These phishing labs helped reinforce the importance of reviewing emails from both a technical and analytical perspective. A message should not be judged only by how it looks on the surface. The sender, domain alignment, authentication results, links, message content, and overall context all need to be reviewed before making a final determination.

The labs also showed that not every reported or spam-filtered email is automatically malicious. Some emails may be legitimate marketing messages or false positives, while others may contain clear signs of phishing such as brand impersonation, suspicious links, failed authentication, or credential-harvesting behavior.

Overall, these investigations helped build a repeatable SOC analyst workflow for email triage: review the email, collect evidence, identify suspicious behavior, determine a verdict, and document the findings clearly.


## Disclaimer

These labs were completed for educational and portfolio purposes only. Suspicious emails were reviewed in a controlled manner. Links were not directly clicked, attachments were not opened, and no malicious content was executed.

Any personal information, email addresses, tracking strings, message IDs, internal IP addresses, or account-specific data should be sanitized before publishing.

