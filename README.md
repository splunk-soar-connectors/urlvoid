[comment]: # "Auto-generated SOAR connector documentation"
# URLVoid

Publisher: Splunk Community  
Connector Version: 2\.0\.1  
Product Vendor: URLVoid  
Product Name: URLVoid  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.9\.39220  

This app supports executing investigative and reputation actions on the URLVoid cloud based service

[comment]: # " File: readme.md"
[comment]: # "  Copyright (c) 2016-2021 Splunk Inc."
[comment]: # ""
[comment]: # "  Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
The app uses the tldextract python module, while executing the **domain reputation** action. This
module uses the tld list from publicsuffix.org. The app ships with a tld list, however it will try
to update the list the first time it runs and then try to update it at a regular interval. The
interval is set in the app config.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a URLVoid asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**identifier** |  required  | string | Identifier
**api\_key** |  required  | password | API Key

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity\. This action makes a request to the service to verify the connection  
[domain reputation](#action-domain-reputation) - Queries URLVoid for domain info  

## action: 'test connectivity'
Validate the asset configuration for connectivity\. This action makes a request to the service to verify the connection

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'domain reputation'
Queries URLVoid for domain info

Type: **investigate**  
Read only: **True**

This action accepts URLs also\. It will extract the domain name from the URL before making the action query\. It also tries to strip out the subdomain if any\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**domain** |  required  | Domain to query | string |  `domain`  `url` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.domain | string |  `domain`  `url` 
action\_result\.data\.\*\.response\.details\.alexa\_rank | string | 
action\_result\.data\.\*\.response\.details\.connect\_time | string | 
action\_result\.data\.\*\.response\.details\.domain\_age | string |  `domain` 
action\_result\.data\.\*\.response\.details\.domain\_age\_date | string |  `domain` 
action\_result\.data\.\*\.response\.details\.download\_size | string | 
action\_result\.data\.\*\.response\.details\.google\_page\_rank | string | 
action\_result\.data\.\*\.response\.details\.header\_size | string | 
action\_result\.data\.\*\.response\.details\.host | string | 
action\_result\.data\.\*\.response\.details\.http\_response\_code | string | 
action\_result\.data\.\*\.response\.details\.ip\.addr | string |  `ip` 
action\_result\.data\.\*\.response\.details\.ip\.asn | string | 
action\_result\.data\.\*\.response\.details\.ip\.asname | string | 
action\_result\.data\.\*\.response\.details\.ip\.city\_name | string | 
action\_result\.data\.\*\.response\.details\.ip\.continent\_code | string | 
action\_result\.data\.\*\.response\.details\.ip\.continent\_name | string | 
action\_result\.data\.\*\.response\.details\.ip\.country\_code | string | 
action\_result\.data\.\*\.response\.details\.ip\.country\_name | string | 
action\_result\.data\.\*\.response\.details\.ip\.hostname | string |  `host name` 
action\_result\.data\.\*\.response\.details\.ip\.latitude | string | 
action\_result\.data\.\*\.response\.details\.ip\.longitude | string | 
action\_result\.data\.\*\.response\.details\.ip\.region\_name | string | 
action\_result\.data\.\*\.response\.details\.speed\_download | string | 
action\_result\.data\.\*\.response\.details\.updated | string | 
action\_result\.data\.\*\.response\.details\.updated\_datetime | string | 
action\_result\.data\.\*\.response\.detections\.count | string | 
action\_result\.data\.\*\.response\.detections\.engines\.engine | string | 
action\_result\.data\.\*\.response\.page\_load | string | 
action\_result\.summary\.asn | numeric | 
action\_result\.summary\.city | string | 
action\_result\.summary\.country | string | 
action\_result\.summary\.domain | string |  `domain`  `url` 
action\_result\.summary\.hostname | string |  `host name` 
action\_result\.summary\.ip | string |  `ip` 
action\_result\.summary\.positives | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 