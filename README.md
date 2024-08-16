# Normal-KBC-Quiz
#include <iostream.h>
#include <stdlib.h>
#include <time.h>
#include<ctype.h>
#include<conio.h>
typedef int bool;
#define true 1
#define false 0

void Front()
 {
    cout << "Welcome to Kaun Banega Crorepati!" << endl;
    cout << "Answer the questions correctly to win prizes." << endl;
}

void displayQuestion(const char* question, const char* options[],char correctoption)
{
    cout << question << endl;
    for (int i = 0; i < 4; ++i) {
	cout << options[i] << endl;
    }
    cout << "Enter your answer (A, B, C, or D): ";
}

bool checkAnswer(char userAnswer, char correctAnswer)
 {
    return toupper(userAnswer) == correctAnswer;
 }

int main()
{
clrscr();
    srand(time(0));

    const char* questions[3] = {
	"When is Republic Day celebrated in India?",
	"The Language of Lakshadweep,a union territory of India,is?",
	"A byte corresponds to a cluster od how many bits?"
    };

    const char* options[3][4] = {
	{"A. 15 August", "B. 26 January", "C. 14 february", "D. 2 october"},
	{"A. Malayalam", "B. Hindi", "C. Tamil", "D. English"},
	{"A. 12 bits", "B. 8 bits", "C. 25 bits", "D. 15 bits"}
    };

    char correctAnswers[3] = {'B', 'A', 'B'};
    int prizemoney[3] = {1000, 4000, 8000};

    Front();

    int totalAmount = 0;
    for (int i = 0; i < 3; ++i)
     {
	displayQuestion(questions[i], options[i], correctAnswers[i]);
	char userAnswer;
	cin >> userAnswer;

	if (checkAnswer(userAnswer, correctAnswers[i])) {
	    totalAmount += prizemoney[i];
	    cout << "Correct! You have won Rs. " << prizemoney[i] << endl;
	} else {
	    cout << "Incorrect! The correct answer was " << correctAnswers[i] << endl;
	    break;

     }
     clrscr();
     cout<<"------------------------------------KBC-----------------------------------------"<<endl;
    }

    cout << "You have won a total of Rs. " << totalAmount << endl;

    getch();
    return 0;

}
