import re

def password_strength(password):
    # Initialize feedback list
    feedback = []

    # Check length
    if len(password) < 8:
        feedback.append("Password must be at least 8 characters long.")
    
    # Check for at least one uppercase letter
    if not re.search(r'[A-Z]', password):
        feedback.append("Password must contain at least one uppercase letter.")
    
    # Check for at least one lowercase letter
    if not re.search(r'[a-z]', password):
        feedback.append("Password must contain at least one lowercase letter.")

    # Check for at least one number
    if not re.search(r'[0-9]', password):
        feedback.append("Password must contain at least one number.")
    
    # Check for at least one special character
    if not re.search(r'[\W_]', password):
        feedback.append("Password must contain at least one special character (e.g., @, #, $, etc.).")
    
    # If feedback is empty, password is strong
    if not feedback:
        return "Password is strong."
    
    # Return all feedback
    return "\n".join(feedback)

# Example usage
password = input("Enter your password: ")
result = password_strength(password)
print(result)
