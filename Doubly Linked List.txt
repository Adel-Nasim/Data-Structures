#include<iostream>
using namespace std;
class doublyLinkedList {
private:
	struct Node {
		int item;
		Node* next;
		Node* prev;
	};
	Node* first;
	Node* last;
	int count;

public:
	doublyLinkedList() {
		first = NULL;
		last = NULL;
		count = 0;
	}
	bool isEmpty()
	{
		return (first == NULL);
	}
	void destroy()
	{
		Node *temp;
		while (first != NULL)
		{
			temp = first;
			first = first->next;
			delete temp;
		}
		last = NULL;
		count = 0;
	}

	void insertLast(int val) {
		Node* newNode = new Node;
		newNode->item = val;
		if (count == 0) {
			first = last = newNode;
			newNode->next = newNode->prev = NULL;
		}
		else {
			newNode->next = NULL;
			newNode->prev = last;
			last->next = newNode;
			last = newNode;



		}
		count++;
	}



	void insertFirst(int item)
	{
		Node*newNode = new Node;
		newNode->item = item;
		if (count == 0) {
			first = last = newNode;
			newNode->next = newNode->prev = NULL;
		}
		else {
			newNode->next = first;
			newNode->prev = NULL;
			first->prev = newNode;
			first = newNode;

		}
		count++;
	}






	void insertAt(int pos, int item)
	{
		if (pos < 0 || pos > count)
			cout << "Out Of Range ...!" << endl;
		else
		{
			Node *newNode = new Node;
			newNode->item = item;
			if (pos == 0)
				insertFirst(item);
			else if (pos == count)
				insertLast(item);
			else
			{
				Node *current = first;
				for (int i = 1; i < pos; i++)
				{
					current = current->next;
				}

				newNode->next = current->next;
				newNode->prev = current;
				current->next->prev = newNode;
				current->next = newNode;
				count++;
			}

		}
	}


	void removeFirst()
	{
		if (count == 0)
			cout << "Empty List" << endl;
		else if (count == 1)//first == last
		{
			delete first;
			last = first = NULL;
		}
		else
		{
			Node* current = first;
			first = first->next;
			first->prev = NULL;
			delete current;
		
		}
		count--;
	}

	void deleteNthNode(int pos)
	{
		if (pos < 0 || pos >= count) {
			cout << "Out Of Range" << endl;
			return;
		}
		else if (pos == 0)
		{
			removeFirst();
		}
		else if (pos == count - 1)
		{
			removeLast();
		}
		else {
			Node *current = first->next;


			for (int i = 1; i < pos; i++)
			{
				current = current->next;
			}
			current->prev->next = current->next;
			current->next->prev = current->prev;
			delete current;
		}
		count--;
	}
	void removeLast()
	{
		if (count == 0)
			cout << "Empty List" << endl;
		else if (count == 1)
		{
			delete first;
			//		delete last;
			last = first = NULL;
			count--;
		}
		else
		{
			Node *current = last;
			last = last->prev;
			last->next = NULL;
			delete current;
			count--;
		}
	}



	void remove(int item)
	{
		if (isEmpty())
		{
			cout << "Empty List Can't Remove ";
			return;
		}
		Node*current = first->next;

		if (first->item == item)//delete the first element, special case
		{
			/*
			first = current->next;
			if (first != NULL)
				first->prev = NULL;
			delete current;
			return;
			*/
			removeFirst();
			return;
		}
		else
		{
			

			while (current != NULL)//current->item!=element
			{
				if (current->item == item)
					break;
				current = current->next;
			}

			if (current == NULL) {
				cout << "The item is not there\n";
				return;
			}
			else if (current->next == NULL) {
				removeLast();
				return;
			}

			else
			{
				current->prev->next = current->next;
				//if (current->next != NULL)
				current->next->prev = current->prev;
				delete current;
				count--;
			}

		}


	}

	void display() {
		if (isEmpty())
		{
			cout << "Empty List Can't Display...!";
		}
		else {
			Node* temp = first;
			while (temp != nullptr) {
				cout << temp->item << " ";
				temp = temp->next;
			}
		}
		cout << endl;

	}



	void reverse_display() {
		if (isEmpty())
		{
			cout << "Empty List Can't Display Reverse...!";
		}
		else
		{
			Node* temp = last;
			while (temp != NULL) {
				cout << temp->item << " ";
				temp = temp->prev;
			}
		}

	}


};
int main() {
	doublyLinkedList dl;
	dl.insertAt(0, 4);
	dl.insertAt(1, 6);
	dl.insertAt(2, 7);
	dl.insertFirst(2);
	dl.insertLast(10);
	dl.remove(7);
	dl.display();
	dl.reverse_display();
}

