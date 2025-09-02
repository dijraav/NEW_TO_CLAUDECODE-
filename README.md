# NEW_TO_CLAUDECODE-
This is a new to CLAUDE CODE, everything required for you to set up and start building your dream app.


# START HERE
> This is a documentation of how I started with Claude Code, so you run less into obstacle and problems along the way.

### If you are using other LLMS, consider adding an LLMs Overlay like Grok, Claude, ChatGPT <br>
You can simply do this by following the just by runnning these in your terminal<br>
**GEMINI** - https://github.com/jzelenkov/macos-gemini-overlay<br>
**GROK** - https://github.com/tchlux/macos-grok-overlay


## INSTALLATION OF CLAUDE CODE

**For MACOS**
```
npm install -g @anthropic-ai/claude-code
cd your-awesome-project
claude
```
**For WINDOWS**<br>
Please refer to the [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code/setup#windows-setup). They provide better illustration as it might not be as straightforward than MacOS

---

## Optimizing your Setups

| Command              | Description                            |
|----------------------|----------------------------------------|
| `/allowed-tools`     | Customize tool permissions             |
| `/terminal-setup`    | Enable shift+enter to insert newlines  |
| `/install-github-app`| Tag @claude on your issues & PRs       |
| `/theme`             | Enable light/dark mode                 |
| `/config`            | Turn on notifications                  |
| 🌐 Turn on MacOS dictation |                                   |

---

# For starter
> If you have existing code base, you Please utilize the codebase


## Use Claude Code to answer questions about your codebase

**Example prompts:**
```
> How is `@RoutingController.py` used?  
> How do I make a new `@app/services/ValidationTemplateFactory`?  
> Why does `recoverFromException` take so many arguments? Look through git history to answer  
> Why did we fix issue `#18363` by adding the if/else in `@src/login.ts` API?  
> In which version did we release the new `@api/ext/PreHooks.php` API?  
> Look at PR `#9383`, then carefully verify which app versions were impacted  
> What did I ship last week?
```

## Steer Claude to use tools your way

**Example prompts:**
```
> Propose a few fixes for issue `#8732`, then implement the one I pick  
> Identify edge cases that are not covered in `@app/tests/signupTest.ts`, then update the tests to cover these. think hard  
> commit, push, pr  
> Use 3 parallel agents to brainstorm ideas for how to clean up `@services/aggregator/feed_service.cpp`
```
## Plug in your team’s tools

**Tell Claude about your bash tools**

> Use the barley CLI to check for error logs in the last training run. Use `-h` to check how to use it.

**Tell Claude about your MCP tools**

```$ claude mcp add barley_server --node myserver```

## Common workflows
| Workflow                               | Example                                                                 | 
|----------------------------------------|-------------------------------------------------------------------------|
| Explore › plan › confirm › code › commit | > Figure out the root cause for issue `#983`, then propose a few fixes. Let me choose an approach before you code. ultrathink |
| Write tests › commit › code › iterate › commit | > Write tests for `@utils/markdown.ts` to make sure links render properly (note the tests won’t pass yet, since links aren’t yet implemented). Then commit. Then update the code to make the tests pass. |
| Write code › screenshot result › iterate | > Implement `[mock.png]`. Then screenshot it with Puppeteer and iterate till it looks like the mock. |

## More context = better performance

**Claude does better with more context**

**There are a number of ways to give Claude more context:**
- `CLAUDE.md`
- Slash commands
- At-mentioning filenames
- (coming soon: MCP resources)

---

## Give Claude more context

Auto-add common bash commands, files, and style conventions to every session:

| Location                          | Usage                        |
|-----------------------------------|------------------------------|
| `/<enterprise root>/CLAUDE.md`    | Shared across all projects   |
| `~/.claude/CLAUDE.md`             | Shared across all projects   |
| `project-root/CLAUDE.md`          | Checked in                   |
| `project-root/CLAUDE.local.md`    | Not checked in               |

*(Shortcut: type `#`)*

**Pull in context on demand:**

| Location                               | Command to use              |
|----------------------------------------|-----------------------------|
| `~/.claude/commands/foo.md`            | Type `/user:foo`            |
| `project-root/.claude/commands/foo.md` | Type `/project:foo`         |
| `project-root/a/`                      | Type `@a`                   |
| `project-root/a/commands/foo.md`       | Type `/project:a:foo`       |
| `project-root/a/CLAUDE.md`             | Pulled in on demand         |
| `project-root/a/foo.py`                | Type `@a/foo.py`            |

---

## Work With Your Teams

Refer to this part of video on how to Work With Your Team: https://youtu.be/6eBSHbLKuN0?t=944

---

## Interlude: Keybindings

**Key combos for common tasks:**

| # | Keybinding / Command                           | Action                                      |
|---|-----------------------------------------------|---------------------------------------------|
| 1 | `Shift+Tab`                                   | Auto-accept edits                           |
| 2 | `#`                                           | Create a memory                             |
| 3 | `!`                                           | Enter bash mode                             |
| 4 | `@`                                           | Add a file/folder to context                |
| 5 | `Esc`                                         | Cancel                                      |
| 6 | `Double-Esc`                                  | Jump back in history, `--resume` to resume  |
| 7 | `Ctrl+R`                                      | Verbose output                              |
| 8 | `/vibe`                                       | Trigger vibe mode                           |

---

## Claude Code SDK

- Use the SDK for programmatic, low-level access to Claude Code  
- Useful for CI and non-interactive contexts, automation, and as a building block for interactive apps  
- Currently supports CLI (TypeScript & Python SDKs coming soon)  

### Example CLI usage
```bash
$ claude -p \
  "what did i do this week?" \
  --allowedTools Bash(git log:*) \
  --output-format json
```
#### Architecture

```
Your agentic application
↓
Claude Code SDK
↓
Anthropic, Bedrock, or Vertex API
↓
Claude models
```

#### Use the SDK as a Unix utility: pipe in, pipe out
```
$ git status | \
  claude -p "what are my changes?" \
  --output-format=json | \
  jq '.result'
```
"Your changes are: ..."

---

## Interlude: Multi-claude

There are many ways to run more Claudes in parallel:

1. Use multiple checkouts in separate terminal tabs  
2. Use one checkout with git worktrees  
3. SSH + TMUX  
4. GitHub Actions, launch jobs in parallel  





# References:
1. [Mastering Claude Code in 30 minutes](https://www.youtube.com/watch?v=6eBSHbLKuN0)




