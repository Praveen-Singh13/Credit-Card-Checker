# Credit-Card-Validator
This C program validates credit card numbers using the Luhn algorithm. It checks if the number is structurally valid and identifies the card type as VISA, MASTERCARD, AMEX, or INVALID based on its prefix and length. A simple and efficient implementation using basic C logic.
#include <stdio.h>
#include <cs50.h>
long number;     int count=1;     int sum=0;
int checksum();
int main()
{
    number = get_long("Enter the credit card number:");
    long a=number;
    checksum();
    if (sum%10==0)
    {
        long n=a;
        while ( n >100)
        {
            n /= 10;
        }
        if (n/10 == 4 && (count-1 == 13 || count-1 == 16))
        {
            printf("VISA\n");
        }
        else if ((n==34 || n== 37) && count-1 == 15)
        {
            printf("AMEX\n");
        }
        else if ((n>= 51 && n<= 55) && count-1 == 16)
        {
            printf("MASTERCARD\n");
        }
        else
        {
            printf("INVALID\n");
        }
    }
    else
    {
        printf("INVALID\n");
    }
}
int checksum()
{
    while (number !=0)
    {
        int digit = number%10;
        if (count%2 == 0)
        {
            digit *=2;
            if (digit>9)
            {
                digit -=9;
            }
        }
        sum= sum+digit;
        number /= 10;
        count++;
    }
    return sum;
}

