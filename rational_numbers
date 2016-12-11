//
//Operations with two rational numbers
// 1) Calculating primes
// 2) Simplification of the entered rational numbers
// 3) +, -, *, / operations

#include <stdio.h>
#include <iostream>
#include <math.h>
#include <vector>

class rationalNumber{
public:
        int top,btm;
        bool divisionByZeroFlag = 0;

        rationalNumber(){}
        rationalNumber(int numerator, int denominator)
        {
        top=numerator;
        btm=denominator;
        }

        rationalNumber operator+ (rationalNumber &);
        rationalNumber operator- (rationalNumber &);
        rationalNumber operator* (rationalNumber &);
        rationalNumber operator/ (rationalNumber &);

        void denominatorCheck();
        void sign();
        void check();
        void simplify(std::vector<int>* a);

        friend std::ostream& operator << (std::ostream& stream, rationalNumber);
        friend std::istream& operator >> (std::istream& stream, rationalNumber&);
};
void rationalNumber::denominatorCheck()
{
        if(btm == 0)
        {
                puts("denominator = 0 , create another fraction");
                divisionByZeroFlag = 1;
        }
}
void rationalNumber::sign()
{
        if(btm < 0)
        {
                btm*=-1;
                top*=-1;
        }

}
void rationalNumber::check()
{
    denominatorCheck();
    if(!divisionByZeroFlag)
    {
     sign();
    }
}
void rationalNumber::simplify(std::vector<int>* primes)
{
    int divisor = 2;
	if(top == btm )
	{
		top =1;
		btm =1;
	}
    else
    {   if(btm != 1)
        {
            for (int i = 0; i < primes->size(); i++)
            {
                divisor = primes->at(i);
               while(top%divisor == 0 && btm%divisor==0)
                {
                        top/=divisor;
                        btm/=divisor;
                }
            }
        }
    }

}
std::istream& operator>> (std::istream& stream,rationalNumber& inside)
{
        char c;
        stream >> inside.top >> c >> inside.btm;
        return stream;

}
std::ostream& operator<< (std::ostream& stream,rationalNumber inside)
{
        stream << inside.top << "/" << inside.btm << "\n";
        return stream;

}
rationalNumber rationalNumber::operator+ (rationalNumber & inner)
{ if(inner.divisionByZeroFlag == 1 || divisionByZeroFlag == 1)
        {
			puts("operation can't be done\n");
        return rationalNumber(0,0);
        }
    else{
        return rationalNumber(top * inner.btm + btm * inner.top, btm * inner.btm);
        }
}
rationalNumber rationalNumber::operator- (rationalNumber & inner)
{
	 if(inner.divisionByZeroFlag == 1 || divisionByZeroFlag == 1)
        {
			puts("operation can't be done\n");
        return rationalNumber(0,0);
        }
    else{
        return rationalNumber(top * inner.btm - btm * inner.top, btm * inner.btm);
        }

}
rationalNumber rationalNumber::operator* (rationalNumber & inner)
{
	if(inner.divisionByZeroFlag == 1 || divisionByZeroFlag == 1)
        {
			puts("operation can't be done/n");
        return rationalNumber(0,0);
        }
    else{
        return rationalNumber(top * inner.top , btm * inner.btm);
        }

}
rationalNumber rationalNumber::operator/ (rationalNumber & inner)
{
	if(inner.divisionByZeroFlag ==1 || divisionByZeroFlag ==1 || inner.top == 0)
        {
                puts("Division by Zero\n");
                return rationalNumber(0,0);
        }
    else{

        return rationalNumber(top * inner.btm , btm * inner.top);
        }
}

void calculatePrimes(int lowerRange,int upperRange,std::vector<int>* primesRef){

     primesRef->push_back(2);
            for(int i =lowerRange; i < upperRange; i+=2)
            {
                bool isPrime=true;
                for(int j=0; j<primesRef->size() ; j++)
                {
                    if(i % primesRef->at(j) == 0)
                    {
                        isPrime=false;
                        break;
                    }
                }
                if(isPrime)
                {
                    primesRef->push_back(i);
                }
            }

}
rationalNumber setNumberByUser()
{
    rationalNumber number;
    do{
        puts("Enter a rational number");
        std::cin >> number;
        number.divisionByZeroFlag = 0;
        number.check();
      } while(number.divisionByZeroFlag);
        std::cout << '\n';
 return number;
}

int main()
{
        rationalNumber a,b,c;
        int upperLimit = 5000;
        std::vector<int> primes;

        std::cout << "This program do +,-,*,/ operations for two rational numbers." <<'\n' <<"For input type numerator/denominator,"<< '\n' << " for ex. 57/171 " << '\n';
        calculatePrimes(3,upperLimit,&primes);

        a = setNumberByUser();
        b = setNumberByUser();

        if(!a.divisionByZeroFlag){
            a.simplify(&primes);}
        if(!b.divisionByZeroFlag){
            b.simplify(&primes);}

        puts("You have entered:");
        std::cout << a << '\n';
        std::cout << b << '\n';

        c = a+b;
        c.simplify(&primes);
        puts("Addition");
        std::cout << c;

        c = a-b;
        c.simplify(&primes);
        puts("Subtraction");
        std::cout << c;

        c = a*b;
        c.simplify(&primes);
        puts("Multiplication");
        std::cout << c;

        c = a/b;
        c.simplify(&primes);
        puts("Division");
        std::cout << c;

    return 0;
}
