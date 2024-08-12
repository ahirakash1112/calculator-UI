# calculator-UI
class Calculator:
    def __init__(self):
        self.expression = ""

    def add_to_expression(self, value):
        self.expression += str(value)

    def evaluate_expression(self):
        try:
            result = str(eval(self.expression))  # Evaluate the expression
            self.expression = result
            return result
        except Exception as e:
            self.expression = ""
            return "Error"

    def clear_expression(self):
        self.expression = ""
        return ""
