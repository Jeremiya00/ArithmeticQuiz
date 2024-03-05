# ArithmeticQuiz
using System;

namespace ArithmeticQuizForTheUser
{
    class ArithmeticQuiz
    {
        static void Main(string[] args)
        {
            Random random = new Random();
            int totalQuestions = random.Next(5, 10);
            int correctAnswers = 0;

            Console.WriteLine("Arithmetic Quiz\n");

            for (int i = 1; i <= totalQuestions; i++)
            {
                int num1 = random.Next(1, 101);
                int num2 = random.Next(1, 101);
                char[] operators = { '+', '-', '*', '/' };
                char op = operators[random.Next(0, operators.Length)];

                Console.Write($"Question {i}: What is {num1} {op} {num2}? ");
                double userAnswer;
                bool parsed = double.TryParse(Console.ReadLine(), out userAnswer);

                if (parsed)
                {
                    double correctAnswer = 0;

                    if (op == '+')
                    {
                        correctAnswer = num1 + num2;
                    }
                    else if (op == '-')
                    {
                        correctAnswer = num1 - num2;
                    }
                    else if (op == '*')
                    {
                        correctAnswer = num1 * num2;
                    }
                    else if (op == '/')
                    {
                        correctAnswer = (double)num1 / num2;
                    }

                    if (userAnswer == correctAnswer)
                    {
                        Console.WriteLine("Correct!\n");
                        correctAnswers++;
                    }
                    else
                    {
                        Console.WriteLine($"Incorrect! The correct answer is {correctAnswer}.\n");
                    }
                }
                else
                {
                    Console.WriteLine("Invalid input. Skipping this question.\n");
                }
            }

            Console.WriteLine("Results:");
            Console.WriteLine($"Total of Correct Answers: {correctAnswers}");
            double percentage = (double)correctAnswers / totalQuestions * 100;
            Console.WriteLine($"Percentage of Correct Answers: {percentage}%");
        }
    }

}
