<div align="center">

# Arnav Modi

Software Engineer 2 at Adobe · B.S. Computer Science, UC San Diego

[![LinkedIn](https://img.shields.io/badge/LinkedIn-arnav--modi-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/arnav-modi/)
[![Email](https://img.shields.io/badge/Email-amodi%40ucsd.edu-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:amodi@ucsd.edu)

</div>

## Work

**Adobe**, on the team building the AI layer over Workfront.

I built the MCP server that makes Workfront queryable in natural language, now released as an
official Anthropic Claude connector and OpenAI plugin. Most of the problem is retrieval rather
than generation: customers define their own fields and relationships, so the schema is too large
to pass to a model, and the agent has to resolve the relevant entities, fields, and join paths
before a query can be written.

Related work on the same platform: a feature store built on Snowflake, Feast, and Redis that
supplies field-usage signals to the ranking layer, LLM call optimization that reduced P95
latency from 73s to 29s, and the Snowflake, Kafka, and Airflow infrastructure the service reads
from.

## Projects

Built at hackathons and on weekends.

<table>
<tr>
<td width="50%" valign="top">

### [Confide](https://github.com/Arnav710/Confide)

`2nd Place · Build with Gemma: JustBuild (Edge/On-Device track)`

A clinical assistant that runs entirely on-device. Gemma 4 serves both reasoning and vision
through Ollama, faster-whisper handles speech input, Piper handles output, and the patient
record persists in local SQLite. No cloud API is involved, so it operates with the network
disconnected.

The model is scoped to language only: it extracts structured facts from dictation and phrases
responses. Allergy and drug-interaction checks are deterministic lookups against curated
clinical tables in code. Correctness is measured by a three-tier evaluation suite covering
deterministic goldens, extraction accuracy, and LLM-judge groundedness, which surfaced a real
safety defect that was then fixed.

<sub>`Gemma 4` `Ollama` `faster-whisper` `Piper` `FastAPI` `React` `Vite` `SQLite` `Python`</sub>

</td>
<td width="50%" valign="top">

### [Anvil](https://github.com/Its-a-me-Ashwin/Anvil)

`All Things Agentic Hackathon · Collaborative Partner track`

An agent that assists with hardware projects end to end. It composes parametric CAD assemblies
with build123d, renders module-level wiring diagrams, writes firmware into a code-server
workspace shared with the user, and slices and dispatches print jobs to a Bambu printer through
a decoupled local bridge service.

Every capability is declared once in an adapter registry that wires MCP toolsets and native
function tools from the same list, with per-tool error boundaries so a failed call returns to
the model instead of aborting the request. Project state (objective, constraints, inventory,
decisions, skill profile) persists in Firestore and is read back into each turn. Printer-camera
monitoring runs on a local Gemma 3 model so that loop avoids a cloud round-trip.

<sub>`Gemini` `Google ADK` `MCP` `FastAPI` `Firestore` `Cloud Run` `build123d` `React` `TypeScript` `Zustand` `Ollama` `Docker`</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### [Lumineer](https://github.com/Arnav710/Guidely)

`Local-first browser assistant for older adults`

A Chrome extension that helps users navigate unfamiliar websites. On each request it serializes
the page's interactive elements, optionally captures a screenshot, then returns one
plain-language instruction and highlights the element to act on. Additional modes summarize
dense documents such as insurance letters and benefit statements, and periodically scan the
visible page for phishing and scam patterns.

Inference runs against a local Ollama server rather than a cloud API, and a single machine on a
home network can serve every browser on it. Measured throughput was roughly 15 tokens/sec on a
Raspberry Pi 5 for one user, about 3 concurrent users on a GTX 1050 Ti laptop, and 6 devices on
a 2025 MacBook Pro.

<sub>`Gemma 4` `Ollama` `FastAPI` `Pydantic` `Chrome MV3` `Python` `pytest`</sub>

</td>
<td width="50%" valign="top">

### [Dealership Agent](https://github.com/Khushisidanaa/dealership-agent)

`Foxit Track Winner · DeveloperWeek 2026 (1,800+ entrants)`

A car-shopping agent that handles dealer contact. It runs inventory search from stated
preferences, places outbound calls and sends texts through Twilio using Deepgram for speech,
then summarizes and ranks the resulting conversations to shortlist vehicles and book test
drives. Foxit generates the buyer-facing PDF report and parses dealer-supplied documents such
as Carfax records.

The backend is FastAPI with WebSockets and MongoDB through the Beanie ODM, fronted by a React
and TypeScript UI, containerized with Docker Compose and deployed live.

<sub>`FastAPI` `WebSockets` `Twilio` `Deepgram` `GPT-4` `Foxit` `MongoDB` `Beanie ODM` `React` `TypeScript` `Docker`</sub>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### [TrendForge](https://github.com/Arnav710/TrendForge)

`Self-improving go-to-market agent`

An agent that runs a full campaign loop. It scans live signals from web search, Reddit,
YouTube, Hacker News and dev.to, scores each surfaced trend for breakout probability and brand
fit, generates campaign concepts, and routes them through a panel of audience personas and a
brand manager before a human approves or overrides the result.

Outcomes feed back into the system: a tribunal compares each critic's prediction against the
measured result, adjusts that critic's reliability score, and updates a persisted playbook of
brand rules. The strategy-generation call can invoke a search tool mid-reasoning to check live
discussion, and every data source falls back to a deterministic dataset when credentials are
absent.

<sub>`Next.js 16` `TypeScript` `OpenAI` `Redis` `MongoDB` `Reddit API` `YouTube Data API`</sub>

</td>
<td width="50%" valign="top">

### Older work

**[MyNewsWire](https://devpost.com/software/mynewswire-45dlzk)**
`3rd Place and Best Use of MongoDB Atlas · MHacks 15`

Personalized news digests. A React interface collects topic preferences, an Express and MongoDB
API filters results from the Newscatcher API, and a Python script generates HTML newsletters
delivered through Twilio SendGrid.

**[DevJournal](https://github.com/cse110-sp24-group5/cse110-sp24-group5)**

A developer journal in vanilla JavaScript, built leading a team of 10. Offline use is handled
by the ServiceWorkers API as a progressive web app, behind a CI/CD pipeline running linting,
Jest unit tests, Puppeteer end-to-end tests, automated documentation, and Codacy analysis.

<sub>`React` `Node` `Express` `MongoDB` `SendGrid` `Jest` `Puppeteer` `Codacy`</sub>

</td>
</tr>
</table>

## Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

**Data & infrastructure**

![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=flat-square&logo=snowflake&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)
![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)

**AI & backend**

![MCP](https://img.shields.io/badge/Model%20Context%20Protocol-1F1F1F?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)

## Earlier

Researched synthetic data generation at MIT under Dr. Kalyan. Published a
[blog post](https://sdv.dev/blog/synthetic-clones-for-ml/) showing synthetic data costs only
2.5% accuracy on downstream models, and a
[paper](https://sites.google.com/view/researchpaper-datascience/home) showing downsampling can
cut training time by up to 90%.

B.S. Computer Science, UC San Diego, Magna Cum Laude.
