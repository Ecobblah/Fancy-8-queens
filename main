//Emmanuel Cobblah
//HW 12 Fancy chess board
#include<iostream>
#include<cstdlib>
using namespace std;
void main() {
	int i, j, k, l;
	typedef char box[5][7];
	box bb, wb,bq,wq, *board[8][8];
	int q[8], c = 0, count = 1;
	q[0] = 0;
	
	//This what makes the black and white queen
	for (int i = 0;i < 5;i++)
		for (int j = 0;j < 7;j++){
			if (i == 4 || i == 0 || j == 0 || j == 6 || (i==1 && j==2) || (i==1 && j==4) ) {
				bq[i][j] = ' ';
				wq[i][j] = char(219);
			}
			else {
				bq[i][j] = char(219);
				wq[i][j] = ' ';
			}
		}
	//fill in bb=black box and wb=whitebox
	for (i = 0;i<5;i++)
		for (j = 0;j<7;j++)
		{
			wb[i][j] = ' ';
			bb[i][j] = char(219);
		}
	//###ALGORITHM PART##//
NC:c++;
	if (c == 8)
		goto print;// we moved to next col because we already places a 1 on the col
	q[c] = -1;//if it new col it will put a neg -1 to show nothing has happened.


NR:q[c]++;//increment the number that represent the 1 in the row of the col;

	if (q[c] == 8) //if the number goes off the board go to Backtrack.	
		goto BT;
	for (int i = 0;i < c;i++)//row test
		if (q[c] == q[i] || c - i == abs(q[c] - q[i])) // row is constant and what moving is the colum based on the i
			goto NR;//if it does see a 1 in any of those conditions go to new row

	goto NC;

BT:c--;// move a col back
	if (c == -1)//at the end backtrack will make row 0 go back to row -1 to solve the problem but that off the board.
		return exit(1);//End program
	goto NR;

print:
	//outputs the 1d array
	for (int j = 0;j < 8;j++)
		cout << q[j]; 
	cout << endl;
	//Fills the board up, with no queens
	for (i = 0;i < 8;i++)
		for (j = 0;j < 8;j++)
			if ((i + j) % 2 == 0)
				board[i][j] = &wb;
			else
				board[i][j] = &bb;
	//Takes the value of the q array, that been shown it has placed 8 queens
	for (int i = 0;i < c;i++) {
		if (board[q[i]][i]==&wb)//if the board square box is white place a bq if not place wq
			board[q[i]][i] = &bq;//takes the 1d array value, whcihs represents the row, and i loops to 8 and places queen waheter q[i] is.
		else
			board[q[i]][i] = &wq;
	}
	// print the board via the pointers in array board
	//This prints the whole board with queens from 1d array.
	cout << " ";
	for (i = 0;i<7 * 8;i++)
		cout << '_';
	cout << endl;
	for (i = 0;i<8;i++)
		for (k = 0;k<5;k++){
			cout << " " << char(179); //print left border
			for (j = 0;j<8;j++)
				for (l = 0;l<7;l++)
					cout << (*board[i][j])[k][l];
			cout << char(179) << endl; // at end of line print bar and then newline
		}
	cout << " ";
	for (i = 0;i<7 * 8;i++)
		cout << char(196);
	cout << endl;
	//Print the solution #
	cout << "Solution number: " << count++ << endl << endl;
	goto BT;// after it outputs it should go back to BT so we can get more solutions untill it reaches the end.

}
