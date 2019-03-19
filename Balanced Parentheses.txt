#include<iostream>
#include<stack>
#include<string>
using namespace std;
bool ArePair(char open, char close)
{
	if (open == '(' && close == ')') 
		return true;
	else if (open == '{' && close == '}') 
		return true;
	else if (open == '[' && close == ']')
		return true;
	return false;
}
bool AreBalanced(string exp)
{
	stack<char>  S;
	int length = exp.length();
	for (int i = 0; i < length; i++)
	{
		if (exp[i] == '(' || exp[i] == '{' || exp[i] == '[')
			S.push(exp[i]);
		else if (exp[i] == ')' || exp[i] == '}' || exp[i] == ']')
		{
			if (S.empty() || !ArePair(S.top(), exp[i]))
				return false;
			else
				S.pop();
		}
	}
	return S.empty() ? true : false;
}

int main()
{
	
	string expression;
	cout << "Enter an expression:";
	cin >> expression;
	if (AreBalanced(expression))
		cout << "Balanced\n";
	else
		cout << "Not Balanced\n";

	return 0;
}
