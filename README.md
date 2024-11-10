# Phishing-Email-Analysis

### Phishing is a type of cyberattack that uses fraudulent emails, text messages, phone calls, or websites to trick people into sharing sensitive data, downloading malware, or otherwise exposing themselves to cybercrime. 

<div>
  <p align="center">
  <img src="pictures/logo.png" width="800"> 
  </p>
</div>

## Useful Tool
[MX Lookup](https://mxtoolbox.com/ "MX Lookup")

## Online URL/Attachment Analysis Tools
[AnyRun](https://app.any.run/ "AnyRun")\
[Hybrid Analysis](https://www.hybrid-analysis.com/ "Hybrid Analysis")

## Reputation Check
[Virustotal](https://www.virustotal.com/gui/ "Virustotal")
[Cisco Talos Intelligence](https://talosintelligence.com/ "Cisco Talos Intelligence")

## Overview
<div>
  <p align="center">
  <img src="pictures/diagram.png" width="800"> 
  </p>
</div>

## Email Header
It is a section of email that contains information like sender, recipient, date, and subject.

### Example:
 
###### MIME-Version: 1.0
###### Received: by 10.220.191.194 with HTTP; Wed, 11 May 2011 12:27:12 -0700 (PDT)
###### Date: Wed, 11 May 2011 13:27:12 -0600
###### Delivered-To: jncjkq@gmail.com
###### Message-ID: <BANLkTi=JCQO1h3ET-pT_PLEHejhSSYxTZw@mail.jncjkq.com>
###### Subject: Test
###### From: Bill Jncjkq <jncjkq@gmail.com>
###### To: bookmarks@jncjkq.net """


## Email Header Analysis
When we suspect an email is phishing, we need to check the headings during a Phishing analysis:

- Was the email sent from the correct SMTP server?
- Are the data "From" and "Return-Path / Reply-To" the same?

# ![image](https://github.com/user-attachments/assets/91932f22-cec2-4b69-90b5-7a41f2ef52f9)
  
##### In this example, the data is different. If we want to reply to this email, we will send a reply to the g-mail address. Just because the data is different, doesn't always mean it's a phishing email. 

# ![image](https://github.com/user-attachments/assets/d4d4e05f-480a-4698-b8c9-47815275488c)

##### As you can see in the image, the email came from the server with the IP address "104.99.94.116". The e-mail came from the domain `info@letsdefend.io`. So, under normal circumstances, "letsdefend.io" is using `101.99.94.116` to send mail. To confirm this, we can query the MX servers that "letsdefend.io" is actively using. 

### [MX Lookup](https://mxtoolbox.com/ "MX Lookup")

An MX lookup is a process that queries the Domain Name System (DNS) to find the Mail eXchanger (MX) records for a specific domain. MX records are DNS records that help domain owners set the email servers for their domains. 
 
An MX lookup is important for email delivery because it helps email servers determine which mail servers are responsible for receiving and handling emails for a domain. An MX lookup tool can also help ensure that emails are routed correctly and securely. 
 
Here are some things an MX lookup tool can do:
- List MX records for a domain in priority order
- Verify reverse DNS records
- Check if the server is an open relay
- Measure the server's response time
- Check each MX record against DNS-based blacklists

# ![image](https://github.com/user-attachments/assets/fcc0fc3b-5be7-4f18-a692-48cc5224ecfd)

If we look at the image above, the domain `letsdefend.io` uses Google addresses as its email server. It means there is no relation with the address "101.99.94.116".

This examination showed that the email did not come from the original address, but was spoofed.


## Static Analysis

Static analysis of a phishing email involves examining the e-mail without executing its contents. Analysts review other attributes such as sender information, email content, links, and attachments to identify potential signs of phishing. Attackers can use HTML to create emails that hide malicious URLs behind buttons or text that appear to be harmless.

# ![image](https://github.com/user-attachments/assets/54ce0864-6e78-4029-8419-69286908a2df)
As seen in the image above, the address the user sees when clicking on a link can be different (the real address is seen when the user hovers over the link). In most phishing attacks, the attackers take a new domain address and complete a phishing attack within a few days. Therefore, if the domain name in the email is new, it is more likely to be a phishing attack. 

By querying [Virustotal](https://www.virustotal.com/gui/ "Virustotal") for web addresses in emails, you can find out if the antivirus engines detect the web address as harmful. If someone else has already analyzed the same address/file in VirusTotal, VirusTotal will not analyze it from scratch, it will show you the old analysis result. 

# ![image](https://github.com/user-attachments/assets/876ba67e-39ad-4504-b807-639543014ec0)


> From the image we can see they were previously analyzed. It doesn't contain malicious content. To scan again, click the `Reanalyze` button. Performing a static analysis of the files in the email can provide insight into the capacity/capability of the file. However, since static analysis takes a long time, dynamic analysis can provide the information you need more quickly.

## [Cisco Talos Intelligence](https://talosintelligence.com/ "Cisco Talos Intelligence")
Cisco Talos Intelligence is a threat intelligence service that helps organizations and the internet community stay secure by detecting, analyzing, and protecting against cybersecurity threats.


# ![image](https://github.com/user-attachments/assets/d3806089-34b9-46fe-9f84-8f580b4672be)

Cisco Talos Intelligence has search sections where we can learn the reputation of IP addresses. By looking up the SMTP address of the email we detected in Talos, we can see the reputation of the IP address and find out if it is on the blacklist. If the SMTP address is blacklisted, it can be assumed that the attack was carried out on a compromised server.

## Dynamic Analysis
Dynamic analysis is a method that analyzes phishing emails and other suspicious files to detect malicious intents. Dynamic Analysis involves executing a suspicious file in a sandbox environment and observing its behavior. This process can help identify malicious intent by tracking the program's actions, such as changes to the registry, memory writes, and API calls to servers. 

## [Browserling](https://www.browserling.com/ "Browserling")
 
Browserling is a cross-browser testing service that allows web designers, developers, and software testers to see how their website looks and functions on different browsers and operating systems.
# ![image](https://github.com/user-attachments/assets/7ada791e-14f4-4b48-a509-5663834f8636)

> The given URL does not lead to anything.

- NOTE- Malware can wait a certain amount of time without taking any action to make detection more difficult. You have to wait for the malware to take action before you decide that the file being scanned is not malicious.

