import random
import json

# 📚 Sample vocabulary (you can expand this easily)
words = {
    "apple": "سیب",
    "book": "کتاب",
    "sun": "خورشید",
    "moon": "ماه",
    "water": "آب",
    "friend": "دوست",
    "happy": "خوشحال",
    "beautiful": "زیبا",
    "family": "خانواده",
    "dream": "رویا"
}

def main():
    print("🌍 Welcome to English Trainer!")
    print("Type the correct translation for each word.\n")

    score = 0
    total = len(words)

    # Randomize question order
    keys = list(words.keys())
    random.shuffle(keys)

    for eng in keys:
        ans = input(f"👉 What is the meaning of '{eng}' in Persian? ").strip()
        if ans == words[eng]:
            print("✅ Correct!\n")
            score += 1
        else:
            print(f"❌ Wrong! The correct answer is '{words[eng]}'\n")

    print("🏁 Training finished!")
    print(f"Your score: {score}/{total} ({(score/total)*100:.1f}%)")

    # Save results
    result = {"score": score, "total": total}
    with open("last_result.json", "w", encoding="utf-8") as f:
        json.dump(result, f, ensure_ascii=False, indent=4)

    print("\n📊 Your progress was saved in 'last_result.json'")

if __name__ == "__main__":
    main()

