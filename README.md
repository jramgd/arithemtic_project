# arithemtic_project
def arithmetic_arranger(problems, show_answers=False):
    # Check for too many problems
    if len(problems) > 5:
        return "Error: Too many problems."
    
    # Initialize parts
    first_line = []
    second_line = []
    dashes = []
    answers = []

    # Process each problem
    for problem in problems:
        parts = problem.split()
        
        # Validate problem structure
        if len(parts) != 3:
            return "Error: Invalid problem format."
        num1, operator, num2 = parts[0], parts[1], parts[2]
        
        # Check operator
        if operator not in ['+', '-']:
            return "Error: Operator must be '+' or '-'."
        
        # Check numbers are digits
        if not num1.isdigit() or not num2.isdigit():
            return "Error: Numbers must only contain digits."
        
        # Check number length
        if len(num1) > 4 or len(num2) > 4:
            return "Error: Numbers cannot be more than four digits."
        
        # Determine width
        max_length = max(len(num1), len(num2)) + 2
        
        # Format the problem
        first_line.append(num1.rjust(max_length))
        second_line.append(operator + " " + num2.rjust(max_length - 2))
        dashes.append("-" * max_length)
        
        # Calculate and store answer
        if show_answers:
            if operator == "+":
                result = str(int(num1) + int(num2))
            else:
                result = str(int(num1) - int(num2))
            answers.append(result.rjust(max_length))

    # Combine lines with four spaces in between
    arranged_problems = (
        "    ".join(first_line) + "\n" +
        "    ".join(second_line) + "\n" +
        "    ".join(dashes)
    )
    if show_answers:
        arranged_problems += "\n" + "    ".join(answers)

    return arranged_problems

# Example Usage
print(arithmetic_arranger(["32 + 698", "3801 - 2", "45 + 43", "123 + 49"]))
print()
print(arithmetic_arranger(["32 + 8", "1 - 3801", "9999 + 9999", "523 - 49"], True))
