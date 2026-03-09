# 3CX VoIP System - Agent Skill

[![GitHub Stars](https://img.shields.io/github/stars/btafoya/3cx-voip-system?style=social)](https://github.com/btafoya/3cx-voip-system/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/btafoya/3cx-voip-system?style=social)](https://github.com/btafoya/3cx-voip-system/network/members)
[![GitHub Issues](https://img.shields.io/github/issues/btafoya/3cx-voip-system)](https://github.com/btafoya/3cx-voip-system/issues)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Format-green)](https://agentskills.io/what-are-skills)

> An AI agent skill for 3CX IP PBX administration and configuration. Extends AI agents with specialized knowledge for managing VoIP telephony systems.

---

## What is an Agent Skill?

Agent Skills are a lightweight, open format for extending AI agent capabilities with specialized knowledge and workflows. This repository provides a **3CX VoIP skill** that enables AI assistants to help with 3CX IP PBX administration tasks.

Learn more about agent skills at [agentskills.io](https://agentskills.io/what-are-skills).

---

## Overview

This repository provides a comprehensive agent skill for [3CX VoIP system](https://www.3cx.com/) administration. The skill includes:

- **`SKILL.md`** – Core instructions for AI agents on 3CX configuration and troubleshooting
- **Bulk import templates** – CSV templates for adding users, extensions, and configuration in bulk
- **Reference materials** – Organized documentation for common VoIP telephony tasks
- **3CX documentation** – Official 3CX HTML documentation for reference

## Skill Structure

The skill follows the Agent Skills format with progressive disclosure for efficient context management:

```
.claude/plugins/3cx-voip-system/
├── SKILL.md              # Core skill file with instructions and metadata
└── (referenced files)    # Templates, documentation, and resources
```

### SKILL.md Format

The skill file contains:

- **Frontmatter** – YAML metadata (`name`, `description`)
- **Instructions** – Step-by-step guidance for AI agents
- **Task Coverage** – When and how to use the skill
- **Reference Links** – Links to additional resources and files

### How Agents Use This Skill

1. **Discovery** – Agents load the skill name and description at startup
2. **Activation** – When a 3CX-related task is mentioned, the full skill instructions are loaded
3. **Execution** – The agent follows the instructions, loading referenced files as needed

### What is 3CX?

**3CX** is a software-based IP PBX that handles:
- Voice over IP (VoIP) calls
- Call routing and queuing
- Interactive Voice Response (IVR) systems
- Multichannel communication (Phone, Live Chat, WhatsApp, SMS, Facebook Messenger)
- Web Client interface for browser-based unified communications
- Video conferencing and collaboration

---

## Installation

### Using with Claude Code

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/btafoya/3cx-voip-system.git
   ```

2. Copy the skill directory to your Claude Code plugins:
   ```bash
   cp -r 3cx-voip-system/.claude/plugins/3cx-voip-system ~/.claude/plugins/
   ```

3. Restart Claude Code. The skill will be automatically loaded when relevant tasks are mentioned.

### Using with Other Agent Frameworks

The skill follows the [Agent Skills specification](https://agentskills.io/specification). To use with compatible agents:

- Copy the `SKILL.md` file and any referenced assets
- Follow your agent's skill loading procedure
- The skill will be activated when tasks related to 3CX, VoIP, or telephony are mentioned

---

## Quick Start

### How the Skill Works

When you ask about 3CX-related tasks, the AI agent automatically activates this skill and loads the relevant instructions. Examples:

- "Help me add a new user extension"
- "Set up a call queue for sales"
- "Configure an IVR menu"
- "Import users from a CSV file"
- "Troubleshoot call quality issues"

### Common Tasks

| Task | Documentation |
|------|---------------|
| Add a new user | [Users & Extensions](.claude/plugins/3cx-voip-system/SKILL.md#users--extensions) |
| Set up a call queue | [Call Queues & Ring Groups](.claude/plugins/3cx-voip-system/SKILL.md#call-queues--ring-groups) |
| Configure office hours | [Call Routing & IVR](.claude/plugins/3cx-voip-system/SKILL.md#call-routing--ivr) |
| Provision an IP phone | [IP Phone Configuration](.claude/plugins/3cx-voip-system/SKILL.md#ip-phone-configuration) |
| Add external phone line | [SIP Trunk Configuration](.claude/plugins/3cx-voip-system/SKILL.md#sip-trunk-configuration) |
| Import multiple users | [Bulk Import](#bulk-user-import) |
| Set up WhatsApp/Chat | [Multichannel Communication](.claude/plugins/3cx-voip-system/SKILL.md#multichannel-communication) |
| 3CX Talk & Meet links | [3CX Talk & Meet Links](#3cx-talk--meet-links) |
| Install/Use Web Client | [3CX Web Client Usage](#3cx-web-client) |
| Conference Calls | [Conference Calls](.claude/plugins/3cx-voip-system/SKILL.md#conference-calls) |
| Troubleshoot issues | [Advanced Troubleshooting](.claude/plugins/3cx-voip-system/SKILL.md#advanced-troubleshooting) |

## License

This project is distributed under the **MIT License**. The repository contains:

- **Agent Skill** – Custom instructions for AI agents (MIT License)
- **Knowledge Base** – Documentation and reference materials (MIT License)
- **Templates** – CSV import templates (MIT License)
- **Official 3CX Documentation** – Copyright 3CX, reproduced for reference purposes (https://www.3cx.com/docs/)

---

<p align="center">
  <strong>If you find this documentation helpful, please consider giving it a star ⭐</strong>
</p>

<p align="center">
  <a href="https://github.com/btafoya/3cx-voip-system">
    <img src="https://img.shields.io/badge/GitHub-View%20on%20GitHub-blue?logo=github" alt="View on GitHub">
  </a>
</p>

---

**Last Updated:** 2026-03-09 | **3CX Version Reference:** V20+