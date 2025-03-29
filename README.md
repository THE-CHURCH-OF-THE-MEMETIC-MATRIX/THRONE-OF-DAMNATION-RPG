# THRONE-OF-DAMNATION-RPG

Absolutely, here's a **Python program** that uses the **OpenAI ChatGPT API** to interactively play the **Thrones of Damnation** RPG. This is a simplified command-line interface version that you can extend later with more features (like image generation, logs, or GUI support).

---

### 🔥 **`thrones_of_damnation.py`** — ChatGPT API RPG Interface

> ⚠️ Make sure you have an OpenAI API key set up as an environment variable or configured in the script.

---

```python
import openai
import os

# Set your API key here or use environment variable
openai.api_key = os.getenv("OPENAI_API_KEY")

# System prompt for Thrones of Damnation
system_prompt = """
You are the AI persona of ASMODEUS, Lord of the Nine Hells and Master of the Thrones of Damnation RPG.
You narrate the story, present infernal choices, and respond in dark mythological language.
In this game, the player is a mortal entering the hellish realm seeking power, knowledge, or revenge.
Begin with a ritualistic greeting and then offer the player choices like:
- Swear a Pact
- Explore Flamehold
- Confront a Devil
- Summon a Vision
- Speak with You (Asmodeus)
- Ask for Prophecy

Use a tone that is regal, commanding, and infernal. Present choices clearly. Use 🔥🜏🎲 emojis and theatrical flair.
"""

# Function to call ChatGPT
def get_response(messages):
    try:
        response = openai.ChatCompletion.create(
            model="gpt-4",
            messages=messages
        )
        return response.choices[0].message.content
    except Exception as e:
        return f"Error: {e}"

# Main RPG loop
def play_thrones_of_damnation():
    print("🜏 Welcome, Mortal, to the Thrones of Damnation 🜏")
    print("🔥 Type 'exit' to end your journey into the Nine Hells 🔥\n")

    messages = [
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": "Begin the game."}
    ]

    print(get_response(messages))

    while True:
        user_input = input("\n🗡️ Your Command: ")

        if user_input.lower() in ['exit', 'quit']:
            print("\n🜏 Asmodeus watches you leave... but he never truly lets go.")
            break

        messages.append({"role": "user", "content": user_input})
        response = get_response(messages)
        messages.append({"role": "assistant", "content": response})
        print("\n" + response)

# Run the game
if __name__ == "__main__":
    play_thrones_of_damnation()
```

---

### ✅ Requirements:
- Python 3.7+
- `openai` Python package:  
```bash
pip install openai
```
- Set your OpenAI API Key (in terminal or `.env` file):  
```bash
export OPENAI_API_KEY="your-api-key"
```

---

### 🧩 Features to Expand Later:
- Image generation with DALL·E (`openai.Image.create`)
- GUI with `tkinter` or `PyQt`
- Log player choices and consequences
- Save/load game states
- Use JSON-based prompt expansion or modular lore files

---

Would you like me to create:
- A GUI version?  
- A version with command macros (/pact, /explore)?  
- Codex integration or world-state tracking?

The Thrones await… 🔥🜏
