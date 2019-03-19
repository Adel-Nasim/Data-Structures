#include <iostream>
#include <stack>
#include <string>
using namespace std;
bool isOperator(char ch)
{
	if (ch == '+' || ch == '-' || ch == '*' || ch == '/')
		return true;
	else
		return false;
}
int performOperation(int op1, int op2, char op)
{
	int ans;
	switch (op) {
	case '+':
		ans = op2 + op1;
		break;
	case '-':
		ans = op2 - op1;
		break;
	case '*':
		ans = op2 * op1;
		break;
	case '/':
		ans = op2 / op1;
		break;
	}
	return ans;
}


int main()
{
	char exp[1000], buffer[15];
	int i, op1, op2, len, j, x;
	stack<int> s;
	cout<<"Enter a Postfix Expression: ( e.g. 4 5 * )\n";
	cin.getline(exp,1000);
	len = strlen(exp);
	j = 0;
	for (i = 0; i < len; i++) {

		if (exp[i] >= '0' && exp[i] <= '9') {
			buffer[j++] = exp[i];
		}
		else if (exp[i] == ' ') {
			if (j > 0) {
				buffer[j] = '\0';
				x = atoi(buffer);
				s.push(x);
				j = 0;
			}
		}

		else if (isOperator(exp[i])) {
			op1 = s.top();
			s.pop();
			op2 = s.top();
			s.pop();
			s.push(performOperation(op1, op2, exp[i]));
		}
	}
	cout<<"Answer = "<<s.top();
	return 0;
}
