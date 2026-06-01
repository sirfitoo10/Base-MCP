# Base MCP (Minimal Context Protocol)

A lightweight and extensible implementation of a Minimal Context Protocol (MCP) in JavaScript.
Built and maintained by [sirfitoo10](https://github.com/sirfitoo10).

---

## ✨ Features

* Simple context management system
* Dynamic tool registration and execution
* Lightweight and easy to extend
* Built with modern ES Modules

---

## 📁 Project Structure

```
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
```

---

## ⚙️ Installation

```bash
git clone https://github.com/sirfitoo10/base-mcp.git
cd base-mcp
npm install
```

---

## 🚀 Usage

Run the example:

```bash
node examples/basic.js
```

Expected output:

```
Echo: Hello MCP!
Tool response: Hello from tool
```

---

## 🧠 How It Works

### Context Handling

```js
mcp.addContext("user", "Hello MCP!");
```

---

### Tool Registration

```js
mcp.registerTool("echo", echoTool);
```

---

### Tool Execution

Command format:

```
tool:<toolName> <arguments>
```

Example:

```
tool:echo Hello from tool
```

---

## 🔌 Example Tool

```js
export async function echoTool(input) {
  return `Tool response: ${input}`;
}
```

---

## 🛠 Future Improvements

* OpenAI / LLM integration
* Persistent memory (file/database)
* More advanced tools (calculator, API fetch, etc.)
* CLI or web interface

---

## 👨‍💻 Author

**GitHub:** https://github.com/sirfitoo10

---

## 📄 License

MIT License
