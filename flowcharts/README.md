# Flowchart: User Registration Process

This flowchart visualizes the backend workflow for registering a new user in the Airbnb Clone system. It includes input validation, email uniqueness check, password encryption, and secure data storage.

![User Registration Flowchart](https://github.com/Hali1439/alx-airbnb-project-documentation/blob/ed6fa6f753ec92b9bc009bee3ea0dbbe8bf5ff17/flowcharts/data-flow-diagram.png))

## Steps:
1. Collect user input (name, email, password).
2. Validate input format and required fields.
3. Check if the email is already registered.
4. Hash password using bcrypt.
5. Store new user in the database.
6. Generate JWT token for authentication.
7. Send optional welcome or confirmation email.
8. Return a success response.


