# PMO AI Agents

PMO AI Agents is a powerful Python library for creating and managing AI-powered Project Management Office (PMO) environments. It leverages the Hierarchical Autonomous Agent Swarm (HAAS) structure and incorporates multiple advanced features for complex project management scenarios.

## Features

- **Multi-Agent System**: Create and manage multiple AI agents, each with specific roles and responsibilities within the PMO.
- **Hierarchical Agent Structure**: Supreme Oversight Board (SOB), Executive Agents, and Sub-Agents.
- **Ethical Governance**: SOB ensures all actions align with established ethical frameworks.
- **Dynamic Agent Creation**: Agents can create and manage sub-agents as needed.
- **Dynamic Model Selection**: Easily switch between different AI models for each agent.
- **Task Orchestration**: Coordinate complex PMO tasks across multiple agents at different levels.
- **Customizable Roles and Privileges**: Define custom roles with specific privileges for each agent.
- **Flexible Workflows**: Design and implement custom workflows for your PMO processes.
- **RAG (Retrieval Augmented Generation) Support**: Enhance agent capabilities with document analysis and information retrieval.
- **Synthetic Data Generation**: Create realistic project management scenarios for testing and development.
- **Needle in a Haystack Testing**: Evaluate agent performance in retrieving specific information from large contexts.
- **Multiple AI Model Support**: Use various AI models including GPT (OpenAI), Claude (Anthropic), Gemini (Google), Grok, Mistral, and Phi-3 (via Ollama).

## Quick Start

```python
from pmo_ai_agents import PMOCrew

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

# Add tasks
crew.add_task({
    "id": "T1",
    "description": "Make high-level project decision",
    "assigned_role": "SOB",
    "use_rag": True
})
crew.add_task({
    "id": "T2",
    "description": "Develop project strategy",
    "assigned_role": "Project Manager"
})
crew.add_task({
    "id": "T3",
    "description": "Conduct risk assessment",
    "assigned_role": "Risk Analyst"
})

# Execute the PMO workflow
import asyncio
results = asyncio.run(crew.kickoff())

# Generate and print report
report = crew.generate_report()
print(report)

# Demonstrate other features
high_level_decision = asyncio.run(crew.make_high_level_decision("Budget constraints and timeline pressure"))
print(f"SOB High-Level Decision: {high_level_decision}")

synthetic_data = asyncio.run(crew.generate_synthetic_data("risk_scenario", 5))
print(f"Synthetic Data: {synthetic_data}")

needle_score = asyncio.run(crew.run_needle_in_haystack_test("Project context...", "Critical milestone"))
print(f"Needle in Haystack Score: {needle_score}")

# Change agent model dynamically
asyncio.run(crew.change_agent_model("Project Manager", "gpt-4"))
```

## Documentation

For full documentation, visit [docs/index.md](docs/index.md).

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for more details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
