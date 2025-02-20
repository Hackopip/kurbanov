using System;

namespace TicTacToe
{
    class Program
    {
        static void Main(string[] args)
        {
            char[] gameBoard = new char[9];
            int position;
            char playerSymbol;

            for (int i = 0; i < 9; i++)
            {
                gameBoard[i] = ';
            }

            while (true)
            {
                Console.WriteLine("Игровое поле:");
                Console.WriteLine(" " + gameBoard[0] + " | " + gameBoard[1] + " | " + gameBoard[2] + " ");
                Console.WriteLine("-----------");
                Console.WriteLine(" " + gameBoard[3] + " | " + gameBoard[4] + " | " + gameBoard[5] + " ");
                Console.WriteLine("-----------");
                Console.WriteLine(" " + gameBoard[6] + " | " + gameBoard[7] + " | " + gameBoard[8] + " ");

                Console.WriteLine("Введите позицию для X или O (1-9): ");
                position = Convert.ToInt32(Console.ReadLine()) - 1;

                if (gameBoard[position]!= ')
                {
                    Console.WriteLine("Позиция уже занята. Попробуйте еще раз.");
                    continue;
                }

                playerSymbol = (position < 3)? 'X' : 'O';
                gameBoard[position] = playerSymbol;

                Console.WriteLine("Ход игрока " + playerSymbol + ".");

                if (CheckWinner(playerSymbol))
                {
                    Console.WriteLine("Игрок " + playerSymbol + " выиграл!");
                    break;
                }

                if (CheckTie())
                {
                    Console.WriteLine("Игра в ничью!");
                    break;
                }
            }
        }

        static bool CheckWinner(char symbol)
        {
            // Проверка горизонтальных линий
            for (int i = 0; i < 3; i++)
            {
                if (gameBoard[i * 3] == symbol && gameBoard[i * 3 + 1] == symbol && gameBoard[i * 3 + 2] == symbol)
                {
                    return true;
                }
            }

            // Проверка вертикальных линий
            for (int i = 0; i < 3; i++)
            {
                if (gameBoard[i] == symbol && gameBoard[i + 3] == symbol && gameBoard[i + 6] == symbol)
                {
                    return true;
                }
            }

            // Проверка диагоналей
            if (gameBoard[0] == symbol && gameBoard[4] == symbol && gameBoard[8] == symbol)
            {
                return true;
            }
            if (gameBoard[2] == symbol && gameBoard[4] == symbol && gameBoard[6] == symbol)
            {
                return true;
            }

            return false;
        }

        static bool CheckTie()
        {
            for (int i = 0; i < 9; i++)
            {
                if (gameBoard[i] == ')
                {
                    return false;
                }
            }
            return true;
        }
    }
}
