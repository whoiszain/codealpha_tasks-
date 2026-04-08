def get_response(user_input):
    """Return a predefined reply based on the user's input."""
    text = user_input.strip().lower()

    if text in ("hello", "hi", "hey"):
        return "Hi! How can I help you today?"

    elif text in ("how are you", "how are you?", "how r you"):
        return "I'm fine, thanks! How about you?"

    elif text in ("i'm fine", "i am fine", "good", "doing well"):
        return "Great to hear that! 😊"

    elif text in ("what is your name", "what's your name", "who are you"):
        return "I'm a simple rule-based chatbot built with Python!"

    elif text in ("what can you do", "help", "what do you do"):
        return "I can respond to greetings, questions, and simple phrases. Try saying hello!"

    elif text in ("bye", "goodbye", "see you", "exit", "quit"):
        return "Goodbye! Have a great day! 👋"

    else:
        return "Sorry, I didn't understand that. Try saying 'hello', 'how are you', or 'bye'."


def main():
    """Main loop — keeps the chat going until the user says bye."""
    print("=" * 45)
    print("       Welcome to the Simple Chatbot!")
    print("  (type 'bye' or 'quit' to end the chat)")
    print("=" * 45 + "\n")

    while True:
        user_input = input("You: ").strip()

        if not user_input:          # ignore blank lines
            continue

        response = get_response(user_input)
        print(f"Bot: {response}\n")

        # Exit the loop when the user says goodbye
        if user_input.strip().lower() in ("bye", "goodbye", "see you", "exit", "quit"):
            break


if __name__ == "__main__":
    main()
