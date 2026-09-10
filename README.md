# AI Game Development using CrewAI

## Overview

This project is a multi-agent Generative AI application that converts a simple user game idea into a 2D game.

The system uses multiple specialized AI agents to handle game design, code generation, and code review.

## Technologies Used

* Python
* CrewAI
* Google Gemini
* Pygame
* PyGBag
* ngrok

## Architecture

```text
User Game Idea
       ↓
Game Designer Agent
       ↓
Game Design Document
       ↓
Python Game Developer Agent
       ↓
Pygame Code
       ↓
QA Engineer Agent
       ↓
Reviewed / Improved Code
       ↓
Playable Game
```

## AI Agents

### 1. Game Designer Agent

The Game Designer Agent takes the user's game idea and creates a structured game design.

It defines:

* Game objective
* Controls
* Game entities
* Game mechanics
* Win/lose conditions

### 2. Python Game Developer Agent

The Python Developer Agent receives the game design as context and generates a complete Python/Pygame implementation.

The generated game includes:

* Player movement
* Obstacles
* Jumping
* Collision detection
* Scoring
* Game-over logic
* Game loop

### 3. QA Engineer Agent

The QA Agent reviews the game design and generated code.

It checks:

* Whether the generated code follows the design
* Potential syntax/runtime issues
* Missing functionality
* Code quality
* Possible improvements

## Workflow

The project uses CrewAI's sequential process.

```text
Game Idea
   ↓
Design Task
   ↓
Code Generation Task
   ↓
QA Review Task
   ↓
Final Code
```

The output of earlier tasks is passed to later tasks using task context.

For example:

```python
context=[task_design]
```

allows the code-generation task to use the game design.

The QA task receives:

```python
context=[task_design, task_code]
```

so it can review the implementation against the original design.

## Example Input

```text
A fun endless runner where a character jumps over obstacles.
```

## Example Output

The system generates a simple Pygame endless-runner game where:

* The player can jump.
* Obstacles move toward the player.
* Collision causes Game Over.
* The score increases as the player survives.

## LLM

Google Gemini is used as the underlying language model for the CrewAI agents.

The API key is stored securely using environment/secret management rather than being hardcoded in the source code.

## Running the Project

Install the required packages:

```bash
pip install -U crewai
pip install "crewai[google-genai]"
pip install "crewai[tools]"
pip install pygame
```

Configure the required API keys using your environment or notebook secret manager.

Then open:

```text
AI_Game_Development_CrewAI.ipynb
```

in Google Colab or Jupyter Notebook and execute the cells.

## Future Improvements

For a production-ready version, I would add:

* Automated testing of generated code
* Sandboxed execution of AI-generated Python code
* RAG using Pygame documentation
* LLM/code evaluation
* Better error handling
* Logging and monitoring
* Secure production API-key management
* Cloud deployment

## Project Concept

The main concept demonstrated by this project is **multi-agent orchestration**, where specialized AI agents collaborate to complete different stages of a larger software-development task.
