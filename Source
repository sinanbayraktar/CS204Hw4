#include <iostream>
#include <string>
#include<sstream>
#include<fstream>
#include "dynintstack.h"

using namespace std;

void ClearStack(DynIntStack & myStack)  // deletion of stack
{
	int value;
	
	while(!myStack.isEmpty())
	myStack.pop(value);
}

int main()
{
	DynIntStack myStack;

	string fileName;
	cout<<"Enter the name of the file: ";
	cin>>fileName;

	ifstream input;
	input.open(fileName);

	while(input.fail())  // error message for wrong file names
	{
		cout<< "Error:Could not open the file "<< fileName<< endl;

		cout<<"Enter the input file name"<< endl;
		cin>>fileName;

		ifstream input;
		input.open(fileName);
	}

	string line;

	for(int i=1; !input.eof(); i++)
	{
		getline(input, line);
		stringstream ss(line);

		char c;
		int deletionValue;

		while (ss>>c)
		{
			if (c == '{')  // opening braket
			{
				myStack.push(i);
			}

			if (c == '}' && myStack.isEmpty())  // early syntax error
			{
				cout<<"Syntax error in line "<<i<<"."<<endl;
				return 0;
			}

			if (c == '}' && !myStack.isEmpty())  // code block
			{
				myStack.pop(deletionValue);
				cout<<"Code block: "<<deletionValue<<" - "<<i<<endl;
			}
		}
	}

	if (!myStack.isEmpty() )  // if stack is not empty at the end of the program
	{
		cout<<"Syntax error at the end of the program"<<endl;
		ClearStack(myStack);
	}

} // end of the program
