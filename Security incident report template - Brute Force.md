# Security incident report

| Indicators that led to discovery of incident | 
| :---- |
| Today, there were multiple reports from customers of their personal computers running slowly after being redirected from yummyrecipesforme.com which was preceded by an unusual prompt to download a file, when logging into the website. Once notified, the website owner attempted to log into the web server, but found their password was changed. | 

| Investigation of incident |
| :---- |
| A sandbox environment was created to safely run a tcpdump to monitor the network traffic. When prompted, the file was downloaded from the yummyrecipesforme.com website, which then redirected the connection to greatrecipesforme.com. After reviewing the logs, it does appear that there is a download request using `HTTP: GET / HTTP/1.1` to download a possible malware. The user connects to yummrecipesforme.com, with the IP 203.0.113.22. <br><br> Once the file is downloaded, the logs show that a new DNS request to greatrecipesforme.com, with the IP 192.0.2.172. Routing the user away from yummyrecipesforme.com. The port number is also changed to 56378. Once at greatrecipesforme.com, another `HTTP: GET / HTTP/1.1` occurs, and a script downloads another malware on the users personal computer. This ticket was escalated to the cybersecurity team for further analysis. |

|Summary of incident and recommendations |
| :---- |
| This review confirms that the website was compromised. An outside actor gained access to the source code, adding a javascript code that prompted users to downloaded the malicious files. The cybersecurity team has confirmed that the web server was impacted by a brute force attack, by a threat actor, who was able to guess the default admin password. No other additional security layers were found to be set up for the admin controls as well. <br><br>Recommendations for future security hardening include: <br>-Requiring a strong password to prevent default password brute force attempts. <br>-Enabling 2FA, two-factor authentications as an extra security layer. <br>-Require frequent password changes and disallowing the reuse of old passwords so past employees may not gain access. <br>-Limit the number of login attempts to prevent future brute force attempts. |
