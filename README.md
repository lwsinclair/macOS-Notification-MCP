[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/devizor-macos-notification-mcp-badge.png)](https://mseep.ai/app/devizor-macos-notification-mcp)

# 🔔 macOS Notification MCP

A Model Context Protocol (MCP) server that enables AI assistants to trigger macOS notifications, sounds, and text-to-speech.

## ✨ Features

- 🔊 **Sound Notifications**: Play system sounds like Submarine, Ping, or Tink
- 💬 **Banner Notifications**: Display visual notifications with customizable title, message, and subtitle
- 🗣️ **Speech Notifications**: Convert text to speech with adjustable voice, rate, and volume
- 🎙️ **Voice Management**: List and select from available system voices
- 🧪 **Testing Tools**: Diagnostic utilities to verify all notification methods

## 🚀 Quick Start with uvx (Recommended)

The fastest way to use this tool is with `uvx`, which runs packages without permanent installation:

```bash
# Install uv if you don't have it
curl -LsSf https://astral.sh/uv/install.sh | sh

# Run the MCP server directly (no installation needed)
uvx macos-notification-mcp
```

## ⚙️ Configure Claude Desktop

Add this to your Claude Desktop configuration (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "macos-notification-mcp": {
      "command": "uvx",
      "args": ["macos-notification-mcp"]
    }
  }
}
```

Then restart Claude Desktop.

## 📦 Alternative Installation Methods

Standard installation:

```bash
pip install macos-notification-mcp
```

Install from source:

```bash
git clone https://github.com/devizor/macos-notification-mcp
cd macos-notification-mcp
pip install .
```

## 🛠️ Available Notification Tools

### 🔊 Sound Notification
```python
sound_notification(sound_name="Submarine")
```
Available sounds: Basso, Blow, Bottle, Frog, Funk, Glass, Hero, Morse, Ping, Pop, Purr, Sosumi, Submarine, Tink

### 💬 Banner Notification
```python
banner_notification(
    title="Task Complete",
    message="Your analysis is ready",
    subtitle=None,  # Optional
    sound=False,    # Optional: Play sound with notification
    sound_name=None # Optional: Specify system sound
)
```

### 🗣️ Speech Notification
```python
speak_notification(
    text="The process has completed",
    voice=None,     # Optional: System voice to use
    rate=150,       # Optional: Words per minute (default: 150)
    volume=1.0      # Optional: Volume level 0.0-1.0
)
```

### 🎙️ Voice Management
```python
list_available_voices()  # Lists all available text-to-speech voices
```

### 🧪 Testing
```python
test_notification_system()  # Tests all notification methods
```

## 🔒 Implementation Details

- ⏱️ **Rate Limiting**: Notifications are processed one at a time with a minimum interval of 0.5 seconds
- 🔄 **Queuing**: Multiple notification requests are handled sequentially
- 🪟 **OS Integration**: Uses native macOS commands (`afplay`, `osascript`, `say`)
- 🔌 **FastMCP**: Built on the FastMCP framework for AI communication

## ⚠️ Troubleshooting

- 🔐 **Permissions**: Ensure notifications are allowed in System Settings → Notifications
- ⏳ **Timing**: Only one notification is processed at a time
- 🌐 **Environment**: If using the command directly (not uvx), you may need to use full paths

## 📄 License

MIT License
