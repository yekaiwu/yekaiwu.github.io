---
title: "Chess Coach"
date: 2024-11-15
summary: "Intelligent chess coaching application combining Stockfish engine with LLMs for real-time analysis, AI commentary, and interactive coaching"
tags:
  - Full-Stack
  - Python
  - AI
  - React
tech_stack:
  - FastAPI
  - Python
  - LangChain
  - Stockfish
  - React
  - TypeScript
  - Material-UI
  - Vite
links:
  - type: github
    url: https://github.com/yekaiwu/Chess_Coach
    label: Code
featured: true
status: "Live"
role: "Solo Developer"
duration: "3 months"
team_size: 1
highlights:
  - "Combines Stockfish engine with GPT & Claude LLMs"
  - "Real-time position evaluation with centipawn scores"
  - "Interactive AI coach with adjustable proficiency levels"
  - "Four-tab analysis interface for comprehensive coaching"
---

An intelligent chess coaching web application that merges Stockfish engine analysis with large language models to deliver real-time coaching, commentary, and tactical guidance.

## Overview

Built a full-stack chess coaching platform that bridges the gap between classical chess engines and modern AI. The application leverages Stockfish for precise move evaluation while using LLMs (OpenAI GPT and Anthropic Claude) to translate complex engine analysis into human-readable coaching insights.

## Key Features

### Analysis Interface
- **Evaluation Tab** - Real-time position assessment with centipawn scores and win probabilities that update dynamically with each move
- **Commentary Tab** - AI-generated analysis of the most recent move with tactical insights and strategic explanations
- **Coach Chatbot** - Interactive LLM-powered coaching with persistent conversation history and adjustable expertise levels
- **Tactics Tab** - Opening detection and identification, turn-based strategic recommendations, and best-move continuations

### Coaching Capabilities
- **Adaptive Proficiency Levels** - Coach adjusts explanations based on player skill level
- **Context-Aware Analysis** - LLM maintains game context throughout the session for coherent coaching
- **Opening Recognition** - Detects and names chess openings as they are played
- **Best Move Suggestions** - Engine-backed recommendations with natural language explanations

## Technical Highlights

### AI Integration
- Dual LLM support with OpenAI GPT and Anthropic Claude via LangChain orchestration
- Configurable `LLM_PROVIDER` and `STOCKFISH_DEPTH` for tunable analysis intensity
- Persistent conversation history enabling contextual follow-up questions
- Pydantic data validation ensuring clean data flow between engine and LLM layers

### Architecture
- Dependency injection pattern for clean, testable backend services
- Singleton Stockfish analyzer instance for efficient resource management
- Modular route handling across game management, analysis, and LLM integration
- Centralized frontend state management with full TypeScript type safety

### Performance
- Real-time game state synchronization between board UI and analysis engine
- Configurable Stockfish search depth balancing analysis quality and response speed
- Vite-powered frontend build for fast development and optimized production bundles

## Architecture

```
┌──────────────────┐     ┌─────────────────┐     ┌──────────────┐
│  React Frontend  │────▶│  FastAPI Backend │────▶│  Stockfish   │
│  (Material-UI)   │     │   (LangChain)    │     │   Engine     │
└──────────────────┘     └────────┬────────┘     └──────────────┘
                                  │
                         ┌────────▼────────┐
                         │   LLM Provider  │
                         │ (GPT / Claude)  │
                         └─────────────────┘
```

## Challenges & Solutions

### Challenge 1: Engine-to-Language Translation
**Problem**: Stockfish outputs raw centipawn scores and algebraic notation that are meaningless to casual players

**Solution**: Built a LangChain pipeline that feeds engine output into the LLM with structured prompts, producing natural language coaching that preserves the analytical accuracy of the engine

### Challenge 2: Conversation Continuity
**Problem**: Maintaining coherent coaching context across multiple moves and user questions

**Solution**: Implemented persistent conversation history with game state injection into each LLM call, giving the coach full awareness of the position and prior discussion

### Challenge 3: Real-Time Synchronization
**Problem**: Keeping board UI, engine analysis, and LLM commentary in sync without stale state

**Solution**: Centralized state management on the frontend with sequential API calls ensuring analysis always reflects the current board position

## Results

- **Dual AI Backend**: Seamlessly supports both OpenAI GPT and Anthropic Claude with a single config toggle
- **Comprehensive Analysis**: Four distinct coaching modes covering evaluation, commentary, chat, and tactics
- **Clean Architecture**: Dependency injection and singleton patterns enable easy extension and testing
- **Type Safety**: Full TypeScript coverage on the frontend prevents runtime errors in complex game state handling

## Tech Stack Details

**Frontend**
- React 18 with TypeScript
- Material-UI for component library
- Chess.js for game logic and validation
- React Chessboard for board visualization
- Axios for HTTP communication
- Vite as build tool

**Backend**
- FastAPI (Python) for REST API
- Python Chess library for game state management
- Stockfish engine for move evaluation
- LangChain for LLM orchestration
- Pydantic for data validation and serialization

**AI & Services**
- OpenAI GPT (configurable model)
- Anthropic Claude (configurable model)
- Stockfish open-source chess engine

## Future Improvements

- [ ] Game import via PGN files
- [ ] Session persistence and game history
- [ ] Multiplayer analysis mode
- [ ] Mobile-responsive layout improvements
- [ ] Custom opening repertoire trainer

## Screenshots

{{< gallery images="featured.png, screenshot-2.png, screenshot-3.png" >}}

## Lessons Learned

1. **LLM as Translator**: The most valuable use of LLMs here is not generating moves but translating engine analysis into coaching language—a task they excel at
2. **Context is Everything**: Feeding full game context into each LLM call dramatically improves coaching quality over stateless prompts
3. **Separation of Concerns**: Keeping engine logic, LLM integration, and API routing in separate modules made iteration much faster
4. **Type Safety Pays Off**: TypeScript on the frontend caught several state management bugs early that would have been painful to debug at runtime

---

**Project Status**: ✅ Live
**GitHub**: [View Source Code](https://github.com/yekaiwu/Chess_Coach)
