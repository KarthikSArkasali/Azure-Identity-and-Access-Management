# Azure Identity and Access Management (IAM) Project

This document showcases key concepts and practical implementations of Azure IAM that demonstrate expertise in managing identities, access, ensuring compliance and security in the cloud.

# 1. Role-Based Access Control (RBAC)

RBAC is a critical Azure IAM feature that enables precise management of access to resources. In this project, the following steps were performed to implement RBAC:
   * a. Identified roles for various teams (e.g., Admin, Developer, Read-only).
   * b. Assigned built-in roles like 'Owner', 'Contributor', and 'Reader' to users and groups.
   * c. Created custom roles with JSON templates for specific permissions.

**Outcome:** This ensured the principle of least privilege, reducing security risks.

A **real-time example** of Role-Based Access Control (RBAC) can be seen in cloud platforms like Microsoft Azure. Here's a practical scenario:

* **Scenario: Azure Role-Based Access Control in a Development Team.**
  
* **Context:** An organization uses Azure for hosting and managing applications. The team consists of developers, testers, and IT administrators. Each group needs different levels of access to Azure resources.

**RBAC Implementation:** <br>

  **1. Developer Role:**
     Developers require access to create and modify virtual machines (VMs), databases, and application services. They are assigned the Contributor role for specific resource groups containing these resources.

  **2. Tester Role:**
     Testers need to verify application functionality but don’t require permissions to modify resources. They are assigned the Reader role, allowing them to view resource configurations without making changes.

  **3. IT Administrator Role:**
     IT admins are responsible for maintaining infrastructure and need full control. They are assigned the Owner role, granting them full access to all resources in the Azure subscription.

  **4. Access Control:**
    * The RBAC ensures that a developer cannot delete the entire resource group, as that permission is beyond the Contributor role.
    * A tester cannot accidentally modify or delete a database since their Reader role restricts them to view-only access.
    * IT admins can make system-wide changes, including user management.
    
* **How it Works in Real-Time:**
  * When a developer logs into the Azure portal, they only see resources within their assigned resource group and are limited to performing actions defined by the Contributor role.
  * If a tester tries to access the portal, they can see resource configurations and logs but can’t modify them.
  * IT admins have full access across all subscriptions and resources.

This kind of structured access ensures security, accountability, and least privilege principles, preventing unauthorized changes or data breaches. It is also auditable, allowing organizations to track who accessed or modified resources.

* **Step-By-Step Guide to Setting up Role-Based Access Control (RBAC)** <br>
    RBAC helps you manage who has access to Azure resources, what they can do with them, and what areas they can access.

   * **1. Navigate to the Resource:**
     Go to the Azure Portal and select the resource (e.g., Virtual Machine, Storage Account).
     Click on Access Control (IAM).

   * **2. Assign a Role:****
     Click Add > Add role assignment.
     Select a role (e.g., Reader, Contributor, or a custom role).
     Assign it to a user, group, or service principal.
     Click Save.

   * **3. Create a Custom Role (Optional):**
     In Access Control (IAM), click + Add > Add custom role.
     Define permissions by uploading a JSON template or using the built-in editor.
     Assign the custom role to a user or group.

# 2. Conditional Access Policies

Implemented Conditional Access policies to enforce access controls based on conditions like location, device, and risk level.
 * a. Configured policies to block access from untrusted locations.
 * b. Required multi-factor authentication (MFA) for sensitive resources.
 * c. Enabled session controls to monitor and limit actions.
   
**Outcome:** Enhanced security by ensuring access only from trusted environments.

A **real-time example** of Conditional Access Policies can be seen in the context of managing access to Microsoft 365 or Azure Active Directory applications.

**Scenario: Secure Access for a Remote Workforce.**
**Context:**
    An organization has employees working both in-office and remotely. The IT team needs to secure access to corporate resources (e.g., email, SharePoint, Teams) while allowing flexibility for remote work.

 * **Implementation of Conditional Access Policies:**
   * **1. Policy:** Require MFA for Access Outside the Corporate Network

     * **Rule:** If a user logs in from outside the corporate office network, they must verify their identity using Multi-Factor Authentication (MFA) (e.g., via an authenticator app or SMS).
     * **Real-Time Application:** A remote employee logging in from a personal device at home is prompted for MFA to complete the login.
      
   * **2. Policy:** Block Access from Untrusted Locations

     * **Rule:** If a login attempt comes from a country or region flagged as high-risk (e.g., locations known for cyber-attacks), the access request is denied.
     * **Real-Time Application:** An unauthorized attempt to access an employee’s account from an untrusted country is automatically blocked.

   * **3. Policy:** Allow Access Only on Compliant Devices

     * **Rule:** Users can only access resources from devices that are compliant with corporate policies (e.g., devices with up-to-date antivirus, OS patches, or managed by the organization).
     * **Real-Time Application:** An employee attempting to log in from an outdated or unmanaged device receives a message requiring them to update or enroll the device.

   * **4. Policy:** Limit Access Based on Application

     * **Rule:** Sensitive applications like financial systems are only accessible when logged in from the corporate network.
     * **Real-Time Application:** A user logging into the financial system from a home network is denied access, while the same user accessing Teams or Outlook is allowed with MFA.

**How it Works in Real-Time:**
 * **Employee Logging In:**
   * Sarah, an employee, logs in from home to check emails. The system verifies her credentials, detects the IP address is external, and enforces MFA before granting access.
   * If Sarah tries to access a sensitive internal app, access is denied unless she connects through a secure corporate VPN.
     
**Attack Mitigation:**

 * An attacker tries to access Sarah's account from a flagged IP in a high-risk country. The conditional access policy blocks the attempt, even with valid credentials.
 
 This approach balances **security** and **usability**, ensuring legitimate users can work flexibly while reducing the risk of unauthorized access. Conditional Access Policies are widely used to meet compliance
 requirements like **Zero Trust Architecture** and **data protection mandates**.

* **Step-By-Step Guide to Setting up Conditional Access Policies**<br>
Conditional Access enforces access policies based on conditions like device or location. 

  * **Go to Azure Active Directory:**
      In the Azure Portal, search for and select Azure Active Directory.
      Click on Security > Conditional Access.

  * **Create a Policy:**
      Click + New policy.
      Name the policy (e.g., "Block Access from Untrusted Locations").
      Under Assignments, choose Users and groups to target specific users or groups.
      Under Cloud apps or actions, select the applications to protect.

  * **Configure Conditions:**
      Under Conditions, configure factors like Sign-in Risk, Device Platforms, or Locations.
      For example, block access from all locations except trusted ones.

  * **Set Access Controls:**
      Under Grant, select Block access or require MFA.
      Click Create to save the policy.


# 3. Identity Protection

Azure AD Identity Protection was utilized to detect and respond to identity-based threats.
 * a. Configured risk-based policies to automatically block risky sign-ins.
 * b. Monitored user risk and sign-in risk levels in Azure AD reports.
 * c. Automated password resets for compromised accounts.
  
**Outcome:** Reduced the risk of unauthorized access through proactive threat management.

A **real-time example** of Identity Protection can be seen in systems like **Microsoft Azure Active Directory (Azure AD)**, where advanced identity protection mechanisms secure user accounts against threats such as compromised credentials and suspicious activities.

**Scenario: Protecting a Corporate Employee's Identity.** <br>
**Context:**
  An organization uses Azure AD to manage employee access to cloud services like Microsoft 365, CRM tools, and HR platforms. Identity Protection ensures user accounts remain secure, even in the event of a 
  compromise attempt.

**1. Risk-Based Conditional Access:**
  * **Real-Time Application:**
    * John, an employee, logs in from an unfamiliar location or device. Azure AD detects this as a potential risk (e.g., based on the IP's reputation or location mismatch).
    * The system prompts John to verify his identity using Multi-Factor Authentication (MFA) before granting access. If the risk is deemed high, access may be blocked altogether.
      
**2. Detection of Leaked Credentials:**
  * **Real-Time Application:**
    * If John's credentials appear on a public breach database (monitored by Azure's threat intelligence), the system flags his account as at risk.
    * Identity Protection enforces an immediate password reset and requires additional security steps like MFA.
      
**3. Sign-In Risk Detection:**
  * **Real-Time Application:**
    * Azure detects multiple failed login attempts from a known malicious bot network against John's account, categorizing this as a high-risk sign-in.
    * John's account is temporarily locked, and the IT admin receives a security alert to investigate further.
      
**4. User Risk Monitoring:**
  * **Real-Time Application:**
    * Jane, another employee, uses weak passwords and exhibits unusual login patterns, like frequent logins from multiple countries within a short time.
    * Azure's Identity Protection flags Jane's account with a High User Risk Level, notifying administrators to apply stricter security measures, such as forcing MFA or suspending the account temporarily.
    
**5. Adaptive Access Controls:**
  * **Real-Time Application:**
    * Employees working from safe, recognized environments are given seamless access. However, when unusual or risky behavior is detected (e.g., login attempts from anonymized IPs or new devices), stricter 
      measures like step-up authentication are applied dynamically.
      
**How It Protects in Real-Time:**
  * **John's Login from a New Country:**
    * John tries to log in while traveling. Identity Protection detects this as an unusual activity and checks for other associated risks (e.g., simultaneous logins from different regions). Depending on the 
       risk level, John is prompted for MFA or blocked.
  * **Credential Theft Mitigation:**
    * If attackers use John's stolen credentials, Identity Protection detects the anomalies (e.g., new device, risky IP), and blocks access before any damage occurs.
      
This kind of proactive identity protection is a cornerstone of **Zero Trust Security**, where every login and device is continuously assessed to minimize risk while maintaining user productivity.

* **Step-By-Step Guide to Setting up Identity Protection**
Identity Protection identifies and mitigates identity risks.

   * **Access Identity Protection:**
       In Azure Portal, go to Azure Active Directory > Identity Protection.

   * **Configure Risk Policies:**
       Click User risk policy or Sign-in risk policy.
       Under Assignments, select users or groups.
       Set risk levels (e.g., medium or high).
       Choose an action (e.g., require password change or block access).
       Save the policy.

   * **Monitor Risks:**
       Under Risk detections, review risky users and risky sign-ins.
       Take remediation actions like forcing a password reset.


# 4. Privileged Identity Management (PIM)

Privileged Identity Management was implemented to manage, monitor, and control access to sensitive roles.
 * a. Enabled just-in-time (JIT) access for privileged roles.
 * b. Configured approval workflows for role activation.
 * c. Reviewed access logs to ensure compliance.
   
**Outcome:** Minimized the attack surface by reducing standing permissions.

A **real-time example** of **Privileged Identity Management (PIM)** can be observed in Microsoft Azure Active Directory (Azure AD PIM), where organizations manage and secure access to privileged roles, such as administrators or resource owners, on a just-in-time basis.

**Scenario: Securing Privileged Access in a Cloud Environment**
**Context:**
A medium-sized organization uses Azure for its cloud services. The IT team manages resources such as virtual machines, databases, and app services. To minimize security risks, they implement PIM to manage access to sensitive roles and resources.

**Real-Time Use of PIM:**<br>
**1. Just-In-Time Role Activation:**
  * **Real-Time Application:**
    * Sarah, an IT administrator, needs to modify the configuration of an Azure resource. Instead of having permanent access to the Owner role, she activates the role only when needed.
    * The activation requires Sarah to provide a justification and pass Multi-Factor Authentication (MFA). The elevated access is granted temporarily (e.g., for 1 hour) and automatically revoked after the 
        session ends.

**2. Approval Workflow for Privileged Roles:**
  * **Real-Time Application:**
    * John, a developer, requests access to the Contributor role for deploying new applications. The request is sent to his manager for approval.
    * Once approved, John’s role is activated, and he can proceed with deployment. The access is time-bound and logged for auditing.
     
 **3. Risk Mitigation Through Alerts:**
   * **Real-Time Application:**
     * PIM detects unusual activity, such as repeated role activation attempts outside business hours. The system raises an alert, prompting administrators to investigate the behavior.

 **4. Access Review and Audit:**
   * **Real-Time Application:**
     * The IT security team schedules regular access reviews through PIM. They find that Alex, a former employee, still has a privileged role.
     * With one click, they remove Alex’s access and generate a report for compliance purposes.
    
 **5. Privileged Access for Azure Resources:**
   * **Real-Time Application:**
     * Lisa, a DevOps engineer, needs temporary access to manage an Azure Kubernetes Service (AKS) cluster. PIM allows her to activate the Kubernetes Cluster Admin role with a specific scope (e.g., a single 
       resource group) and revokes access once the task is completed.
      
**How It Works in Real-Time:**
  * **Minimizing Risk of Exploitation:**
    * By granting privileged access only when needed and for a limited time, the risk of a compromised admin account being used for malicious purposes is significantly reduced.
  * **Auditing and Compliance:**
    * Every role activation, including justification, time of activation, and actions taken, is logged. This ensures compliance with standards like ISO 27001, GDPR, or SOX.

PIM ensures **least privilege access**, **time-bound permissions**, and **real-time governance**, making it indispensable for securing sensitive operations in dynamic environments.

* **Step-By-Step Guide to Setting up Privileged Identity Management (PIM)**
PIM manages privileged roles and minimizes standing admin access.

   * **Enable PIM:**
       Go to Azure Active Directory > Privileged Identity Management.
       Click Azure AD roles or Azure resource roles.
       Enable PIM for the desired resource.

   * **Assign Eligible Roles:**
       Select Roles and choose a role (e.g., Global Administrator).
       Assign it as Eligible instead of permanent.

   * **Configure Just-in-Time Access:**
       Click Settings for the role.
       Enable Require approval for role activation.
       Set activation time limits.

   * **Review Access Logs:**
       Under Audit logs, review who activated roles and when.

# 5. Integration with Azure Active Directory

Azure AD integration was utilized for seamless identity management across applications.
 * a. Integrated on-premises Active Directory with Azure AD using Azure AD Connect.
 * b. Enabled single sign-on (SSO) for cloud applications.
 * c. Configured application proxy for secure remote access to on-premises apps.
   
**Outcome:** Streamlined identity management and improved user productivity.

A **real-time example** of integration with **Azure Active Directory (Azure AD)** can be seen in organizations using Azure AD as the central identity provider for managing user authentication across multiple applications and platforms.

**Scenario: Seamless Single Sign-On (SSO) for Enterprise Applications**
**Context:**
A company with 1,000 employees uses multiple applications, such as Microsoft 365, Salesforce, and ServiceNow. Instead of maintaining separate login credentials for each application, the IT team integrates these apps with Azure AD to provide a unified sign-in experience.

**Real-Time Integration in Action:**
  **1.Single Sign-On (SSO):**
    * **Real-Time Application:**
      * An employee, Jane, logs into her workstation using her Azure AD credentials.
      * When Jane opens Salesforce or Microsoft Teams, she is automatically authenticated without needing to enter separate usernames and passwords.
      * This is possible because Azure AD acts as the identity provider for all connected apps, enabling SSO.
      
  **2. Conditional Access Policies:**
    * **Real-Time Application:**
      * When John, a manager, tries to access ServiceNow from an unmanaged personal device, Azure AD enforces a Conditional Access policy requiring him to verify his identity via MFA.
      * If the device doesn't meet security compliance standards, access is denied.
      
  **3. Integration with Third-Party Applications:**
    * **Real-Time Application:**
      * The company integrates GitHub Enterprise with Azure AD for secure developer collaboration. Developers log in using their corporate Azure AD accounts, ensuring consistent access control and governance.
      
  **4. B2C Integration for Customer-Facing Apps:**
    * **Real-Time Application:**
      * A retail company uses Azure AD B2C to enable customers to sign in to its e-commerce platform. Customers can log in using social accounts like Google or Facebook, or they can create accounts managed in 
        Azure AD B2C.
      * This provides a seamless user experience while the backend integrates securely with the company’s Azure AD tenant.
      
  **5. Dynamic Group Membership:**
    * **Real-Time Application:**
      * New hires are automatically added to Azure AD groups based on their job roles. For example, a new developer is added to the "Engineering Team" group, giving them instant access to Azure DevOps and Jira 
      through role-based access.
      
  **6. Azure AD Application Proxy:**
    * **Real-Time Application:**
      * The company has an on-premises HR system accessible only within the corporate network. By integrating it with Azure AD Application Proxy, employees can securely access the HR system from outside the 
        office using their Azure AD credentials.
        
**How It Works in Real-Time:**
  * **Unified Access:** Employees access all connected applications using a single Azure AD identity, eliminating the need for multiple passwords and reducing the risk of breaches.
  * **Enhanced Security:** With features like Conditional Access, MFA, and device compliance checks, access is dynamically managed to ensure security.
  * **Simplified IT Management:** IT admins configure and enforce policies centrally in Azure AD, making it easier to onboard/offboard users and maintain access control.
  
Azure AD’s integration capabilities provide a robust identity and access management foundation, streamlining operations while ensuring security and compliance.

* **Step-By-Step Guide to Setting up Integration with Azure Active Directory**
Integrating Azure AD simplifies identity management and access control.

  * **Set Up Azure AD Connect:**
      Download and install Azure AD Connect on your on-premises server.
      Configure it to sync on-premises identities with Azure AD.

  * **Enable Single Sign-On (SSO):**
      Go to Azure Active Directory > Enterprise applications.
      Select the application you want to enable SSO for.
      Configure SSO by following the application-specific guide.

  * **Configure Application Proxy (Optional):**
      Go to Azure Active Directory > Application proxy.
      Enable the proxy and download the connector.
      Configure the proxy settings for on-premises apps.

  * **Manage Users and Groups:**
      Assign users to applications or groups in Azure Active Directory.
      Set conditional access and MFA policies for these applications.

**Conclusion**
This project demonstrates a comprehensive understanding of Azure IAM concepts and their application in real-world scenarios. The implementation of RBAC, conditional access, identity protection, PIM, and Azure AD integration highlights the ability to design and manage secure, efficient cloud environments.
