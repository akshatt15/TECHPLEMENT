# TECHPLEMENT
Random Password Manager(Python)
import random
import string

def generate_password(length, use_uppercase, use_lowercase, use_digits, use_symbols):
    characters = ''
    if use_uppercase:
        characters += string.ascii_uppercase
    if use_lowercase:
        characters += string.ascii_lowercase
    if use_digits:
        characters += string.digits
    if use_symbols:
        characters += string.punctuation
    
    if not characters:
        print("Error: Please select at least one character type.")
        return None
    
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def get_bool_input(prompt):
    while True:
        user_input = input(prompt).lower()
        if user_input == 'y':
            return True
        elif user_input == 'n':
            return False
        else:
            print("Invalid input. Please enter 'y' or 'n'.")

def main():
    print("Welcome to the Random Password Generator!")
    length = int(input("Enter the length of the password: "))
    
    use_uppercase = get_bool_input("Do you want to include uppercase letters? (y/n): ")
    use_lowercase = get_bool_input("Do you want to include lowercase letters? (y/n): ")
    use_digits = get_bool_input("Do you want to include digits? (y/n): ")
    use_symbols = get_bool_input("Do you want to include symbols? (y/n): ")
    
    password = generate_password(length, use_uppercase, use_lowercase, use_digits, use_symbols)
    
    if password:
        print("Your random password is:", password)

if __name__ == "__main__":
    main()
