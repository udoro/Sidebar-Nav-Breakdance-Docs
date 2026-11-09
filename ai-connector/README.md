---
icon: sparkles
---

# AI Connector

The AI Connector lets an AI agent work on your Sidebar Navigation Builder header in Breakdance. You describe what you want in plain English, and the agent changes your sidebar for you.

***

## What you need

* **Breakdance**, with the Sidebar Navigation Builder header template pasted in and set up. See [Installation](../getting-started.md).
* **A Breakdance MCP server on your site.** It gives the agent tools such as `get-post-tree` and `edit-post`.
* An **AI agent that can use MCP tools**, such as [Claude Code](https://docs.claude.com/en/docs/claude-code/overview), [Codex](https://openai.com/codex/) or [Cursor](https://www.cursor.com).

A chat window with no tools won't work.

***

## Set it up

Do both steps, in order.

### Step 1: Connect your agent to your Breakdance site

Follow Breakdance's own guide: [Connect Your AI Agent](https://breakdance.com/documentation/getting-started/connect-your-ai-agent/). In short:

1. In WordPress, go to **Breakdance > Settings > Agents & MCP**. Install or activate **Agent Connector**.
2. Click **Connect**, pick your agent in the wizard, and follow its steps.
3. If your agent can't reach Breakdance, go back to **Breakdance > Settings > Agents & MCP**. Turn on **Enable MCP Access** (allow agents to access this site over MCP), and click **Save Changes**.

Start a new session when you're done, because agents only load MCP servers when a session starts.

To check it worked, ask the agent: "List the Breakdance tools you can use." You should see tools such as `get-post-tree`, `edit-post` and `preview-post`.

### Step 2: Add the skills files

The skills files teach your agent how the sidebar works in Breakdance.

1. Make a folder on your computer for this work, for example `Sidebar Nav`. Open it in your agent and start a session there.
2. Paste this into the chat and send it:

```
Use curl to download these four files into a folder called sidebar-nav-breakdance-skills in this project. Then read sidebar-nav-breakdance-skills/sidebar-nav-breakdance-skills.md and follow it.
https://raw.githubusercontent.com/udoro/Sidebar-Nav-Breakdance-Docs/main/ai-connector/sidebar-nav-breakdance-skills/sidebar-nav-breakdance-skills.md
https://raw.githubusercontent.com/udoro/Sidebar-Nav-Breakdance-Docs/main/ai-connector/sidebar-nav-breakdance-skills/sidebar-nav-breakdance-skills-build.md
https://raw.githubusercontent.com/udoro/Sidebar-Nav-Breakdance-Docs/main/ai-connector/sidebar-nav-breakdance-skills/sidebar-nav-breakdance-skills-reference.md
https://raw.githubusercontent.com/udoro/Sidebar-Nav-Breakdance-Docs/main/ai-connector/sidebar-nav-breakdance-skills/sidebar-test.mjs
```

To update the skills later, paste the same message again.

**Prefer a manual download?** [Download this repository](https://github.com/udoro/Sidebar-Nav-Breakdance-Docs/archive/refs/heads/main.zip), copy the `ai-connector/sidebar-nav-breakdance-skills` folder into your project folder, and tell your agent to read `sidebar-nav-breakdance-skills/sidebar-nav-breakdance-skills.md`.

***

## What you can ask for

**Change the look**

> *"Make the sidebar dark navy with white links, and orange on hover."*

> *"Make the icons smaller and the links closer together."*

**Change behavior**

> *"Let me collapse the sidebar to icons, and expand it on hover."*

> *"Hide the sidebar behind a menu button and push the page aside when it opens."*

> *"Put the sidebar on the right."*

**Add to the menu**

> *"Add a Services panel with links to Design, Build and Support."*

> *"Put a dropdown with our three locations under About."*

**For the best results**

* Attach a screenshot of a sidebar you like.
* Say what should happen on mobile.
* Say if it should collapse, slide in, or stay open.

The agent asks before it changes the structure of your sidebar, and tells you how to put things back.

***

## Your context file

The agent keeps a file called `sidebar-nav-breakdance-user-context.md` next to the skills files. It notes your preferences and what you've built, so the next session starts faster. The agent creates it on your first session and asks before it adds anything. Updating the skills files keeps it.

***

## Tips

* **Start each session by telling your agent to read `sidebar-nav-breakdance-skills/sidebar-nav-breakdance-skills.md`.** Agents don't remember earlier sessions.
* **Check the result on your site.** The agent checks your published pages, but it can't see inside your Breakdance builder.
* **Some changes need you in the builder.** Before the agent's first change, it tests whether your site accepts it. If your site doesn't, the agent gives you the builder steps instead.

***

## Troubleshooting

| Problem | What to do |
| --- | --- |
| The agent says it can't reach your site | Check the connection from step 1, then start a new session. |
| The server shows as connected, but the agent has no Breakdance tools | Start a new session. Agents only load MCP servers when a session starts. |
| The agent can't find your sidebar | Paste the Sidebar Navigation Builder template into a header template first. See [Installation](../getting-started.md). |
| The agent gives you builder steps instead of making a change | Some changes can't be made through the Breakdance MCP server. Do the steps in the builder, then tell the agent you're done. |
| Changes show in the builder but not on your site | Clear your site's cache. |
