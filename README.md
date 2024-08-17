First they invented a car. Then they decided that the only way to use the car was driving backwards and forwards the same single road. The engine of this car is called the transformer model architecture, and the car itself is referred to as large language model. Marvin Minsky would probably have asked: But what about road networks?

In the quest for higher intelligence, we could call network nodes in a directed graph as a "multiagent" and each of the nodes an "agent." We could then suppose that this network evolves, somehow, autonomously over "time" and that we may only define the initial configuration; self-modification has power.

We then define that each node shall be a single LLM instance with its own configuration: more precisely, that of (0) initial prompt (1) LLM-settings, EG the specification, means of accessing & parameters of the model (2) virtual terminal emulator that takes the input of the LLM (3) TE-settings (EG installed linux packages, hardware access, online credientials).

Now — the invididual agent has an internal process of: (0) the initial prompt getting run on the LLM (1) TE commands of the agent causing things. A multiagent has an internal process of: agents doing what they would alone — but also using commands such as
- "/msg [agent-name] [prompt]" would send a message to the other agent with that name; the other agent would then evaluate that message as a prompt.
- "/allow-msg [agent-name-0] [agent-name-1]" would allow agent called [agent-name-0] to message [agent-name-1]
- "/add-agent [name] [llm-settings] [initial prompt]" would create an agent with these settings.

We provide the information for the agents about every commands & rule via a static & automatically-generated system prompt based on these.

I claim that it is possible build an artifical general intelligence with this.

![(also the number of agents must get higher, guessing 5000 with 60% certainty, but 95% certainty that higher than in this example)](https://github.com/zp4om627xC7UscjY/agi-manifesto/blob/main/sketch-1718047689846.png)

Yet the amount of different possible different multiagent configurations grows faster than exponentially as the number of agents increases. One could say that even with every second & every computer in the universe, we would still not be able to try all agents with more than few hundred nodes. Consequently, we need the Multiagent Systems Explorer—an accessible submarine for systematic search of more and more intelligent multiagents from the bottoms of this "combinatorial ocean."

![(example2)](https://github.com/zp4om627xC7UscjY/agi-manifesto/blob/main/sketch-1717913477230.png)

![(example3)](https://github.com/zp4om627xC7UscjY/agi-manifesto/blob/main/sketch-1717913492748.png)

---

This was originally scheduled to be published in 2021. My monero address is: 49juVze4wpvCyrS91EabyAHQTL232pUsW2whQtNqzpHobLHwtWyWQswF7qD4xSe2jxPL1Uk1EKzwvZo8W3gnxomsD23NPqu. All copyrights reserved (for the time being).

---

2024-08-15 I am thoroughly convinced that humans will get to the exact same end results, the design—as I depicted here far before them. But they will do sk by making MANY! small steps instead of directly adapting the fact that directed graphs are the best representation for LLM-multiagents, which have capacity to already be essentially AGI.

The problem – your problem – remains lack of ability to use LLMs. First you will make small steps eventually realizing the scheme depicted here. Then you will realize the scale of this problem and hope you had implemented the Multiagent Systems Explorer earlier.

2024-08-17: I have seen lots of talk about invididual "agents" this year. The analogue to that discussion would be buzz about servers without having an internet—surely the components can be fun, but you are missing out if you do not understand the system makes only really sense as an interconnected whole.

Mechanically, chatbots are primitive technology because the work is half for the human. These "agents" often simply act as preconfigured chatbots, at best weakly connected to each other without real underlying systems. Compare to LLM-multiagents, where the human only configures the initial configuration, after which the AI system works autonomously—to a degree determined by the quality of the initial configuration.
