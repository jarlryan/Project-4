/* Functions By Ryan Jarl
   Created on: Mar 20, 2021
   This program implements functions to receive 
   an input file (mp4romanletrdata.txt) that contains
   data consisting of a series randomly placed roman 
   numerals and math operators, outputing roman numerals
   with their standard numeric conversions, and 
   calculates the standard numeric result using the 
   operator given on each line, with conversions back to 
   roman numerals.*/

#include <iostream>
#include <fstream>
#include <string>

using namespace std;

void get_Data(ifstream &input, string &R1, string &R2, char &Oper) //Gets data from file, passes values by reference and establishes order from which the files reads.
{
	input >> R1 >> R2 >> Oper;
}

int convert_from_Roman_to_Decimal(string R) //Passes strings of roman numerals and filters them through the switch statement and converts to decimal.
{
	int N = 0;

	for(int x = 0; x < R.size(); x++)
	{
		switch (R[x])
		{
		case 'I':
			N += 1;
			break;
		case 'V':
			N += 5;
			break;
		case 'X':
			N += 10;
			break;
		case 'L':
			N += 50;
			break;
		case 'C':
			N += 100;
			break;
		case 'D':
			N += 500;
			break;
		case 'M':
			N += 1000;
			break;
		default:
			cout << "Error" << endl;
		}
	}
	return N;
}

string convert_from_Decimal_to_Roman(int N) //Passes whatever number is converted through series of statements, and returns new roman values (for result).
{
	string R = "";
	while (N > 0)
	{
			if (N >= 1000)
			{
				R += "M";
				N -= 1000;
			}
			else if (N >= 500)
			{
				R += "D";
				N -= 500;
			}
			else if (N >= 100)
			{
				R += "C";
				N -= 100;
			}
			else if (N >= 50)
			{
				R += "L";
				N -= 50;
			}
			else if (N >= 10)
			{
				R += "X";
				N -= 10;
			}
			else if (N >= 5)
			{
				R += "V";
				N -= 5;
			}
			else if (N >= 1)
			{
				R += "I";
				N -= 1;
			}
	}
	return R;
}

int calc_Romans(int N1, int N2, char Oper) //Used to simultaneously get operator and decide how each operator affects converted decimals (calculations).
{
		switch (Oper)
		{
		case '+':
			return N1 + N2;
			break;
		case '-':
			return N1 - N2;
			break;
		case '*':
			return N1 * N2;
			break;
		case '/':
			if (N2 > 0)
		{
			return N1 / N2;
		}
			else
			break;
		}
		return 0;
}
void print_Result(string R1, string R2, char Oper, string result, int Nresult) //Used to print results from called upon functions.
{
	cout << "The First Number Is: " << R1 << "(" << convert_from_Roman_to_Decimal(R1) << ")" << endl;
	cout << "The Second Number Is: " << R2 << "(" << convert_from_Roman_to_Decimal(R2) << ")" << endl;
	cout << "The Operator Is: " << Oper << endl;
	cout << "The Result Is: " << Nresult << "(" << result << ")" << endl;
	cout << "****************************************" << endl;
}
int main()
{
	string R1, R2, result;
	int N1, N2, Nresult;
	char Oper;

	ifstream input;
	input.open("mp4romanletrdata.txt");
	while (!input.eof())
	{
		get_Data(input, R1, R2, Oper);
		N1 = convert_from_Roman_to_Decimal(R1);
		N2 = convert_from_Roman_to_Decimal(R2);
		Nresult = calc_Romans(N1, N2, Oper);
		result = convert_from_Decimal_to_Roman(Nresult);
		print_Result(R1, R2, Oper, result, Nresult);
		input.get();
	}
	input.close();
	return 0;
}
