## Integration of a Mathematical Calulations with a Chat Completion System using LLM Function-Calling

### AIM:
To design and implement a Python function that calculates the area of a circle given its radius, and integrate it with a chat completion system using the function-calling feature of a large language model (LLM) for interactive computation and detailed explanation.

### PROBLEM STATEMENT:
Develop a Python-based solution that accurately calculates the area of a circle when provided with its radius. The solution should not only compute the area but also provide a step-by-step explanation of the calculation process. Additionally, the function must be integrated with a large language model (LLM) using its function-calling feature, enabling users to interactively request area calculations through natural language inputs.

### DESIGN STEPS:

#### STEP 1:
Install required packages

#### STEP 2:
Give the essential function calling code into it

#### STEP 3:
Integrate the function into an LLM-based chat completion system with function-calling capabilities.

### PROGRAM:
```
from dotenv import load_dotenv
import google.generativeai as genai
import os

# Load API key from .env
load_dotenv()
genai.configure(api_key="AIzaSyChL3CmyEpJnCIkuOqSEmOWjv5XHdySSIE")

# Create a Gemini model
model = genai.GenerativeModel("gemini-1.5-flash")

import math
import json

# Function to actually calculate the area
def find_area_of_circle(radius):
    """Calculate the area of a circle given its radius"""
    area = math.pi * (radius ** 2)
    circle_info = {
        "shape": "circle",
        "radius": radius,
        "formula": "π × r²",
        "area": area,
        "steps": [
            f"Step 1: Square the radius ({radius}² = {radius ** 2})",
            f"Step 2: Multiply by π ({math.pi:.2f} × {radius ** 2})",
            f"Step 3: The area is {area:.2f}"
        ]
    }
    return json.dumps(circle_info, indent=4)

# Function definition schema
functions = [
    {
        "name": "find_area_of_circle",
        "description": "Calculate the area of a circle given its radius",
        "parameters": {
            "type": "object",
            "properties": {
                "radius": {
                    "type": "number",
                    "description": "The radius of the circle (e.g., 7.0)",
                }
            },
            "required": ["radius"],
        },
    }
]

# Example messages
messages = [
    {
        "role": "user",
        "content": "Find the area of a circle with radius 7"
    }
]

# Example usage
if __name__ == "__main__":
    print(find_area_of_circle(7))
```

### OUTPUT:

<img width="923" height="387" alt="image" src="https://github.com/user-attachments/assets/56a7bb93-60aa-455e-8fd2-e891c3dd7e5b" />




### RESULT:
Hence,the python program to design and implement a Python function for converting miles to km, integrating it with a chat completion system utilizing the function-calling feature of a large language model (LLM) is written successfully and executed.
