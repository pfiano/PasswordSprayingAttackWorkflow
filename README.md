# Password Spraying Attack Workflow
This is a Password Spraying Attack detection workfklow to be imported in Cisco XDR Automate.

This workflow leverages information available in ISE.

# Workflow Description

1) The workflow periodically checks for any abnormal increase in the execution of Policy Sets in ISE over the observation period, which could signal an ongoing Password Spraying Attack.

2) If detected, the workflow verifies the presence of RADIUS FAILURE messages and assesses whether a relevant portion of these failures are attributed to 'WRONG PASSWORD' reasons.

3) If such messages account for more than X% of the total, it further confirms the likelihood of an ongoing attack.

4) Moreover, the workflow examines the usernames associated with failed login attempts to determine if any of them have successfully established active sessions following a 'WRONG PASSWORD' failure, as this could indicate a potential breach.

6) Finally, upon detection of suspicious activity, an email notification is dispatched.
   

# Workflow Characteristics and Prerequisites

- A moving average algorithm is employed to enhance the reliability of hit count increase detection.
- Workflow variables can be adjusted to fine-tune detection parameters.
- Both OpenAPI and ERS APIs on ISE have been leveraged.
- Cisco XDR Automation Remote is necessary to enable the workflow to communicate with ISE within the customer's network, assuming no access to the public internet.
