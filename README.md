# PressCheck AI Backend

Spring Boot backend for **PressCheck AI**, an AI-powered PR pitch generator and quality reviewer.

The backend accepts campaign information, sends it to an AI model using Spring AI, and returns a structured journalist outreach pitch together with quality evaluation results.

## Project Purpose

PressCheck AI is designed to help PR consultants create concise journalist outreach pitches while reducing common AI-generated content problems such as:

* Unsupported claims
* Invented statistics
* Excessive marketing language
* Weak personalization
* Poor journalist relevance
* Missing calls-to-action

The project also demonstrates responsible AI-assisted software development through structured outputs, validation, guardrails, and testing.

## Tech Stack

* Java
* Spring Boot
* Spring AI
* OpenAI API
* Maven
* Jakarta Validation
* REST API

## Current Features

* Generate PR journalist outreach pitches
* Generate three subject-line suggestions
* Generate follow-up messages
* Evaluate generated pitches
* Score:

    * Clarity
    * Personalization
    * Newsworthiness
    * Conciseness
    * Journalist relevance
* Identify strengths and warnings
* Prevent unsupported or invented information through prompt guardrails
* Validate incoming API requests

## Architecture

```text
Client
   |
   v
PitchController
   |
   v
PitchService
   |
   v
Spring AI ChatClient
   |
   v
OpenAI API
   |
   v
Structured Pitch Response
```

## Project Structure

```text
src/main/java/com/thabith/presscheck_ai/
|
├── config/
│   └── AiConfig.java
|
├── controller/
│   └── PitchController.java
|
├── dto/
│   ├── PitchRequest.java
│   ├── PitchResponse.java
│   └── PitchEvaluation.java
|
├── service/
│   └── PitchService.java
|
└── PressCheckAiApplication.java
```

## API

### Generate PR Pitch

```http
POST /api/pitches/generate
```

### Example Request

```json
{
  "companyName": "Nova Finance",
  "companyDescription": "Nova Finance develops AI-powered accounting software for small businesses.",
  "announcement": "The company has launched a new AI bookkeeping assistant.",
  "targetAudience": "Small business owners",
  "journalistName": "Sarah Smith",
  "publication": "TechCrunch",
  "campaignGoal": "Generate media coverage for the new product"
}
```

### Example Response

```json
{
  "angle": "How AI is helping small businesses simplify bookkeeping",
  "subjectLines": [
    "Story idea: AI and small-business bookkeeping",
    "How small businesses are adopting AI accounting tools",
    "New AI bookkeeping assistant launches for SMEs"
  ],
  "pitch": "Hi Sarah, ...",
  "followUp": "Hi Sarah, just following up...",
  "evaluation": {
    "overallScore": 85,
    "clarity": 90,
    "personalization": 82,
    "newsworthiness": 84,
    "conciseness": 88,
    "journalistRelevance": 81,
    "strengths": [
      "Clear story angle",
      "Concise pitch",
      "Strong call-to-action"
    ],
    "warnings": [
      "Journalist personalization could be stronger"
    ]
  }
}
```

## AI Guardrails

The AI is instructed to:

* Use only information provided by the user
* Never invent statistics
* Never invent awards
* Never invent customer numbers
* Never invent quotes
* Avoid unsupported claims
* Avoid exaggerated marketing language
* Keep pitches concise
* Generate exactly three subject-line suggestions
* Flag missing information instead of inventing details

## Environment Configuration

The application requires an OpenAI API key.

Set the following environment variable:

```bash
export OPENAI_API_KEY="your-api-key"
```

The application configuration should reference the environment variable:

```properties
spring.ai.openai.api-key=${OPENAI_API_KEY}
```

Do **not** commit API keys to GitHub.

## Running the Project

Clone the repository:

```bash
git clone git@github.com:Thabith2001/PressCheck-AI.git
```

Navigate into the project:

```bash
cd PressCheck-AI
```

Run the application:

```bash
./mvnw spring-boot:run
```

The backend will run by default on:

```text
http://localhost:8080
```

## Development Approach

The project is intentionally kept small and focused.

The current MVP prioritizes:

1. Clear requirements
2. AI-assisted implementation
3. Structured AI output
4. Validation
5. Guardrails
6. Testing
7. Code review and verification

Features such as authentication, persistence, CRM integration, WhatsApp, SMS, and email sending are intentionally excluded from the initial version.

## Planned Improvements

Future improvements may include:

* Separate pitch generation and evaluation services
* Deterministic quality checks
* Unsupported-claim detection
* Automated evaluation test cases
* Improved error handling
* Retry handling for invalid model responses
* Frontend integration with Next.js
* Campaign history
* HubSpot integration
* Twilio integration

## Security

Sensitive credentials are provided through environment variables.

Files such as `.env` are excluded through `.gitignore`.

Never commit API keys or production credentials to the repository.

## Author

**Mohamed Thabith Shahul Hameed**

Graduate Software Engineer
Java | Spring Boot | Next.js | AI Integration
# PressCheck-AI
# PressCheck-AI
# PressCheck-AI
