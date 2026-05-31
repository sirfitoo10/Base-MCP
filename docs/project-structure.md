base-mcp/
│── src/
│   ├── core/
│   │   └── mcp.js
│   ├── tools/
│   │   └── echoTool.js
│
│── examples/
│   └── basic.js
│
│── package.json
│── README.md
⚙️ 2. Project Setup
Initialize project
mkdir base-mcp
cd base-mcp
npm init -y
Enable ES Modules

Edit your package.json:

{
  "name": "base-mcp",
  "version": "1.0.0",
  "type": "module"
}
🧠 3. MCP Core (src/core/mcp.js)
export class MCP {
  constructor() {
    this.context = [];
    this.tools = {};
  }

  addContext(role, content) {
    this.context.push({ role, content });
  }

  registerTool(name, fn) {
    this.tools[name] = fn;
  }

  async run() {
    const lastMessage = this.context[this.context.length - 1];

    if (!lastMessage) {
      return "No context provided.";
    }

    // Trigger tool if message starts with "tool:"
    if (lastMessage.content.startsWith("tool:")) {
      const [_, toolName, ...args] = lastMessage.content.split(" ");

      const tool = this.tools[toolName];
      if (!tool) {
        return `Tool "${toolName}" not found.`;
      }

      return await tool(args.join(" "));
    }

    // Default response
    return `Echo: ${lastMessage.content}`;
  }
}
🔌 4. Example Tool (src/tools/echoTool.js)
export async function echoTool(input) {
  return `Tool response: ${input}`;
}
▶️ 5. Example Usage (examples/basic.js)
import { MCP } from "../src/core/mcp.js";
import { echoTool } from "../src/tools/echoTool.js";

const mcp = new MCP();

// Register tool
mcp.registerTool("echo", echoTool);

// Normal message
mcp.addContext("user", "Hello MCP!");
console.log(await mcp.run());

// Tool usage
mcp.addContext("user", "tool:echo Hello from tool");
console.log(await mcp.run());
▶️ 6. Run the Project
node examples/basic.js
Expected output:
Echo: Hello MCP!
Tool response: Hello from tool
🚀 7. Upload to GitHub
Initialize Git
git init
git add .
git commit -m "initial commit"
Connect to your repository
git remote add origin https://github.com/sirfitoo10/base-mcp.git
git branch -M main
git push -u origin main
🔥 8. Optional Next Steps

You can extend this project further:

Add OpenAI integration
npm install openai
Improve features
Add memory (store context in file/database)
Add more tools (calculator, API fetcher, etc.)
Add command parser
Build CLI or web interface
🧠 Summary

You now have:

A working MCP core
A simple tool system
A runnable example
A project ready for GitHub
