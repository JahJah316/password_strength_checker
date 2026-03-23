# password_strength_checker
import re
import random
import string

def check_password(password):
    score = 0

    if len(password) >= 8:
        score += 1
    if re.search(r'[A-Z]', password):
        score += 1
    if re.search(r'[a-z]', password):
        score += 1
    if re.search(r'[0-9]', password):
        score += 1
    if re.search(r'[!@#$%^&*(),.?":{}|<>]', password):
        score += 1

    if score <= 2:
        return "Password too weak"
    elif score == 3 or score == 4:
        return "Moderate password"
    else:
        return "Strong password"

def generate_suggestion(length=12):
    characters = string.ascii_letters + string.digits + "!@#$%^&*()"
    suggestion = ''.join(random.choice(characters) for _ in range(length))
    return suggestion


# MAIN PROGRAM (runs the code)
password = input("Enter your password: ")

print(check_password(password))

suggestion = generate_suggestion()
print(f"Suggested strong password: {suggestion}")
Why I built this:
This is my first official project and I wanted to start getting into cybersecurity projects. I wanted to also explore how password security works. 
