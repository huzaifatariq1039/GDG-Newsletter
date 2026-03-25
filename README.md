AI Trends Curator: An Automated Research Agent
I built this n8n-based automation to solve a specific problem for my GDG on Campus IST community: staying updated with the breakneck speed of AI without spending hours scrolling through feeds. This agent acts as a lead researcher, scouting multiple platforms for trending models and news, synthesizing the data, and delivering a curated "Top 10" report directly to community members.

🚀 How It Works
The workflow is designed to be fully hands-off. It triggers automatically every morning, processes high-volume data through a custom JavaScript engine, and uses a Large Language Model (LLM) to make "smart" decisions about what actually matters.

1. Data Sourcing (The Scrapers)
I’ve set up three primary entry points to capture a broad spectrum of AI developments:

Hugging Face: I query their API to pull the top 10 trending models based on community scores. This ensures we see what the open-source community is actually building.

Medium: I scrape the latest articles tagged with "Artificial Intelligence" to capture thought leadership and deep dives.

Google News: An RSS feed tracks "Artificial Intelligence" mentions over the last 24 hours to keep us grounded in industry news.

2. The Processing Engine
Once the data is collected, it goes through a custom JavaScript Code Node. I wrote this to normalize the messy data coming from different sources (RSS vs. JSON API) into a single, clean string. This step is crucial because it prevents the AI model from getting confused by varying data structures and keeps the token usage efficient.

3. AI Analysis (The "Brain")
I use an AI Agent node powered by the Llama-3.1-8b model via Groq. I've engineered the system prompt to force the AI to act as a "Lead AI Researcher." It evaluates the raw text and ranks the top 10 most impactful items based on their potential utility for developers.

The agent is strictly instructed to output a clean JSON array, which allows the final step to remain perfectly formatted every single time.

4. Automated Delivery
The final output is sent via Gmail. I designed a custom HTML template for the email that includes:

Ranked Titles with direct links.

Company/Source attribution.

One-sentence summaries for quick scanning.

Specific Use-Cases so our members know exactly how to apply the tech.

🛠️ Tech Stack
Automation: n8n

LLM: Llama 3.1 8B (via Groq)

Languages: JavaScript & HTML

Data Sources: Hugging Face API, Google News RSS, Medium RSS

📂 Setup & Installation
Import the Workflow: Download the My workflow.json and import it into your n8n instance.

Configure Credentials:

Set up a Groq API account for the LLM.

Connect your Gmail OAuth2 to enable the email delivery.

Adjust the Schedule: The default is set to 9:00 AM. You can change the Schedule Trigger to suit your community's timezone.

Update the Mailing List: Currently, it's set to a specific recipient. You can swap this for a Google Sheet or a database of your community members' emails.

💡 Why I Built This
As the AI Lead at GDG IST, I want to ensure my team and community are always ahead of the curve. This tool removes the "noise" of the internet and provides a high-signal, actionable report that helps us focus on building rather than just searching.

Developed by Huzaifa Tariq – AI Engineer & GDG Lead.
