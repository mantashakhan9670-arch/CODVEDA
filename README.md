# File Encryption and Decryption System
# Codveda Technologies Internship - Task 2

def encrypt(text, shift):
    encrypted_text = ""

    for char in text:
        encrypted_text += chr(ord(char) + shift)

    return encrypted_text


def decrypt(text, shift):
    decrypted_text = ""

    for char in text:
        decrypted_text += chr(ord(char) - shift)

    return decrypted_text


def encrypt_file(input_file, output_file, shift):
    try:
        with open(input_file, "r", encoding="utf-8") as file:
            content = file.read()

        encrypted_content = encrypt(content, shift)

        with open(output_file, "w", encoding="utf-8") as file:
            file.write(encrypted_content)

        print("File encrypted successfully!")
        print("Encrypted file saved as:", output_file)

    except FileNotFoundError:
        print("Error: File not found.")


def decrypt_file(input_file, output_file, shift):
    try:
        with open(input_file, "r", encoding="utf-8") as file:
            content = file.read()

        decrypted_content = decrypt(content, shift)

        with open(output_file, "w", encoding="utf-8") as file:
            file.write(decrypted_content)

        print("File decrypted successfully!")
        print("Decrypted file saved as:", output_file)

    except FileNotFoundError:
        print("Error: File not found.")


print("===== FILE ENCRYPTION & DECRYPTION =====")
print("1. Encrypt File")
print("2. Decrypt File")

choice = input("Enter your choice (1 or 2): ")
shift = 3

if choice == "1":
    input_file = input("Enter file name to encrypt: ")
    output_file = input("Enter encrypted file name: ")
    encrypt_file(input_file, output_file, shift)

elif choice == "2":
    input_file = input("Enter file name to decrypt: ")
    output_file = input("Enter decrypted file name: ")
    decrypt_file(input_file, output_file, shift)

else:
    print("Invalid choice.")
    print("Invalid choice. Please select a valid operation.")
