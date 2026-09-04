# Intuz — Your automation partner, one workflow at a time.

<p align="center">
  <picture>
    <img alt="Banner Image" src="https://github.com/user-attachments/assets/210f97fc-0fce-404a-b647-7dfe1302cd37" />
  </picture>
</p>

# Automate cold outreach with email personalization using Gemini and Google Sheets

Intuz helps organizations orchestrate AI, automation, and enterprise systems through scalable workflows. Our repository showcases proven implementations across healthcare, operations, customer support, document processing, sales, and back-office functions, enabling teams to accelerate automation initiatives without starting from scratch.

[N8N Creator](https://n8n.io/creators/intuz/) · [AI Consulting](https://www.intuz.com/ai-transformation-services/) · [AI Workflow Automation](https://www.intuz.com/workflow-automation-services/) · [For Custom Workflow Automation](https://www.intuz.com/get-started/)

---

This n8n template from [Intuz](https://www.intuz.com/) provides a complete and automated solution for powerful cold outreach campaigns.

It connects a Google Sheet of prospect data with Google Gemini to automatically generate highly personalized emails. By analyzing specific keywords and data points like company name, industry, or job title from your sheet, this automated workflow crafts unique, relevant messages that feel one-to-one, creating a complete system to dramatically improve your engagement and response rates.

## How It Works

Manually writing personalized emails for a long list of leads is a significant bottleneck. This workflow eliminates that friction by creating an automated system that reads your lead list, understands the context, and writes compelling drafts for you.

- **Scheduled Lead Processing:** On a schedule you define (e.g., daily), the workflow automatically activates to process your lead list.
- **Fetches Your Lead List:** It connects to your designated Google Sheet and reads all the lead data you’ve prepared, such as names, companies, roles, and any custom notes or pain points.
- **Intelligent Filtering:** The workflow is smart enough to know which leads have already been processed. Using an **If** node, it filters out any rows that already contain a generated email, ensuring it only works on new, untouched leads.
- **AI-Driven Personalization (Google Gemini):** This is the core of the engine. For each new lead, it sends the relevant data to the Google Gemini Chat Model. The AI follows a custom prompt you define to draft a completely unique email, including a compelling subject line and a personalized body.
- **Structured Data Output:** The workflow uses a Structured Output Parser to ensure the AI’s response is always in a clean, predictable JSON format (e.g., `{"subject": "...", "body": "..."}`), making the data easy to handle in the next steps.
- **Seamlessly Updates Your Spreadsheet:** Finally, the generated subject line and email body are written back into the correct row for that lead in your Google Sheet, ready for your team to copy, paste, and send.

## How to Use: Quick Start Guide

### 1. Import Workflow Template

- Download the template’s JSON file and import it into your n8n instance via **File > Import from JSON**.

### 2. Configure Credentials

- **Google Gemini:** Create and apply your API key credentials to the **Google Gemini Chat Model** node.
- **Google Sheets:** Set up and apply OAuth credentials for the Google account that owns your lead spreadsheet. Apply this credential to both the **Read Leads from Sheet** and **Update Sheet with Email** nodes.

### 3. Customize Nodes & Spreadsheet

- **Prepare Your Google Sheet:** Ensure your sheet has columns for lead data (e.g., `FirstName`, `Company`, `Role`) and empty columns to receive the output (e.g., `GeneratedSubject`, `GeneratedEmail`).
- **Read Leads from Sheet:** Double-click this node and select your spreadsheet and sheet name from the list.
- **If Node:** Update the condition to check your specific output column. For example, if your output column is named `GeneratedEmail`, the condition should check if `{{$json.GeneratedEmail}}` is empty.
- **Basic LLM Chain Node:** This is the most important step:
  1. Edit the template prompt to match your product, service, and desired tone.
  2. In the Template Variables section, make sure the values (e.g., `{{ $('Read Leads from Sheet').item.json.FirstName }}`) match the exact column names from your Google Sheet.
- **Update Sheet with Email Node:** Select your spreadsheet and sheet name. Set the Lookup Column to a unique identifier for each lead, such as their Email address. Then, map the output from the **Prepare Data for Sheet** node to the correct destination columns in your sheet.

### 4. Test & Activate

- **Test Run:** Click **Execute Workflow** to perform a test run. Check your Google Sheet to see if the first unprocessed lead was updated correctly with a new subject and body.
- **Activate:** Once satisfied, toggle the workflow **Active** switch to enable it to run on your defined schedule.

## Requirements

To use this workflow template, you will need:

1. **n8n Instance:** A running n8n instance (cloud or self-hosted).
2. **Google Gemini Account:** For generating the email content (requires a Google Gemini API Key from Google AI Studio).
3. **Google Sheets Account:** With a prepared spreadsheet containing your lead list and columns for the generated output.

## Connect with us

- **Website:** https://www.intuz.com/n8n-workflow-automation-templates/
- **Email:** [getstarted@intuz.com](mailto:getstarted@intuz.com)
- **LinkedIn:** https://www.linkedin.com/company/intuz/
- **Get Started:** https://n8n.partnerlinks.io/intuz
- **For Custom Workflow Automation:** https://www.intuz.com/get-started/
