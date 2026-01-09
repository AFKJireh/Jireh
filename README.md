import sys
import random

def start_recommendation_engine():
    print("--- Welcome to the Ultimate Game Finder ---")
    
    # 1. Device Check
    device = input("First, what device are you using? (PC, Console, or Mobile): ").strip().lower()

    # 2. Interest & Personality Questions
    print("\nAnswer the following questions so I can get to know your gaming style:")
    
    q1 = input("1. Do you prefer exploring a story or testing your reflexes? (Story/Reflexes): ").strip().lower()
    q2 = input("2. How do you feel about horror? (Love it/Hate it): ").strip().lower()
    q3 = input("3. Would you describe yourself as a 'Loner' or a 'Social Butterfly'? (Loner/Social): ").strip().lower()
    q4 = input("4. Do you prefer realistic graphics or stylized/cartoonish art? (Realistic/Stylized): ").strip().lower()

    # 3. Recommendation Logic
    # We use a simple logic gate to suggest a game based on the device and the 'Story vs Reflex' answer
    suggestion = ""
    
    if device == "pc":
        if q1 == "story":
            suggestion = "Baldur's Gate 3" if q3 == "social" else "The Witcher 3"
        else:
            suggestion = "Valorant" if q2 == "hate it" else "Dead by Daylight"
            
    elif device == "console":
        if q1 == "story":
            suggestion = "The Last of Us" if q4 == "realistic" else "The Legend of Zelda"
        else:
            suggestion = "Elden Ring" if q2 == "love it" else "Rocket League"
            
    elif device == "mobile":
        if q1 == "story":
            suggestion = "Genshin Impact"
        else:
            suggestion = "PUBG Mobile" if q3 == "social" else "Monument Valley"
    else:
        suggestion = "Minecraft (The Universal Choice)"

    print(f"\n--- Based on your personality, you should play: {suggestion}! ---")

    # 4. The Download/Exit Sequence
    download = input(f"\nWould you like to download {suggestion} now? (Yes/No): ").strip().lower()

    if download == "yes":
        print(f"\nRedirecting you to the official {device} store to download {suggestion}...")
        print("Please follow the on-screen instructions at the store page. Happy gaming!")
    else:
        print("\nSelection declined. Closing application...")
        sys.exit()

if __name__ == "__main__":
    start_recommendation_engine()
