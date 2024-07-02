# PMO AI Agents

PMO AI Agents is now powered by the Hierarchical Autonomous Agent Swarm (HAAS), a sophisticated AI governance structure that enables more complex and ethically-aligned project management workflows.

## Features

- **Hierarchical Agent Structure**: Supreme Oversight Board (SOB), Executive Agents, and Sub-Agents.
- **Ethical Governance**: SOB ensures all actions align with established ethical frameworks.
- **Dynamic Agent Creation**: Agents can create and manage sub-agents as needed.
- **Multi-Model Support**: Use various AI models for different agents and tasks.
- **Task Orchestration**: Coordinate complex PMO tasks across multiple agents at different levels.
- **Customizable Roles and Privileges**: Define custom roles with specific privileges for each agent.

## Quick Start

```python
from pmo_ai_agents import PMOCrew, Task

# Initialize PMOCrew with HAAS structure
crew = PMOCrew(sob_model="gpt-4")

# Add Executive Agents
project_manager = crew.add_executive_agent(
    role="Project Manager",
    goal="Ensure project success and stakeholder satisfaction",
    model="gpt-3.5-turbo"
)

risk_analyst = crew.add_executive_agent(
    role="Risk Analyst",
    goal="Identify and mitigate project risks",
    model="claude-2"
)

# Add Sub-Agents
crew.add_sub_agent(
    executive_agent=project_manager,
    role="Schedule Manager",
    goal="Optimize project schedule",
    model="gemini-pro"
)

crew.add_sub_agent(
    executive_agent=risk_analyst,
    role="Compliance Officer",
    goal="Ensure regulatory compliance",
    model="mistral-medium"
)

# Add tasks
crew.add_task(Task("T1", "Make high-level project decision", "SOB"))
crew.add_task(Task("T2", "Develop project strategy", "Project Manager"))
crew.add_task(Task("T3", "Conduct risk assessment", "Risk Analyst"))
crew.add_task(Task("T4", "Optimize project schedule", "Schedule Manager"))
crew.add_task(Task("T5", "Review compliance requirements", "Compliance Officer"))

# Execute the PMO workflow
import asyncio
results = asyncio.run(crew.kickoff())

# Generate and print report
report = crew.generate_report()
print(report)

# Make a high-level decision
decision_context = "The project is facing budget constraints and timeline pressure."
high_level_decision = asyncio.run(crew.make_high_level_decision(decision_context))
print(f"SOB High-Level Decision: {high_level_decision}")
```

## Hierarchical Structure

1. **Supreme Oversight Board (SOB)**: Highest level of authority, responsible for ethical oversight and high-level decisions.
2. **Executive Agents**: Manage specific domains and can create sub-agents.
3. **Sub-Agents**: Specialized agents focused on specific tasks within their parent agent's domain.

## Agent Privileges

- **SOB**: Can create, terminate, and override decisions of any agent.
- **Executive Agents**: Can create and terminate sub-agents within their domain.
- **Sub-Agents**: Have limited privileges, focused on executing specialized tasks.

## Supported AI Models

- GPT models (OpenAI): "gpt-3.5-turbo", "gpt-4o", etc.
- Claude models (Anthropic): "claude-3.5", "claude-instant-3", etc.
- Gemini models (Google): "gemini-pro", etc.
- Grok models: "grok-1", etc.
- Mistral models: "mistral-tiny", "mistral-small", "mistral-medium", etc.
- Phi-3 (via Ollama): "phi-3"

## API Key and Model Setup

To use the different AI models, you need to set up the corresponding API keys. Create a `.env` file in your project root directory based on the provided `.env.sample` file:

1. Copy `.env.sample` to `.env`
2. Fill in your API keys for the models you plan to use

Example:
```
OPENAI_API_KEY=your_openai_api_key_here
ANTHROPIC_API_KEY=your_anthropic_api_key_here
GOOGLE_API_KEY=your_google_api_key_here
GROK_API_KEY=your_grok_api_key_here
MISTRAL_API_KEY=your_mistral_api_key_here
OLLAMA_URL=http://localhost:11434
```

Make sure to keep your `.env` file secure and never commit it to version control.

## Documentation

For full documentation, visit [docs/index.md](docs/index.md).

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for more details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
