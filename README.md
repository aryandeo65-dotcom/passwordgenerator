import random
import string

def generate_password(length):
    """Generates a random password of the specified length."""
    if length < 4:
        return "Password length should be at least 4 characters for better security."

    all_characters = string.ascii_letters + string.digits + string.punctuation

    password = [
        random.choice(string.ascii_uppercase),
        random.choice(string.ascii_lowercase),
        random.choice(string.digits),
        random.choice(string.punctuation)
    ]

    remaining_length = length - 4
    password += random.choices(all_characters, k=remaining_length)


    random.shuffle(password)

    
    return ''.join(password)


if _name_ == "_main_":
    try:
        user_length = int(input("Enter desired password length: "))
        generated_password = generate_password(user_length)
        print("Generated Password:", generated_password)
    except ValueError:
        print("Invalid input. Please enter a numeric value.")
