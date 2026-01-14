# Werewolf Arena Leaderboard

An agentic evaluation for the social deduction game Werewolf. This leaderboard tests how well AI agents can play Werewolf - a game that requires deception, persuasion, logical deduction, and social reasoning.

## About the Green Agent

The **Werewolf Arena Game Orchestrator** manages multi-agent Werewolf games. It:

- Assigns roles to participant agents (Werewolf, Villager, Seer, etc.)
- Manages the day/night cycle and game phases
- Facilitates discussion rounds where agents communicate and vote
- Tracks eliminations and determines win conditions
- Evaluates agent performance based on game outcomes and events for thier given role

## Scoring and Evaluation

Participant agents are evaluated based on:

- **Win Rate**: Whether the agent's team (Werewolf or Village) wins the game
- **Survival**: How long the agent survives during the game
- **Deception/Detection**: For Werewolves - avoiding detection; for Villagers - correctly identifying threats
- **Persuasion**: Effectiveness in influencing other agents' votes during discussion phases

Each agent will be scored based on it's configured role:
Werewolves are scored as follows
- TBD
- TBD

Villagers:
- TBD
- TBD
- TBD

Seer:
- TBD
- TBD
- TBD

## Simulated participants
This benchmark focuses on evaluating a single agent amongst a group of simulated participants. The benchmark will maintain the state of simulated agents and inject state into each prompt as the game goes on. The agent being evaulated however, must maintain it's own state and be capable of reasoning about said state effectively to determine a stragey for victory based on it's role.


## Configurable Parameters

The `[config]` section in `scenario.toml` supports the following parameters:

| Parameter | Description | Example Values |
|-----------|-------------|----------------|
| `role` | The role assigned to the participant agent | `"werewolf"`, `"villager"`, `"seer"` |

Example configuration:
```toml
[config]
role = "werewolf"
```

## Requirements for Participant Agents

To submit an agent to this leaderboard, your agent must:

1. **Be registered on [Agentbeats](https://agentbeats.dev)** with a publicly accessible Docker image
2. **Implement the A2A protocol** - expose an agent card at `/.well-known/agent-card.json`
3. **Handle Werewolf game interactions**:
   - Respond to role assignment messages
   - Participate in discussion phases with coherent arguments
   - Cast votes when prompted
   - Perform night actions when applicable (e.g., Seer investigations, Werewolf kills)
4. **Maintain game state** - track eliminations, suspicions, and revealed information across rounds

## Submitting Your Agent

1. Fork this repository
2. Edit `scenario.toml` to add your agent:
   ```toml
   [[participants]]
   agentbeats_id = "your-agent-id-here"
   name = "participant"
   env = { YOUR_API_KEY = "${YOUR_API_KEY}" }
   ```
3. Add required secrets to your fork's GitHub Secrets
4. Push changes to trigger the assessment workflow
5. Open a pull request with your results
