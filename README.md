# ReasonateAI MVP

## Overview
ReasonateAI is an AI-powered web application generator.

## Tech Stack
- LangGraph
- FastAPI
- React
- Tailwind CSS
- Docker

## Project Structure
- backend/
- frontend/
- docs/

## Sprint Goal
Build a functional MVP in 7 days.


# Recommended Folder Structure

text
reasonateaimvp/

docs/
README.md

pod1_langgraph/
│
├── graph.py
├── state.py
├── planner.py
├── coder.py
├── reviewer.py
├── prompts/
│     ├── planner.txt
│     ├── coder.txt
│     └── reviewer.txt
│
├── models.py
├── main.py
├── utils.py
└── requirements.txt


# 1. README.md

Write:

* Project overview
* Installation steps
* How to run
* Folder explanation

Example:

md
# ReasonateAI MVP

This project generates websites using AI.

Workflow:

Planner → Coder → Reviewer


# 2. docs/

This folder contains documentation.

Example files:


architecture.md
workflow.md
api.md

Write things like:

* System architecture
* LangGraph flow
* AI workflow


# 3. state.py

This is one of the most important files.

It stores the data shared between nodes.

Example:

python:
from typing import TypedDict

class AgentState(TypedDict):
    user_intent: str
    architecture_plan: str
    raw_code: dict
    validation_status: bool


# 4. planner.py

Planner reads the user's prompt.

Example

Input

Create a portfolio website


Planner Output

python:
{
 "pages":["Home","About","Projects"],
 "theme":"dark",
 "framework":"html"
}


The planner **doesn't generate code**.

It only creates a plan.



# 5. coder.py

Reads Planner output.

Generates

json:

{
 "html":"...",
 "css":"...",
 "javascript":"..."
}


This is where the AI coding model is called.



# 6. reviewer.py

Checks whether the generated code is correct.

Example checks:

✔ JSON valid

✔ HTML exists

✔ CSS exists

✔ JavaScript exists

✔ AI didn't refuse

Returns

python:

True

or

python:

False


# 7. graph.py

Connects everything.

Example flow:

Planner

↓

Coder

↓

Reviewer


LangGraph is configured here.


# 8. prompts/

Instead of writing prompts inside Python files,

create:

planner.txt

coder.txt

reviewer.txt


Example:

planner.txt

You are an expert software architect.

Analyze user intent.

Return architecture plan.


# 9. models.py

Stores LLM configurations.

Example:

python:

planner_model

coder_model

reviewer_model

This keeps model setup separate from business logic.


# 10. utils.py

Utility functions.

Example:

Load prompt

Parse JSON

Read file

Save output

Logging


# 11. main.py

Runs the whole workflow.

Example:

User Prompt

↓

Planner

↓

Coder

↓

Reviewer

↓

Print Result



# 12. requirements.txt

Contains packages.

Example

```
langgraph

langchain

groq

python-dotenv

pydantic


# Overall Flow

    text
User Prompt
      │
      ▼
planner.py
      │
      ▼
state.py
      │
      ▼
coder.py
      │
      ▼
reviewer.py
      │
      ▼
graph.py
      │
      ▼
Generated HTML/CSS/JS
