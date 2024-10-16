//# Educational-Quiz-for-Special-Children
//The Educational Quiz for Special Children offers a personalized, engaging learning experience tailored to each child's abilities. It promotes inclusivity and skill development through adaptive features. Using technology like the Datetime Module and data structures, it ensures a seamless experience, though it requires tech access and maintenance.




import datetime

class EducationalQuiz:
    def __init__(self):
        self.questions = {
            "easy": ["What color is the sky?", "What is 2 + 2?", "How many legs does a cat have?"],
            "medium": ["Who painted the Mona Lisa?", "What is the capital of France?", "What is the largest planet in our solar system?"],
            "hard": ["What is the square root of 64?", "Who wrote 'Romeo and Juliet'?", "What is the powerhouse of the cell?"]
        }
        self.answers = {
            "easy": ["blue", "4", "4"],
            "medium": ["Leonardo da Vinci", "Paris", "Jupiter"],
            "hard": ["8", "William Shakespeare", "mitochondria"]
        }
        self.knowledge_level = None
        self.current_question = 0
        self.score = 0
        self.questions_to_ask = []
        self.start_time = None
        self.end_time = None
    def sample_test(self):
        sample_questions = ["What is 1 + 1?", "What color is a banana?", "How many days are in a week?"]
        correct_answers = ["2", "yellow", "7"]
        correct_count = 0

        print("Let's start with a few sample questions:")
        for i in range(3):
            answer = input(sample_questions[i] + " : ")
            if answer.lower() == correct_answers[i]:
                correct_count += 1
                print("Correct!")
            else:
                print("Incorrect.")
        
        if correct_count == 3:
            self.knowledge_level = "hard"
        elif correct_count == 2:
            self.knowledge_level = "medium"
        else:
            self.knowledge_level = "easy"
                self.questions_to_ask = self.questions[self.knowledge_level]
        print(f"Based on your performance, you will be answering {self.knowledge_level} level questions.")

    def check_answer(self):
        question = self.questions_to_ask[self.current_question]
        user_answer = input(question + " : ")

        correct_answer = self.answers[self.knowledge_level][self.current_question]
        
        if user_answer.lower() == correct_answer.lower():
            print("Correct!")
            self.score += 1
        else:
            print(f"Incorrect. The correct answer is: {correct_answer}")

        self.current_question += 1
        
        if self.current_question >= len(self.questions_to_ask):
            self.end_time = datetime.datetime.now()  # Record the end time of the quiz
            self.display_summary()
        else:
            self.questions_to_ask = self.questions[self.knowledge_level]

    def display_summary(self):
        duration = self.end_time - self.start_time
        print(f"Quiz completed. Your score is: {self.score}")
        print(f"Quiz started at: {self.start_time.strftime('%Y-%m-%d %H:%M:%S')}")
        print(f"Quiz ended at: {self.end_time.strftime('%Y-%m-%d %H:%M:%S')}")
        print(f"Total duration: {duration}")

    def run_quiz(self):
        name = input("Enter your name: ")
        age = int(input("Enter your age: "))
        print(f"Welcome, {name} ({age} years old)! Let's start the quiz.")
        
        self.start_time = datetime.datetime.now()  # Record the start time of the quiz
        print(f"Quiz started at: {self.start_time.strftime('%Y-%m-%d %H:%M:%S')}")

        self.sample_test()
        
        while self.current_question < len(self.questions_to_ask):
            self.check_answer()

if __name__ == "__main__":
    quiz = EducationalQuiz()
    quiz.run_quiz()

