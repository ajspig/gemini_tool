# Writing Style Analysis & Research Agent

A workflow for building a custom research agent that learns your writing style and generates content that matches your voice using Gemini CLI and your personal knowledge base.

## Overview

This project creates a personalized research agent that analyzes your writing style from markdown notes and browser history, then generates content that matches your unique voice. It leverages your Obsidian vault and Firefox browsing data to create contextually rich, stylistically consistent research documents.

## Problem/Use Case

- **Style Consistency**: Maintaining your unique writing voice across different research documents and drafts
- **Context Integration**: Combining personal notes with recent research to create comprehensive content
- **Personalized AI**: Training an AI agent to write like you, not like a generic assistant
- **Research Synthesis**: Automatically connecting your existing knowledge with new information from your browsing history

## How to Run

### Prerequisites
- Gemini CLI installed and configured
- Obsidian vault with markdown notes (or any folder with markdown files)
- Firefox browser history path mine is /Users/abbyspig/Library/Application Support/Firefox/Profiles/fk42ywmv.default-release                   │

### Step-by-Step Workflow

1. **Set up your project directory**
   ```bash
   mkdir writing-agent
   cd writing-agent
   ```
2. **Start gemini-cli**

3. **Add your data sources**
   ```bash
   /directory add /path/to/your/obsidian/vault
   /directory add /path/to/your/firefox/history
   ```

4. **Generate your writing style profile**
   ```bash
   gemini-cli "Analyze my writing voice from these markdown notes and generate a markdown file that describes my writing style. Save the markdown file as user_context.md"
   ```

5. **Create research content with your style**
   ```bash
   gemini-cli "Given this outline @{path to note outline} use the @user_context.md to direct my writing style and complement the first draft with research from my recent firefox history found here @{path to firefox history}""
   ```

## Where Gemini is Called

- **Style Analysis**: Gemini analyzes your markdown notes to extract writing patterns, tone, structure preferences, and vocabulary choices
- **Content Generation**: Gemini synthesizes your existing notes with recent research to create new content in your voice
- **Research Integration**: Gemini connects information from your Firefox history with your personal knowledge base

## What's Local

- **Obsidian Vault**: Your personal markdown notes and knowledge base
- **Firefox History**: Your browsing data and research trails
- **Generated Files**:
  - `user_context.md` (your writing style profile)
  - Research documents and drafts
- **File Processing**: All analysis happens locally through Gemini CLI

## What's Hard/Interesting

- **Style Extraction**: Identifying subtle writing patterns from unstructured notes (Obsidian imports from Notion can have weird formatting)
- **Context Synthesis**: Meaningfully combining personal notes with browser history without overwhelming the model
- **Voice Consistency**: Maintaining authentic writing style while incorporating new research
- **Data Integration**: Seamlessly blending structured notes with unstructured browsing data
- **Prompt Engineering**: Crafting prompts that preserve writing voice while adding substantive research

## What's Next

### MCP Server Integration
- **Custom MCP Server**: Build a Model Context Protocol server that automatically:
  - Monitors your Obsidian vault for changes
  - Tracks your research patterns from browser history
  - Updates your writing style profile over time
  - Provides real-time writing assistance

### Potential Enhancements
- **Multi-source Analysis**: Incorporate other writing samples (emails, documents, social media)
- **Style Evolution Tracking**: Monitor how your writing style changes over time
- **Collaborative Research**: Share anonymized style patterns with team members
- **Auto-updating Context**: Continuously refine the writing style model as you create more content
- **Research Recommendations**: Suggest relevant sources based on your writing patterns and interests

## File Structure
```
writing-agent/
├── user_context.md          # Generated writing style profile
├── research_drafts/         # Generated research documents
├── source_notes/           # Reference to Obsidian vault
└── browser_context/        # Firefox history integration
```

## Notes
- Obsidian file names may appear unusual if imported from Notion (ignore the weird formatting)
- Works with any folder containing markdown files, not just Obsidian
- The system learns from both content and structure of your existing notes
- Firefox history provides recent research context to complement existing knowledge
