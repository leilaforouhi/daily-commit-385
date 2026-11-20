import time

def calculate_wpm(text, duration):
    words = len(text.split())

    if duration <= 0:
        return 0

    minutes = duration / 60
    return words / minutes

def main():
    print("Typing Speed Tester")
    print("-------------------")
    print("Type the following sentence:\n")

    target = (
        "Practice makes progress. "
        "Consistent effort improves typing speed."
    )

    print(target)
    input("\nPress Enter when ready...")

    print("\nStart typing:")
    start = time.time()

    typed_text = input("> ")

    end = time.time()
    duration = end - start

    words = len(typed_text.split())
    wpm = calculate_wpm(typed_text, duration)

    accuracy = 0

    if target:
        correct = sum(
            1 for a, b in zip(typed_text, target)
            if a == b
        )

        accuracy = correct / len(target) * 100

    print("\n--- Typing Report ---")
    print(f"Time: {duration:.2f} seconds")
    print(f"Words typed: {words}")
    print(f"Typing speed: {wpm:.2f} WPM")
    print(f"Character accuracy: {accuracy:.2f}%")

if __name__ == "__main__":
    main()
