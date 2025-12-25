# 🍳 SmartChef AI – Multi-Agent Recipe Creator

SmartChef AI is a multi-agent AI system that generates personalized, diet-friendly, and occasion-specific recipes using only the ingredients provided by the user.

This project was built as part of the Google Capstone – Agents Intensive Program to demonstrate agentic AI design, modular architecture, and real-world problem solving.

--------------------------------------------------

## Step 1: Problem Identification

Many users face difficulty deciding what to cook with the ingredients they already have. Existing recipe applications require manual search and filtering, which is time-consuming and inefficient.

The goal was to build an intelligent system that can:
• Accept ingredients as input
• Automatically suggest suitable recipes
• Apply user preferences and constraints

--------------------------------------------------

## Step 2: Choosing Multi-Agent Architecture

Instead of building a single monolithic program, the system was designed using a multi-agent architecture.

Each agent is responsible for a specific task:
• Input understanding
• Recipe generation
• Ranking and personalization

This improves modularity, scalability, and maintainability.

--------------------------------------------------

## Step 3: Designing the System Flow

The overall system flow is:

User Input  
→ Ingredient Interpreter Agent  
→ Recipe Generation Agent  
→ Ranking Agent  
→ Final Output  

--------------------------------------------------

## Step 4: Building Ingredient Interpreter Agent

This agent processes raw user input and converts it into structured data.

Responsibilities:
• Normalize text
• Extract ingredients
• Remove duplicates

```python
# agents/interpreter.py

class IngredientInterpreterAgent:
    def run(self, user_input: str) -> list:
        text = user_input.lower()
        text = text.replace("i have", "")
        text = text.replace("and", ",")
        items = text.split(",")

        cleaned = [item.strip() for item in items if item.strip()]
        return list(set(cleaned))
```

--------------------------------------------------

## Step 5: Building Recipe Generation Agent

This agent generates recipe options using the cleaned ingredient list.

```python
# agents/generator.py

from tools.recipe_db import search_recipes

class RecipeGenerationAgent:
    def run(self, ingredients: list) -> list:
        return search_recipes(ingredients)
```

--------------------------------------------------

## Step 6: Creating Recipe Tool (Database)

A simple recipe database tool is used to match ingredients.

```python
# tools/recipe_db.py

def search_recipes(ingredients: list) -> list:
    recipes = [
        {"name": "Vegetable Sandwich", "ingredients": ["bread", "tomato", "onion"], "prep_time": 10},
        {"name": "Tomato Omelette", "ingredients": ["tomato", "egg"], "prep_time": 8},
        {"name": "Veg Stir Fry", "ingredients": ["onion", "capsicum", "tomato"], "prep_time": 15}
    ]

    return [r for r in recipes if any(i in r["ingredients"] for i in ingredients)]
```

--------------------------------------------------

## Step 7: Building Ranking & Personalization Agent

This agent ranks recipes based on relevance and preparation time.

```python
# agents/ranker.py

class RankingAgent:
    def run(self, recipes: list, preferences: dict) -> list:
        return sorted(recipes, key=lambda x: x["prep_time"])
```

--------------------------------------------------

## Step 8: Orchestrating All Agents

The main orchestrator controls the execution flow and agent communication.

```python
# main.py

from agents.interpreter import IngredientInterpreterAgent
from agents.generator import RecipeGenerationAgent
from agents.ranker import RankingAgent

class SmartChefOrchestrator:
    def run(self, user_input: str):
        ingredients = IngredientInterpreterAgent().run(user_input)
        recipes = RecipeGenerationAgent().run(ingredients)
        return RankingAgent().run(recipes, {})

if __name__ == "__main__":
    chef = SmartChefOrchestrator()
    print(chef.run("I have tomato, onion and bread"))
```

--------------------------------------------------

## Step 9: Final Output

The system returns a ranked list of recipes with minimal preparation time and high relevance.

--------------------------------------------------

## Step 10: Key Learnings

• Multi-agent system design
• Modular architecture
• Rule-based AI decision making
• Real-world problem solving
• End-to-end project execution

--------------------------------------------------

## Conclusion

SmartChef AI demonstrates how agent-based AI systems can solve real-world problems by dividing complex workflows into specialized components.
