# smart-chef-ai
Multi-agent AI system that generates personalized recipes from available ingredients
# 🍳 SmartChef AI – Multi-Agent Recipe Creator

SmartChef AI is a **multi-agent AI system** that generates **personalized, diet-friendly, and occasion-specific recipes** using only the ingredients provided by the user.

This project was built as part of the **Google Capstone – Agents Intensive Program** to demonstrate **agentic AI design**, modular architecture, and real-world problem solving.

---

## 📌 Problem Statement

Many people struggle daily with deciding what to cook using the ingredients they already have.  
Traditional recipe applications require long browsing, manual filtering, and often result in wasted food or poor meal choices.

There is a need for an intelligent system that can:
- Instantly suggest recipes
- Use available ingredients efficiently
- Adapt to diet preferences and occasions

---

## 💡 Solution Overview

SmartChef AI solves this problem using a **multi-agent approach**.

The system:
- Understands ingredients from natural language
- Generates multiple recipe options
- Filters by diet and event (lunchbox, party, quick meals)
- Ranks recipes using user preferences
- Stores preferences for personalization

---

## 🤖 Why Multi-Agent Architecture?

A single AI prompt is not sufficient for this problem because recipe creation involves multiple reasoning steps.

Using multiple agents allows:
- Task specialization
- Better accuracy
- Scalability and maintainability
- Personalization using memory

---

## 🏗️ System Architecture

**Flow:**

User Input  
→ Ingredient Interpreter Agent  
→ Recipe Generation Agent  
→ Ranking & Personalization Agent  
→ Final Recipe Recommendations  

---

## 🧩 Agent Details

### 1️⃣ Ingredient Interpreter Agent
**Role:** Cleans and normalizes user input.

**Responsibilities:**
- Extracts ingredients from free-text input
- Normalizes ingredient names
- Removes duplicates and invalid items

---

### 2️⃣ Recipe Generation Agent
**Role:** Generates recipe options.

**Responsibilities:**
- Uses cleaned ingredients
- Matches recipes from a dataset
- Applies dietary constraints
- Produces multiple recipe suggestions

---

### 3️⃣ Ranking & Personalization Agent
**Role:** Filters and ranks recipes.

**Responsibilities:**
- Applies diet rules (vegetarian, vegan, etc.)
- Ranks recipes by preparation time and relevance
- Uses stored user preferences for personalization

---

## 🧠 Memory System

- **Session Memory:** Stores ingredients and generated recipes during a session
- **Long-Term Memory:** Stores user preferences for future recommendations

This enables personalized results across sessions.

---

## 🛠️ Tech Stack

- **Language:** Python 3
- **Architecture:** Multi-Agent AI System
- **Concepts Used:** Agent orchestration, memory, modular design
- **Platform:** GitHub

---

## 📁 Project Structure

smart-chef-ai/
├── main.py
├── agents/
│ ├── interpreter.py
│ ├── generator.py
│ └── ranker.py
├── tools/
│ └── recipe_db.py
├── memory/
│ └── session_store.py
├── requirements.txt
└── README.md


---

## 🌍 Impact

- Reduces food waste
- Saves time in daily meal planning
- Encourages healthier eating
- Demonstrates real-world agentic AI design

---

## 🏁 Conclusion

SmartChef AI demonstrates how **multi-agent AI systems** can effectively solve real-world problems by breaking complex workflows into specialized components.  
The project highlights modular design, personalization, and scalability.

---

## 👩‍💻 Author

**Ashwitha Ummalla**  
Google Capstone – Agents Intensive

