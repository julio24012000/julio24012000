import random

class AsistenteAritmetica:
    def __init__(self):
        self.correct_answers = 0
        self.total_questions = 0

        self.positive_feedback = ["¡Muy bien!", "¡Excelente!", "¡Buen trabajo!", "¡Sigue así!"]
        self.negative_feedback = ["No. Por favor intenta de nuevo.", "Incorrecto. Intenta una vez más.", "¡No te rindas!", "No. Sigue intentando."]

    def generate_question(self, level, operation):
        if level == 1:
            num1 = random.randint(1, 9)
            num2 = random.randint(1, 9)
        elif level == 2:
            num1 = random.randint(1, 99)
            num2 = random.randint(1, 99)
        else:
            num1 = random.randint(1, 999)
            num2 = random.randint(1, 999)

        if operation == 1:
            question = f"¿Cuánto es {num1} + {num2}?"
            answer = num1 + num2
        elif operation == 2:
            question = f"¿Cuánto es {num1} - {num2}?"
            answer = num1 - num2
        elif operation == 3:
            question = f"¿Cuánto es {num1} * {num2}?"
            answer = num1 * num2
        else:
            question = f"¿Cuánto es {num1} / {num2}? (redondea a dos decimales)"
            answer = round(num1 / num2, 2)

        return question, answer

    def run(self):
        print("Bienvenido al programa de instrucción asistida por computadora de operaciones aritméticas básicas.")

        level = int(input("Por favor, elige el nivel de dificultad (1, 2, 3): "))
        operation = int(input("Por favor, elige el tipo de problema aritmético a estudiar (1: suma, 2: resta, 3: multiplicación, 4: división, 5: mezcla): "))

        while self.correct_answers < 10:
            question, answer = self.generate_question(level, operation)
            user_answer = float(input(question))

            if user_answer == answer:
                print(random.choice(self.positive_feedback))
                self.correct_answers += 1
            else:
                print(random.choice(self.negative_feedback))

        percentage_correct = (self.correct_answers / self.total_questions) * 100

        if percentage_correct < 75:
            print("Por favor pide ayuda adicional a tu instructor.")
        else:
            print("¡Felicidades, estás listo para pasar al siguiente nivel!")

        self.correct_answers = 0
        self.total_questions = 0

        restart = input("¿Quieres permitir que otro estudiante pruebe el programa? (s/n): ")
        if restart.lower() == "s":
            self.run()
        else:
            print("Gracias por usar el programa de instrucción asistida por computadora.")

--->
