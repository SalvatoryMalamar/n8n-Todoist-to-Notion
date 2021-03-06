# n8n-Todoist-to-Notion

A workflow for the automation tool [n8n](https://n8n.io/). Facilitates using Todoist's UI to input data into Notion database pages and/or page blocks.

# The Problem it Solves

On mobile there's an appreciable delay for opening/loading a desired location in Notion before getting to the point of data input. In contrast, Todoist's android widget opens immediately upon click. This workflow allows Todoist to be our input for Notion saving all that time spent waiting. It makes recording fleeting idea and notes into Notion more feasible. 


# How it Works

1. The workflow recieves webhook notifications from Todoist when a new task is added or updated.
2. Based on which Todoist project the task was added to, the task's content and description is then added as a database page or page block by using Notion's integration function.
3. The initial task is deleted from Todoist. 

![Image of the workflow](https://i.imgur.com/J47tLBL.jpeg)


# What's Required.

- A local or hosted n8n installation
- 

# Use Cases and Examples

**Adding a new page to a Notion database filling the title and a property fields**

Todoist (content field) -> Notion Database (title field)
Todoist (description field) -> Notion Database (property field)

*Examples:* See the Idea, question, or Issue node sections in the n8n workflow


**Adding a new block to an existing page underneath another block**

Todoist (content field) -> Notion Page (block text)

*Examples:* See the grocery or shopping node sections in the n8n workflow


**Adding a new page to a Notion database with a title and page content**

Todoist (content field) -> Notion Database (title field)

Todoist (description field) -> Notion Database (page content)


*Example:* See the notes node section in the n8n workflow.


# Configuration

## Credentials

The user is required to setup and configure n8n for both Todoist and Notion credential authentication. Instructions for Todoist credentials can be found [here](https://docs.n8n.io/credentials/todoist/). Notion's credential documentation is found [here](https://docs.n8n.io/credentials/notion/#prerequisites).


## Defining Todoist Project ids

Each **If** block defines the Todoist project id that will trigger the Notion actions that follow the if block.


## Defining Notion database/page/block ids

This is done individually for each Notion block.


# Other Blocks

**Crypto Block**

The crypto block verifies that the webhook request passed to n8n is actually from Todoist's servers. It calculates the HMAC as described in Todoist's API documentation.

**Function2 Block**

A gramatically correct way to convert a string to title case. Authored by [dipole_moment on stackoverflow](https://stackoverflow.com/a/46774740/15066576). Creates a new object with the $json['content'] field formatted in proper case. Important words and acronyms are capitalized. Unimportant words are not. Leaves the original string intact so users can choose if they'd like to use title case or not.
