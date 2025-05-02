
# AI Agent demonstration

Highlight this experimentation is done off-Vodafone (using my private logins to all the services, on my home PC, using no Vodafone data)

## Agent with Wikipedia and Calculator tool

I'm using a tool called n8n to demonstrate AI Agents. I don't recommned to use n8n for anything real - This toos is a UI on LangChain/LangGraph and I would recommend using LangChain/LangGraph directly or if you want a graphical UI based development environment, use LangFlow. Alternatively, if you want a Google centric approach use their Agent Development Kit, or for Microsoft use Autogen or for simpler agents for knowledge workers use Copilot Studio. There is even a very simple agent builder built into the Copilot that we all have access to.

### Memory

Show no-memory -> memory

```
Hi, my name is Lester
```

Note how many tokens were required - shoud be **33** Prompt 22, Completion: 11

```
What is my name?
```

**50** Tokens Prompt 21, Completion: 29
It should answer something like `I'm sorry, but I don't have access to personal information about you unless you've shared it in this conversation. How can I assist you today?`


**Reset the converstion and turn on Memory**

```
Hi, my name is Lester
```

Note how many tokens were required - shoud still be **33** Prompt 22, Completion: 11

```
What is my name?
```

Should get an answer like `Your name is Lester. How can I help you today?`
Note, there are now more input tokens, as it has passed the message history into the model - **58** tokens: Prompt 45, Completion: 13


## Using tools

Calculation without and with tool 

```
What is 9x9?
```

Should get a correct - but understand this was a guess (in the same way as we don't have to work out answers to simple multiplications)

```
What is 14875x79876?
```

The correct answer shold be 1,188,155,500. It will probably guess wrong



**Add calculator and retry**

```
What is 14875x79876?
```

It should give the correct answer of 1,188,155,500.

Show the message being passed to the Calculator.



Show calculation with words

```
What is two dozen times seven-hundred and fifty-five?
```


**Show Wikipedia as tool**

Example where it will use the tool twice

```
Compare serverless technologies Knative and AWS Lambda. Show the output as a table.
```

Show that it used the tool twice (and it didn't use the calculator tool as it was not relevant).
Compare it to a RAG approach where it would do a similarity lookup in a Vector database. The lookup would include the 'Show output as a table'. This agentic approach is muich more effective - it is using the LLM to determine what tools to query and to construct the payload of the query.

**How does this work**

Go back to the previous query. (disconnect the memory)

```
Hi, my name is Lester
```

When I didn't have any tools attached, the query used  22 tokens for the Prompt. Now with the tools attached, it is taking 114 tokens for the Prompt.
It is adding a description of the tools towards the LLM. The LLM in its next word prediction can choose to predict some special tokens to say it wants you to call the tool. It also generates the payload to use to call.


## Agents in Claude Desktop

Repeat that this is my home computer and Claude is not a Vodafone approved tool and you should not send any Vodafone data to Claude.

```
What is TM Forum ODA?
```

```
Get information on all the TM Forum Open-APIs for Service Management. Show the output in a table with a description and example use-cases.
```

## How does this work? What is MCP?

Show https://github.vodafone.com/Innovation-Network/MCP-AIVA/blob/main/aiva_mcp_server.py


## Agent mode in Visual Studio Code

```
Generate server stub implementations for all of the APIs required to integrate partners into a Wholesale Broadband platform using the TM Forum Open-APIs.
```



**Make AI work visible** :

Not just a Chatbot. What about a Kanban to make AI Work visible?


https://lester-thomas.atlassian.net/jira/software/projects/BTS/boards/1


Demonstrate that AI is not just a Chatbot.
Show AI working on TechRadar papers independently, but with Human oversight

Ensure the n8n script is running

Empty kanban

Put simple card into backlog with
```
Create a Tech Radar blip for Edge Computing
```


It should automatically trigger the creation of new cards.

Review one card.



Review cards and add a comment for 
```
Consider Sovereign Cloud approaches
```

Look again at a couple of cards - move them all to the Reviewed tab.

Refresh to see the Main card in Review (it may take a while afterwards for the actual Tech Radar to appear)



Show the agent workflow