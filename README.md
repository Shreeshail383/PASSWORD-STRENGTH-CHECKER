def password_strength_checker(password):
    """
    Checks the strength of a password based on basic rules.
    Returns: WEAK, MEDIUM, or STRONG
    """

    score = 0

    # Flags to track password properties
    has_upper = False
    has_lower = False
    has_digit = False
    has_special = False

    special_chars = "!@#%^&*"

    # Length check
    if len(password) >= 8:
        score += 1

    # Loop through each character in the password
    for ch in password:
        if ch.isupper():
            has_upper = True
        elif ch.islower():
            has_lower = True
        elif ch.isdigit():
            has_digit = True
        elif ch in special_chars:
            has_special = True

    # Increase score based on conditions met
    if has_upper:
        score += 1
    if has_lower:
        score += 1
    if has_digit:
        score += 1
    if has_special:
        score += 1

    # Decide password strength
    if score <= 2:
        return "WEAK 👎"
    elif score <= 4:
        return "MEDIUM ‼️"
    else:
        return "STRONG 💪"


if __name__ == "__main__":
    password = input("Enter your password: ")
    result = password_strength_checker(password)
    print("Password Strength =", result)
