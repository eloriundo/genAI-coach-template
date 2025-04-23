# genAI-coach-template
A quick draft in langgraph to build a multi-session "guide", which can be adjusted to performe as a coach, trainer, therapist, teacher, etc.
The main idea is to setup a plan that spans over multiple sessions, and then in each new sessions check history, decide what to focus on for this session, conduct the session, and document it. 
I'm keeping it simple and general, so it can be adjusted to specific use cases and integrations.

## Understanding the notebook
* The first sections are all classess, prompts and functions declarations
* Check the 3 long prompts to udnerstand the overall setup of the agent, and the specifics of the onboarding and session phases
* In the classes, check the CoachingPlan class. This should define and document the user journey. The Session class is smaller, to document each specific session
* You can skim through the functions. There is one to summarize the ongoing conversation and delete old messages, a couple to make decisions in each graph. finalize_session is interesting as it documents the finishing session and udpates the overall plan if needed.
* Then come two subgrap. Each has its own orchestrator node, and otherwise use the common functions. If you see the messages in the notebook outputs you can see how I first interacted with the onboarding bot to define my coaching journey, and then interacted with the session bot in my "first session", discussed progress regarding the goals and steps defined in the previous conversation, documented this session, and updated the plan.

## TO DO
 A lot! But to start:
 * Add an ad-hoc companion bot, to have conversations which are not formal sessions
 * Tie these sub-graphs into a super graph that identifies where we are in the journey, the intent of the user, and thus which subgraph to run
 * Create more helper functions and tools, e.g. to update the plan, access parts of memory and past sessions, etc. These can be provided as tools in a more ReAct architecture.
 * Add LLM as a judge to guide iterations in a structured way