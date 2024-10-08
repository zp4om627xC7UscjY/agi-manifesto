# agi-manifesto

## Introduction

First they invented a car. Then they decided that the only way to use the car was driving backwards and forwards the same single road. The engine of this car is called the transformer model architecture, and the car itself is referred to as a large language model. Marvin Minsky would probably have asked: **But what about road networks?**

In the quest for higher intelligence, we could consider network nodes in a directed graph as a "multiagent" and each of the nodes as an "agent." We could then suppose that this network evolves, somehow, autonomously over "time" and that we may only define the initial configuration; **self-modification has power**.

We then define that each node shall be a single LLM instance with its own configuration: more precisely, that of:

1. **Initial prompt**: The starting prompt for the LLM.
2. **LLM settings**: The specification, means of accessing, and parameters of the model.
3. **Virtual terminal emulator (TE)**: A terminal emulator that takes the input of the LLM.
4. **TE settings**: Installed Linux packages, hardware access, online credentials, etc.

Now, the individual agent has an internal process of:

1. The initial prompt getting run on the LLM.
2. TE commands of the agent causing things.

A multiagent has an internal process of agents doing what they would alone — but also using commands such as:

- `/msg [agent-name] [prompt]` would send a message to the other agent with that name; the other agent would then evaluate that message as a prompt.
- `/allow-msg [agent-name-0] [agent-name-1]` would allow the agent called `[agent-name-0]` to message `[agent-name-1]`.
- `/add-agent [name] [llm-settings] [initial prompt]` would create an agent with these settings.

We provide the information for the agents about every command and rule via a static and automatically generated system prompt based on these.

**I claim that it is possible to build an artificial general intelligence with this.**

![Also the number of agents must get higher, guessing 5000 with 60% certainty, but 95% certainty that higher than in this example](https://github.com/zp4om627xC7UscjY/agi-manifesto/blob/main/sketch-1718047689846.png)

Yet the number of different possible multiagent configurations grows faster than exponentially as the number of agents increases. One could say that even with every second and every computer in the universe, we would still not be able to try all agents with more than a few hundred nodes. Consequently, we need the **Multiagent Systems Explorer** — an accessible submarine for systematic search of more and more intelligent multiagents from the bottoms of this "combinatorial ocean."

![Example 2](https://github.com/zp4om627xC7UscjY/agi-manifesto/blob/main/sketch-1717913477230.png)

![Example 3](https://github.com/zp4om627xC7UscjY/agi-manifesto/blob/main/sketch-1717913492748.png)

---

## Formal description of what I mean

### Multiagent system

The system is best modeled as a directed graph \( G = (V, E) \), where:

- \( V \) is the set of agents (nodes).
- \( E \) is the set of directed edges representing allowed communication between agents.

Each agent \( a \in V \) operates based on its unique configuration and interacts with other agents according to defined communication protocols.

### Single agent

(Every single) an agent \( a \) is defined by the tuple:

\[
a = \left( \text{ID}_a, \text{LLM}_a, \text{Prompt}_a, \text{TE}_a, \text{TESettings}_a, \text{Permissions}_a \right)
\]

- **\(\text{ID}_a\)**: Unique identifier for the agent.
- **\(\text{LLM}_a\)**: The language model instance with specific settings (e.g., params, model, for non-local keys).
- **\(\text{Prompt}_a\)**: The initial prompt provided to the LLM
- **\(\text{TE}_a\)**: Virtual terminal emulator associated with the agent.
- **\(\text{TESettings}_a\)**: Configuration of the terminal emulator (e.g., linux packages, online credientials, robot controls—"the agency").
- **\(\text{Permissions}_a\)**: Permissions specifying which agents can send messages to this agent.

### How it works

#### Activation

An agent \( a \) is **only evaluated when it receives a message or prompt**. The activation process involves:

1. **Message reception**: Agent \( a \) receives a message \( m \) from another agent \( b \).

2. **Evaluation**: The agent processes the message by appending it to its prompt and evaluating it using its LLM:

   \[
   \text{Output}_a = \text{LLM}_a(\text{Prompt}_a + m)
   \]

3. **Action generation**: Based on the LLM's output, the agent generates commands to be executed in its terminal emulator \( \text{TE}_a \).

4. **Command execution**: The commands are executed within \( \text{TE}_a \), potentially modifying the agent's state or environment.

5. **State update**: The agent updates its internal state, including \( \text{Prompt}_a \) and \( \text{TEState}_a \), based on the execution results.

### Internal COMUNICATION

Agents communicate using specific commands, and messages are only delivered if permissions allow:

- **Send message**:
  - **Command**: `/msg [agent-name] [prompt]`
  - **Effect**: Sends a message to the agent named `[agent-name]`. The receiving agent processes it upon receipt.

- **Manage permissions**:
  - **Command**: `/allow-msg [agent-name-0] [agent-name-1]`
  - **Effect**: Grants permission for `[agent-name-0]` to send messages to `[agent-name-1]`.

- **Add agent**:
  - **Command**: `/add-agent [name] [llm-settings] [initial prompt]`
  - **Effect**: Creates a new agent with the specified configurations.

We shall provide the information for the agents about every command and rule via a static and automatically generated system prompt based on these.

### The actual process of evaluation & (multi)agent cognition

#### Agent states

The state of an agent \( a \) at time \( t \) is:

\[
S_a(t) = \left( \text{Prompt}_a(t), \text{TEState}_a(t), \text{Permissions}_a(t) \right)
\]

- **\(\text{Prompt}_a(t)\)**: The current prompt, including the initial prompt and received messages.
- **\(\text{TEState}_a(t)\)**: The state of the terminal emulator.
- **\(\text{Permissions}_a(t)\)**: Current communication permissions.

#### State transition

When an agent \( a \) receives a message \( m \) at time \( t \), its state transitions to:

\[
S_a(t+1) = \delta_a(S_a(t), m)
\]

Where \( \delta_a \) is defined by:

1. **Update prompt**:

   \[
   \text{Prompt}_a(t+1) = \text{Prompt}_a(t) + m
   \]

2. **Evaluate LLM**:

   \[
   \text{Output}_a = \text{LLM}_a(\text{Prompt}_a(t+1))
   \]

3. **Execute commands**: Commands derived from \( \text{Output}_a \) are executed in \( \text{TE}_a \).

4. **Update TE state**:

   \[
   \text{TEState}_a(t+1) = \text{TEState}_a(t) + \text{Effects of executed commands}
   \]

5. **Update permissions**: Adjust \( \text{Permissions}_a(t+1) \) if modified.

#### Communication states

Communication is governed by:

- **Delivery cond**:

  \[
  \text{Deliver}(a_b, a_a, m) =
  \begin{cases}
  \text{Message is delivered to } a_a, & \text{if } a_b \in \text{Permissions}_a \\
  \text{Message is discarded}, & \text{otherwise}
  \end{cases}
  \]

- **Permissions pred**:

  \[
  a_b \in \text{Permissions}_a \implies \text{Permission granted for } a_b \text{ to message } a_a
  \]

### Self-modification and evolution

Agents have the capability to modify themselves and the network through executed commands.

#### Self-modification

Agents can alter:

- **Prompts**: Modify \( \text{Prompt}_a \) by appending or editing content.
- **LLM settings**: Change \( \text{LLM}_a \)'s parameters.
- **Terminal emulator configuration**: Adjust \( \text{TESettings}_a \) by installing packages or changing access credentials.

#### Multiagent network modification

Some agents can:

- **Create other agents**: Create new agents with `/add-agent`.
- **Modify permissions**: Use `/allow-msg` to create new messaging edges.
- **Send messages**: Communicate & "see" agents with `/msg`.

---

This was originally intended to be published in 2021.

All rights reserved (for the time being).
