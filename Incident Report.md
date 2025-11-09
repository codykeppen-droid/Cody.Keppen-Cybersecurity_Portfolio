# **Data Leak Worksheet**

## **Incident Summary**

A sales manager shared access to a folder of internal-only documents with their team during a meeting. The folder contained files associated with a new product that has not been publicly announced. It also included customer analytics and promotional materials. After the meeting, the manager did not revoke access to the internal folder, but warned the team to wait for approval before sharing the promotional materials with others.

During a video call with a business partner, a member of the sales team forgot the warning from their manager. The sales representative intended to share a link to the promotional materials so that the business partner could circulate the materials to their customers. However, the sales representative accidentally shared a link to the internal folder instead. Later, the business partner posted the link on their company's social media page assuming that it was the promotional materials.

## **Analysis**

| Control | Least Privilege |
| :---- | :---- |
| **Issue(s)** | The sharing of a folder containing sensitive information to personnel who should not have access to this folder is the root cause of this incident. This issue is related to the concept of **Least Privilege**. As a member of the sales team, who should not have access to the folder, handled the data in an irresponsible manner. The result of these actions caused confusion as a business partner posted the link with the new product, thinking it was promotional material data, leaking new product and customer analytics. Creating a data breach of sensitive company material. |
| **Review** | **NIST SP 800-53: AC-6** addresses the concept of Least Privilege. It gives the concept of only allowing the least amount of accesses necessary for an individual to complete their functions. While also providing controls to implement to mitigate the risks associated with data access. These controls are: <br>-Restrict access to sensitive resources based on user role.<br> -Automatically revoke access to information after a period of time. <br>-Keep activity logs of provisioned user accounts.<br> -Regularly audit user privileges.
| **Recommendation(s)** | It is recommended to restrict access to sensitive resources at the user level. An automatic revoking process if a user is given temporary access. A review of activity logs to easily complete access audits and discover unapproved sharing of accesses. |
| **Justification** | In this instance, restricting access at a user level, even if the data was shared, would still restrict the user as they would not be authorized to access the shared data. The implementation of a temporary access process would allow for temporary access to data that would be removed once the user exits the data, or after a certain amount of time. Regular audits and logs of activity would allow for more unauthorized accesses to be caught. Whether that is through a discovery of personnel accessing data they shouldn’t on the logs through a regular audit or an activity log alert. |

## **Security Plan Snapshot**

The NIST Cybersecurity Framework (CSF) uses a hierarchical, tree-like structure to organize information. From left to right, it describes a broad security function, then becomes more specific as it branches out to a category, subcategory, and individual security controls.

| Function | Category | Subcategory | Reference(s) |
| :---- | :---- | :---- | :---- |
| **Protect** | **PR.DS:** Data security | **PR.DS-5:** Protections against data leaks. | NIST SP 800-53: AC-6 |

In this example, the implemented controls that are used by the manufacturer to protect against data leaks are defined in NIST SP 800-53—a set of guidelines for securing the privacy of information systems.

### **NIST SP 800-53: AC-6**

NIST developed SP 800-53 to provide businesses with a customizable information privacy plan. It's a comprehensive resource that describes a wide range of control categories. Each control provides a few key pieces of information:

* **Control:** A definition of the security control.  
* **Discussion:** A description of how the control should be implemented.  
* **Control enhancements:** A list of suggestions to improve the effectiveness of the control.

| AC-6 | Least Privilege |
| :---- | :---- |
| **Control:** | Only the minimal access and authorization required to complete a task or function should be provided to users. |
| **Discussion:** | "Processes, user accounts, and roles should be enforced as necessary to achieve least privilege. The intention is to prevent a user from operating at privilege levels higher than what is necessary to accomplish business objectives." |
| **Control enhancements:** | \<ul\>\<li\>Restrict access to sensitive resources based on user role.\</li\>\<li\>Automatically revoke access to information after a period of time.\</li\>\<li\>Keep activity logs of provisioned user accounts.\</li\>\<li\>Regularly audit user privileges.\</li\>\</ul\> |

