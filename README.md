# EC2 Monitoring and Remediation System - ServiceNow Implementation

This project details the creation of a semi-automated incident response system on the ServiceNow platform for Netflix's AWS infrastructure. The system was designed to address a critical business problem where a failing EC2 instance caused service disruptions due to a lack of integration between monitoring and incident response systems. The project was successfully enhanced with AI Agent capabilities to provide an intelligent conversational interface for remediation.

The completed solution now includes both a manual UI and an intelligent AI agent to automatically detect EC2 failures, create incidents, and provide immediate, conversational remediation guidance to the DevOps team, all within ServiceNow.

## System Overview

Last week, a critical AWS EC2 instance failure in the US-East region caused buffering issues for
viewers. The incident went undetected for 45 minutes because our existing monitoring system
lacked integration with ServiceNow. As a result, DevOps engineers had to manually find
remediation procedures, which delayed the response and led to potential subscriber churn.
This project's goal was to build a semi-automated incident response system that automatically
detects EC2 failures, creates incidents, and provides immediate remediation guidance to the
DevOps team, all within ServiceNow. The system integrates our internal AWS monitoring server
with ServiceNow, enabling quick, informed, and centralized incident response.

## Implementation Steps

**1. Core System Setup**

- Custom Tables: An EC2 Instance table to track real-time EC2 status and a Remediation Log table to audit all remediation attempts.

- Secure Integration: Configuration of a Connection & Credential Alias to securely interact with the external AWS Integration Server.

- Automated Workflow: A single Flow Designer workflow that triggers on EC2 failures, creates an incident, and sends a notification to the DevOps team via Slack.

- Manual Remediation Interface: A client-side UI Action (Trigger EC2 Remediation) and a server-side Script Include to allow DevOps engineers to manually restart a failed EC2 instance with one click.

- AI Agent Enhancement: An intelligent conversational AI Agent that can identify EC2 instance IDs from natural language and execute the same proven remediation scripts without manual UI navigation.

- Knowledge Base Integration: A knowledge article containing remediation steps, configured to be discoverable by AI Search.


**2. Automated Incident Response**

- Flow Designer Workflow: The core of the system is a single Flow Designer workflow. This flow
is triggered automatically when the Instance status on an EC2 record changes to "OFF."

- AI-Powered Guidance: The flow uses a custom AI Search action to automatically retrieve
relevant knowledge articles based on the incident. It finds the article "Run the UI Action 'Trigger
EC2 Remediation' on the associated record" which provides immediate, actionable guidance.

- Instant Notifications: The flow sends a Slack notification to the DevOps channel, including the
retrieved knowledge article. This ensures the team is instantly alerted and has the information
they need to resolve the issue without manual searching. 

- Incident Creation: Finally, the flow automatically creates an incident record for the failed EC
instance, centralizing the issue in the IT Service Management system.

## System Architecture Diagram
The diagram.png file shows the seamless flow from EC2 failure detection to automated incident
creation, AI-powered guidance, one-click manual remediation, and AI agent implementation with all actions logged for
auditing.
<img width="1550" height="1203" alt="Diagram" src="https://github.com/user-attachments/assets/cd3f6d94-f4c1-416e-80eb-0b69c368d678" />



## Optimization

- The successful manual remediation system was enhanced with an AI Agent to provide a more efficient, conversational workflow. This enhancement adds an intelligent layer that can identify EC2 instance IDs from natural language input, get human-in-the-loop approval, and execute the same remediation scripts without requiring DevOps engineers to navigate the UI.

- Efficiency: The AI Agent significantly reduces the time it takes to resolve an issue by eliminating the need to manually search for records, copy IDs, and click buttons. A DevOps engineer can now resolve an issue by simply typing a command in a chat interface.

- Human-in-the-Loop: The supervised execution of the AI Agent ensures that a human is always in the loop to approve the remediation action, preventing unintended consequences.

- Conversational Interface: The AI Agent provides a more intuitive way for engineers to interact with the system, especially during peak hours when multiple incidents need to be addressed quickly.

- Script Optimization: The AI Agent's Script Tool was designed to use the same proven RemediationHelper logic, ensuring consistency and reliability across both the manual and AI-driven workflows.

  <img width="870" height="467" alt="Screen Shot 2025-09-18 at 9 18 02 AM" src="https://github.com/user-attachments/assets/7486d568-f0fa-46ab-baa2-d7cbd95f3510" />


## DevOps Usage

For Netflix DevOps engineers, the system provides a choice between two workflows:

- Manual Workflow (for complex cases): For a detailed review, engineers can navigate to the incident record, click on the EC2 record, and use the "Trigger EC2 Remediation" button.

- AI Agent Workflow (for quick resolution): For routine or urgent issues, engineers can interact with the AI Agent by typing a command like "Restart instance i-09ae69f1cb71f622e" or "Help me with incident INC0001234". The agent will handle the rest with human approval.


<img width="1392" height="454" alt="Screen Shot 2025-09-18 at 9 48 32 AM" src="https://github.com/user-attachments/assets/6e7b473f-aafa-42b0-ad5b-c4b156aeadd9" />



