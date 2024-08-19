![Images](images.jpeg)

## Issue Summary

On August 15th, 2024, our company experienced a significant outage affecting our primary web application, which serves as a critical tool
for our clients' daily operations. The outage began at 2:30 PM UTC and lasted until 6:00 PM UTC, impacting approximately 60% of our active 
users. Users reported slow load times, frequent timeouts, and inability to access certain features, leading to a disruption in their
workflow and productivity. The root cause was traced back to a misconfiguration in our load balancer settings following a routine 
maintenance update.

### Timeline

August 15th, 2024, 2:32 PM UTC - The issue was first detected through an automated monitoring alert indicating increased latency 
across our web application.  

August 15th, 2024, 2:45 PM UTC - Initial investigation focused on the application layer, suspecting a potential bottleneck in the 
database queries due to recent schema changes.

August 15th, 2024, 3:15 PM UTC - Misleading path: Investigation shifted towards network congestion, considering the spike in traffic 
during peak hours.

August 15th, 2024, 3:30 PM UTC - Incident escalated to the infrastructure team upon realizing the scope of the issue extended beyond application-level concerns.

August 15th, 2024, 4:00 PM UTC - Further investigation revealed the misconfiguration in the load balancer settings, specifically related to session persistence and health check intervals.

August 15th, 2024, 5:45 PM UTC - The issue was resolved by reverting the load balancer configuration to its previous state and adjusting the health check intervals to better suit our application's needs.

August 15th, 2024, 6:00 PM UTC - Full functionality restored, and a post-outage review initiated to prevent future occurrences.

### Root Cause and Resolution

The root cause of the outage was identified as a misconfiguration in the load balancer settings. Specifically, the health check intervals were set too aggressively, causing healthy instances to be marked as unhealthy and removed from the pool. Additionally, the session persistence mechanism was improperly configured, leading to inconsistent routing of user sessions. This combination resulted in increased latency and service disruptions for our users.

To resolve the issue, the infrastructure team reverted the load balancer configuration to its last known good state. They then adjusted the health check intervals to a more conservative setting and corrected the session persistence settings to ensure consistent user experience across sessions.

### Corrective and Preventative Measures

To prevent similar issues in the future, we will implement the following measures:

Conduct thorough testing of any changes to infrastructure components, including load balancers, before deploying them to production environments.
Implement more granular monitoring and alerting for load balancer metrics, such as health check failures and session persistence errors.
Establish a formal change management process that includes peer reviews and approvals for infrastructure changes.
Schedule regular training sessions for the engineering team on best practices for configuring and managing load balancers and other critical infrastructure components.
Develop and maintain comprehensive documentation on our infrastructure setup, including configurations and operational procedures, to facilitate quicker resolution of future incidents.
This incident highlighted the importance of meticulous planning and testing when making changes to our infrastructure. By implementing these corrective and preventative measures, we aim to enhance our system's resilience and minimize the impact of future outages on our users.
