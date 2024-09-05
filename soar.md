# SOAR 
This page deals with Security Orchestration Automation and Response.

# Table of content

* [Must read](https://github.com/cyb3rxp/awesome-soc/blob/main/soar.md#must-read)
* [What is SOAR](https://github.com/cyb3rxp/awesome-soc/blob/main/soar.md#what-is-soar)?
* [Simple and commonly needed automation tools](https://github.com/cyb3rxp/awesome-soc/blob/main/soar.md#simple-and-commonly-needed-automation-tools)
* [Common automations](https://github.com/cyb3rxp/awesome-soc/blob/main/soar.md#common-security-automation-use-cases)

# Must read/watch

* PaloAlto, [Security orchestration for dummies](https://www.paloaltonetworks.com/content/dam/pan/en_US/assets/pdf/cortex-xsoar/Security-Orchestration-For-Dummies-Demisto-Special-Edition.pdf);
* ThreatConnect, [SIRP / SOA / TIP benefits](https://threatconnect.com/blog/realizing-the-benefits-of-security-orchestration-automation-and-response-soar/);
* Swimlane, [Cyber Threat readiness report 2023](https://swimlane.com/wp-content/uploads/Cyber-Threat-Readiness-Report-2023.pdf);
* Swimlane, [Automating SIEM alert triage](https://swimlane.com/resources/videos/automating-siem-alert-triage-demo/?utm_source=pardot&utm_medium=email_newsletter);
* Gartner, [Market Guide for Security Orchestration, Automation and Response Solutions](https://www.gartner.com/doc/reprints?id=1-2ADE1K2G&ct=220621&st=sb);
* Microsoft, [Microsoft Defender XDR , Security Copilot and Sentinel integrated into 1 portal](https://techcommunity.microsoft.com/t5/microsoft-mechanics-blog/microsoft-defender-xdr-security-copilot-amp-microsoft-sentinel/ba-p/3989312);
* RecordedFuture [The Automation Advantage: Transforming Cybersecurity and Efficiency in Organisations](https://go.recordedfuture.com/automation-advantage-webinar?utm_medium=email&_hsenc=p2ANqtz-_zNWKiR0eBOCpx_R5cUwRu3iPfgPI8BeMLutfF1ywpL5i6LleQRxBvCUZ-dbaseqlfOWtLVikC5-lmwPYyhQCltn4Clg&_hsmi=316108876&utm_content=316108876&utm_source=hs_email)
* PaloAlto, [Top security orchestration use cases](https://www.paloaltonetworks.com/engage/cortex-xsoar/top-security-orchestration-use-cases?utm_source=marketo&utm_medium=email&utm_campaign=Global-NU-EN-21-04-14-XX-P3-Cortex-XSOAR.EN-NU05-Cortex_XSOAR-MOFU&utm_network=pf&mkt_tok=NTMxLU9DUy0wMTgAAAGRtyevdpJBsF0cPQpwRMziLi8AsU4MneA1CMmGAGggPsBuYenJW9khG5e7Wqa78zC0GcLaP0a2R-e6bJpJ0BQAwEKLDrSpqe6npkmcM3DpNXSeqbeAJ9E&_pfses=Rx9LBfVH47t8TMQ542Kr7pCt#page=3)
* PTP, [SOAR-based security monitoring](https://ptp.cloud/soar-based-security-monitoring/)

# What is SOAR?

As per [Gartner definition](https://securityboulevard.com/2021/08/gartner-soar-magic-quadrant-when-where-and-how/):

![image](https://user-images.githubusercontent.com/16035152/186781422-ebb3996a-da66-4d27-a55f-6065fa84fca5.png)

Hence the statement that **SOAR is in fact made of 3 critical tools** (see drawing above): 
* SIRP;
* TIP;
* SOA.

And on top of that, SIEM.

Thus, in my view as well in Gartner's mind when they invented the name, **SOAR is more an approach, a vision, based on technologies and processes**, than a technology or a tool per say. 

More especially, SOAR mainly aims at:
* reducing human error;
* offloading repetitive and valueless tasks for humans, to an automate (security orchestrator);
* improving integration between tools (thanks to API);
* increasing performance of SOC/CERT teams (higher workload with the same team size), constant quality, and improved processes (quicker processes runs);


# SOAR need for security monitoring

Here is [an example](https://ptp.cloud/soar-based-security-monitoring/) of a SOC workflow leveraging SOAR approach, with the following technology layers in place:
* SIEM: [Fluency](https://www.fluencysecurity.com/),
* SIRP: [TheHive](https://github.com/TheHive-Project/TheHive),
* SOA: [Shuffle](https://github.com/Shuffle/Shuffle),
* TIP: [MISP](https://www.misp-project.org/),
* ITSM: [ConnectWise](https://www.connectwise.com/)

![image](https://github.com/user-attachments/assets/fefe6c00-7f20-4408-a1eb-91622c2c3fbd)


# Simple and commonly needed automation tools

* Online automated hash checker (script):
  * my recommendation: [Munin](https://github.com/Neo23x0/munin), or with PowerShell [Posh-VT](https://github.com/darkoperator/Posh-VirusTotal)

* Online URL automated analysis:
  * my recommendation: [CyberGordon](https://cybergordon.com/), [URLScan.io](https://urlscan.io/)

* Online automated sample analyzer:
  * my recommendation, via script and without sample submission: [Malwoverview](https://github.com/alexandreborges/malwoverview);
  * my recommendations for online dynamic analysis: [Hybrid-Analysis](https://www.hybrid-analysis.com/), [Joe's sandbox](https://www.joesandbox.com/#windows)

* Offline automated sample analyzer:
  * My recommendation: [Qu1cksc0pe](https://github.com/CYB3RMX/Qu1cksc0pe)

* (pure) Windows tasks automation:
  * My recommendations: [AutoIT](https://www.autoitscript.com/site/), [Chocolatey](https://chocolatey.org/)

* SaaS-based (and partly free, for basic stuff) SOA:
  * [Shuffle](https://shuffler.io/)



# Common security automation use cases

## My recommendations for detection (alerts handling):

Try to implement at least the following automations, leveraging the SOA/SIRP/TIP/SIEM capabilities:
* Make sure all the context from any alert is being automatically transfered to the SIRP ticket, with a link to the SIEM alert(s) in case of.
  * Leverage API (through SOA) if needed to retrieve the missing context info, when using built-in integrations.
* Automatically query the TIP for any artefacts or even IOC that is associated to a SIRP ticket.
* Automatically retrieve the history of antimalware detections for an user and/or endpoint, that is associated to a SIRP ticket.
* Automatically retrieve the history of SIEM detections for an user and/or endpoint, that is associated to a SIRP ticket.
* Automatically retrieve the history of SIRP tickets for an user and/or endpoint, that is associated to a new SIRP ticket.
* Automatically query AD or the assets management solution, for artefact enrichment (user, endpoint, IP, application, etc.).


## My recommendations for detection (artefacts investigation):

* Search for a list of IP addresses in the TIP:
   * My recommendation: use a script to query OpenCTI for with a CSV file, and make sure the output will confirm known malicious IP addresses (+ OpenCTI link to the IOC).
* Extract a list of fresh IOCs from the TIP, and embed them in an IOC scanner:
   * My recommendation: use a script extract IP/URL/domains over the last month, MD5 over the last year, and embed them in [Thor Lite](https://www.nextron-systems.com/thor-lite/) or [DFIR-ORC](https://github.com/dfir-orc).


## My recommendations for response (incident response, containment/eradication steps):

* Block an IP on all firewalls (including VPN), SWG and CASB.
* Block an URL on SWG. 
* Block an email address (sender) on SEG.
* Block an exe file (by hash) on endpoints (leveraging antimalware/EDR or AppLocker).
* Block an exe file (by hash) on gateways and CASB: SWG, SEG, CASB.
* Block an internal IP, on internal routers/FW, thanks to ACL (to prevent lateral movement).
* Block an IP address on web servers, linux firewalls, etc. based on community-driven CTI:
  * My recommendation: [CrowdSec bouncer](https://www.crowdsec.net/blog/crowdsec-not-your-typical-fail2ban-clone).
* Reset an ID-provider (AD, Entra ID, etc.) account password.
* Disable an AD account (both user and computer, since computer account disabling will block authentication with any AD account on the endpoint, thus preventing from lateral movement or priv escalation).
* Report a (undetected) sample to security vendors, via email. Here are a few addresses, in case of: 
  * Files samples (to be attached in a password-protected Zip file, with 'infected' as password): samples@eset.com, report@sentinelone.com, virus_submission@bitdefender.com, vsamples@f-secure.com, virus@avira.com, submitvirus@fortinet.com, virus_research@avertlabs.com, virus_doctor@trendmicro.com;
  * URL/IP samples: samples@eset.com, report@sentinelone.com, virus_submission@bitdefender.com, phishing-samples@email-samples.withsecure.com, phish@office365.microsoft.com, report@openphish.com, reportphishing@apple.com, abuse@clean-mx.de, datasubmission@mcafee.com. 
* Report a false positive to security vendors, via email;
  * You may want to have a look at [this page](https://github.com/yaronelh/False-Positive-Center) to know the required email address;
  * Report false positive on VT (ML scanner) to CrowdStrike: VTscanner@crowdstrike.com.
* Report a malicious URL (for instance, phishing) to a security vendor for takedown steps
  * My recommendation: [Netcraft](https://www.netcraft.com/cybercrime/) [via API](https://report.netcraft.com/api/v3), or [PhishReport](https://phish.report/docs).
 
 ## Automation example around identity-based detections

 * https://github.com/cyb3rxp/awesome-soc/blob/main/threat_intelligence.md#identity-based-detections
  

# End
Go to [main page](https://github.com/cyb3rxp/awesome-soc/blob/main/README.md).
