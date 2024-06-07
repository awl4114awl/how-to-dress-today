# How to Dress Today

Welcome to the "How to Dress Today" project! This guide will walk you through the code step by step, helping you understand how it works and how to use it to get clothing recommendations based on the weather.

### Step 1: Import Necessary Libraries

The first step is to import the required libraries. We use `requests` to fetch weather data from an API and `json` to handle JSON data.

```python
import requests
import json
```

### Step 2: Define the Weather API Function

We define a function `get_weather` that takes a `location` as an argument and returns the weather data for that location.

- We construct the API URL using the base URL and the location.
- We make a GET request to the API and parse the response as JSON.
- We return the weather data.

```python
def get_weather(location):
    api_key = 'your_api_key_here'  # Replace with your actual API key
    base_url = 'http://api.openweathermap.org/data/2.5/weather?q='
    complete_url = f"{base_url}{location}&appid={api_key}&units=metric"
    
    response = requests.get(complete_url)
    data = response.json()
    
    if data['cod'] != '404':
        main = data['main']
        weather = data['weather'][0]
        return {
            'temperature': main['temp'],
            'humidity': main['humidity'],
            'description': weather['description']
        }
    else:
        return None
```

### Step 3: Define the Clothing Recommendation Function

Next, we define a function `recommend_clothing` that takes the temperature as an argument and returns clothing recommendations.

- We use simple if-else statements to provide recommendations based on the temperature.

```python
def recommend_clothing(temperature):
    if temperature < 0:
        return "Wear a heavy coat, gloves, and a hat."
    elif 0 <= temperature < 10:
        return "Wear a coat and a hat."
    elif 10 <= temperature < 20:
        return "Wear a jacket or sweater."
    elif 20 <= temperature < 30:
        return "Wear a t-shirt and jeans."
    else:
        return "Wear shorts and a t-shirt."
```

### Step 4: Main Function

In the main function, we:

- Get the location from the user.
- Fetch the weather data using the `get_weather` function.
- If the data is available, print the weather details and the clothing recommendation.
- If the data is not available, print an error message.

```python
if __name__ == "__main__":
    location = input("Enter your city: ")
    weather = get_weather(location)
    
    if weather:
        print(f"Current temperature: {weather['temperature']}°C")
        print(f"Weather description: {weather['description']}")
        print(recommend_clothing(weather['temperature']))
    else:
        print("City not found.")
```

## Full Code

Here is the complete code for your reference:

```python
import requests
import json

def get_weather(location):
    api_key = 'your_api_key_here'  # Replace with your actual API key
    base_url = 'http://api.openweathermap.org/data/2.5/weather?q='
    complete_url = f"{base_url}{location}&appid={api_key}&units=metric"
    
    response = requests.get(complete_url)
    data = response.json()
    
    if data['cod'] != '404':
        main = data['main']
        weather = data['weather'][0]
        return {
            'temperature': main['temp'],
            'humidity': main['humidity'],
            'description': weather['description']
        }
    else:
        return None

def recommend_clothing(temperature):
    if temperature < 0:
        return "Wear a heavy coat, gloves, and a hat."
    elif 0 <= temperature < 10:
        return "Wear a coat and a hat."
    elif 10 <= temperature < 20:
        return "Wear a jacket or sweater."
    elif 20 <= temperature < 30:
        return "Wear a t-shirt and jeans."
    else:
        return "Wear shorts and a t-shirt."

if __name__ == "__main__":
    location = input("Enter your city: ")
    weather = get_weather(location)
    
    if weather:
        print(f"Current temperature: {weather['temperature']}°C")
        print(f"Weather description: {weather['description']}")
        print(recommend_clothing(weather['temperature']))
    else:
        print("City not found.")
```

By following this guide, you should be able to understand how the code works and how to use it to get clothing recommendations based on the weather.
