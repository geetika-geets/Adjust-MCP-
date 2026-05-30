# Adjust-MCP-

**Overview**
This project provides MCP tools that allow AI assistants to interact with Adjust services through natural language.
**Current capabilities:**
- Query reporting data
- Retrieve campaign information
- Access attribution insights

Adjust uses "npx mcp-remote" to directly connect to Adjust's hosted MCP 

```serverClaude Desktop  ←→  mcp-remote(tool)  ←→  Adjust's hosted MCP server```

**Requirements:** 
- Claude Desktop APP: https://claude.ai/login

**Steps**
1) Create an Adjust MCP Token and save it for later use using the Link: https://automate.adjust.com/ai-assistant-service/mcp_token
2) Login/Create Account to the Claude desktop APP.
3) Go to Terminal and run the following commands: 
	1) open -e ~/Library/Application\ Support/Claude/claude_desktop_config.json
	2) A Text file will open. Replace ALL Content with 
		  `{
		  `"mcpServers": {
		    `"adjust-copilot": {
		      `"command": "/opt/homebrew/bin/npx",
		      `"args": [
		        `"mcp-remote",
		        `"https://automate.adjust.com/ai-assistant-service/mcp/",
		        `"--header",
		        `"Authorisation: Bearer {Adjust MCP token generated in the First step}"
		      `]`
			`}`
			 `}`
				`}`
		

		3) **Save the File**
		4) **Restart Claude**
			1) pkill -9 -x "Claude" 
			2) open -a Claude
		5) **Verify the Connection**
			1) ps aux | grep npx
			2) If the Output is like below, it means the MCP is now running below:
			   46885 0.0 0.0 441887584 1360 s003 S+ 12:18PM 0:00.01 grep adjust username 46873 0.0 0.2 459524208 37504 ?? S 12:18PM 0:00.48 node /Users/username/.npm/_npx/705d23756ff7dacc/node_modules/.bin/mcp-remote [https://automate.adjust.com/ai-assistant-service/mcp/](https://automate.adjust.com/ai-assistant-service/mcp/) --header Authorization: Bearer xxxx username 46846 0.0 0.3 442778672 42688 ?? S 12:18PM 0:00.39 npm exec mcp-remote [https://automate.adjust.com/ai-assistant-service/mcp/](https://automate.adjust.com/ai-assistant-service/mcp/) --header Authorization: Bearer xxxx username 46845 0.0 0.0 442191712 672 ?? S 0:00.00 /Applications/Claude.app/Contents/Helpers/disclaimer /opt/homebrew/bin/npx mcp-remote [https://automate.adjust.com/ai-assistant-service/mcp/](https://automate.adjust.com/ai-assistant-service/mcp/) --header Authorization: Bearer xxxx
4) **Once the connection is established, Open Claude Desktop App**
	1) Open Claude Desktop → **Settings → Connectors**
	2) Click the **"+"** button
	3) Fill in:
		1) **Name** : adjust-copilot
		2) **URL**`https://automate.adjust.com/ai-assistant-service/mcp/
	4) Click Save
	5) Restart Claude Desktop
	6) Once successfully connected, you can see adjust-copilot connected

5) After the successful connection, open the chat and ask Claude about your Adjust account Performance
			
			
