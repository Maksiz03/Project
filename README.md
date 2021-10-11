using System;
class Program
{
    private static void CountingBrackets(string str, int length, ref int a, ref int b, ref int count,
        ref int countMax)
    {
        for (var i = 0; i < length; i++)
        {
            if (str[i] == '(')
                a += 1;
            else if (str[i] == ')')
            {
                if ((i != length - 1 && str[i + 1] != '(') || i == length - 1)
                    count++;
                b += 1;
            }
            if (a == b)
            {
                if (count > countMax)
                    countMax = count;
                count = 0;
            }
        }
    }
    private static void CheckAnswer(int a, int b, int countMax)
    {
        if (a == b)
            Console.WriteLine(countMax);
        else Console.WriteLine("Не корерктно");
    }
    static void Main()
    {
        var str = Console.ReadLine();
        var length = str.Length;
        if (length == 0)
        {
            Console.WriteLine("Не кооректно");
            return;
        }
        var a = 0;
        var b = 0;
        var count = 0;
        var countMax = 0;
        CountingBrackets(str, length, ref a, ref b, ref count, ref countMax);
        CheckAnswer(a, b, countMax);
    }
}