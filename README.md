# assignment-1-Ai
<img width="1157" height="890" alt="image" src="https://github.com/user-attachments/assets/553137ec-a192-401e-b773-8fe9d9820119" />
# crypto_chatbot.py

crypto_db = {  
    "Bitcoin": {  
        "price_trend": "rising",  
        "market_cap": "high",  
        "energy_use": "high",  
        "sustainability_score": 3/10  
    },  
    "Ethereum": {  
        "price_trend": "stable",  
        "market_cap": "high",  
        "energy_use": "medium",  
        "sustainability_score": 6/10  
    },  
    "Cardano": {  
        "price_trend": "rising",  
        "market_cap": "medium",  
        "energy_use": "low",  
        "sustainability_score": 8/10  
    }  
}

def respond_to_query(user_query):
    user_query = user_query.lower()

    if "sustainable" in user_query or "eco" in user_query:
        recommend = max(crypto_db, key=lambda x: crypto_db[x]["sustainability_score"])
        return f"Green alert! 🌱 {recommend} has the highest sustainability score – great for eco-conscious investing!"

    elif "trending" in user_query or "rising" in user_query:
        trending = [coin for coin, data in crypto_db.items() if data["price_trend"] == "rising"]
        return f"The cryptos currently trending up 📈 are: {', '.join(trending)}."

    elif "long-term" in user_query or "growth" in user_query:
        for coin, data in crypto_db.items():
            if data["price_trend"] == "rising" and data["market_cap"] == "high":
                return f"For long-term growth, consider {coin}! 🚀 Strong trend and market cap."
        return "None of the current cryptos match ideal long-term growth traits right now."

    elif "energy" in user_query or "low energy" in user_query:
        low_energy = [coin for coin, data in crypto_db.items() if data["energy_use"] == "low"]
        return f"Coins with low energy use 🔋: {', '.join(low_energy)}."

    elif "exit" in user_query:
        return "Thanks for chatting with GreenSatoshi 🌱. Stay green, and invest smart!"

    else:
        return "Hmm 🤔 I didn't catch that. Try asking about sustainability, trends, energy use, or long-term growth!"

def start_chat():
    print("👋 Welcome to GreenSatoshi 🌱 – your friendly crypto eco-advisor.")
    print("Ask me about trending coins, energy use, or sustainable options.")
    print("Type 'exit' to end the chat.\n")

    while True:
        user_input = input("You: ")
        response = respond_to_query(user_input)
        print(f"GreenSatoshi 🌱: {response}\n⚠️ Crypto is risky—always do your own research!\n")
        if "exit" in user_input.lower():
            break

if __name__ == "__main__":
    start_chat()
