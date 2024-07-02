# PMO AI Agents

PMO AI Agents is a Python library for creating and managing AI-powered Project Management Office (PMO) environments. It provides a flexible framework for building complex, multi-agent systems to handle various PMO tasks and processes.

## Features

- Multi-Agent System: Create and manage multiple AI agents, each with specific roles and responsibilities within the PMO.
- Dynamic Model Selection: Easily switch between different AI models for each agent.
- Task Orchestration: Coordinate complex PMO tasks across multiple agents.
- Customizable Roles: Define custom roles for your PMO, such as Project Manager, Risk Analyst, Resource Manager, etc.
- Flexible Workflows: Design and implement custom workflows for your PMO processes.
- RAG (Retrieval Augmented Generation) Support: Enhance agent capabilities with document analysis and information retrieval.
- Synthetic Data Generation: Create realistic project management scenarios for testing and development.
- Needle in a Haystack Testing: Evaluate agent performance in retrieving specific information from large contexts.
- Multiple AI Model Support: Use various AI models including GPT (OpenAI), Claude (Anthropic), Gemini (Google), Grok, Mistral, and Phi-3 (via Ollama).

## Installation

```bash
pip install pmo-ai-agents
```

## Quick Start

```python
from pmo_ai_agents import PMOCrew, Task

# Initialize PMOCrew with different AI models
crew = PMOCrew(agents=[
    {"role": "Project Manager", "goal": "Ensure project success and stakeholder satisfaction", "model": "gpt-3.5-turbo"},
    {"role": "Risk Analyst", "goal": "Identify and mitigate project risks", "model": "claude-2"},
    {"role": "Project Controller", "goal": "Plan, execute, monitor, and control project schedule", "model": "gemini-pro", "type": "ProjectController"},
    {"role": "Resource Manager", "goal": "Optimize resource allocation", "model": "phi-3"}
])

# Add tasks
crew.add_task(Task("T1", "Conduct initial project risk assessment", "Risk Analyst"))
crew.add_task(Task("T2", "Develop project plan", "Project Manager"))
crew.add_task(Task("T3", "Create project schedule", "Project Controller", task_type="plan_schedule"))
crew.add_task(Task("T4", "Allocate resources for the project", "Resource Manager"))

# Execute the PMO workflow
results = await crew.kickoff()

# Generate and print report
report = crew.generate_report()
print(report)
```

## Dynamic Model Selection

You can easily change the model for an agent or add new agents with different models:

```python
# Add a new agent with a different model
crew.add_agent(
    role="Quality Assurance",
    goal="Ensure project deliverables meet quality standards",
    model="mistral-medium"
)

# Add a task for the new agent
crew.add_task(Task("T5", "Develop quality assurance plan", "Quality Assurance"))

# Execute the updated workflow
results = await crew.kickoff()
```

## Supported AI Models

PMO AI Agents supports the following AI models:

- GPT models (OpenAI): "gpt-3.5-turbo", "gpt-4", etc.
- Claude models (Anthropic): "claude-2", "claude-instant-1", etc.
- Gemini models (Google): "gemini-pro", etc.
- Grok models: "grok-1", etc.
- Mistral models: "mistral-tiny", "mistral-small", "mistral-medium", etc.
- Phi-3 (via Ollama): "phi-3"

Documentation
For full documentation, visit docs/index.md.

Contributing
We welcome contributions! Please see our Contributing Guide for more details.

License
This project is licensed under the MIT License - see the LICENSE file for details.
