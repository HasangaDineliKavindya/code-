# code-
def arithmetic_arranger(problems, show_answers=False):
    if len(problems) > 5:
        return "Error: Too many problems."

    arranged_problems = []
    for problem in problems:
        operands = problem.split()
        if len(operands) != 3:
            return "Error: Invalid problem format."

        operand1 = operands[0]
        operator = operands[1]
        operand2 = operands[2]

        if operator not in ["+", "-"]:
            return "Error: Operator must be '+' or '-'."

        if not operand1.isdigit() or not operand2.isdigit():
            return "Error: Numbers must only contain digits."

        if len(operand1) > 4 or len(operand2) > 4:
            return "Error: Numbers cannot be more than four digits."

        if operator == "+":
            result = int(operand1) + int(operand2)
        else:
            result = int(operand1) - int(operand2)

        width = max(len(operand1), len(operand2)) + 2
        arranged_problems.append(f"{operand1.rjust(width)}\n{operator} {operand2.rjust(width - 2)}\n{'-' * width}")
        if show_answers:
            arranged_problems[-1] += f"\n{str(result).rjust(width)}"

    return "    ".join(arranged_problems)

