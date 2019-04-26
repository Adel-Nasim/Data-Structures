#include <iostream>
#include <cassert>
using namespace std;
class arrayQueueType
{
	int rear;
	int front;
	int length;
	int *arr;
	int maxSize;

public:
	arrayQueueType(int size) {
		if (size <= 0)
			maxSize = 100;
		else
			maxSize = size;

		front = 0;

		arr = new int[maxSize];
		rear = maxSize - 1;
		length = 0;
	}
	int isEmpty()
	{
		return length == 0;
	}
	bool isFull()
	{
		return length == maxSize;
	}
	void addQueue(int Element)
	{
		if (isFull())
		{
			cout << "Queue Full Can't Enqueue ...!";
		}
		else
		{
			rear = (rear + 1) % maxSize;
			arr[rear] = Element;
			length++;
		}


	}
	void deleteQueue()
	{
		if (isEmpty())
		{
			cout << "Empty Queue Can't Dequeue ...!";
		}
		else
		{
			front = (front + 1) % maxSize;
			--length;

		}


	}
	int frontQueue()
	{
		assert(!isEmpty());
		return arr[front];
	}

	int rearQueue()
	{
		assert(!isEmpty());
		return arr[rear];
	}


	void printQueue()
	{
		if (!isEmpty()) {
			for (size_t i = front; i != rear; i = (i + 1) % maxSize)
			{
				cout << arr[i] << " ";
			}
			cout << arr[rear];
		}
		else
			cout << "Empty Queue";
	}


	int queueSearch(int element) {
		int pos = -1;
		if (!isEmpty())
		{
			for (int i = front; i != rear; i = (i + 1) % maxSize)
				if (arr[i] == element)
				{
					pos = i;
					break;
				}
			if (pos == -1)
			{
				if (arr[rear] == element)
					pos = rear;
			}
		}
		else
			cout << "Q is empty ! " << endl;
		return pos;
	}


	~arrayQueueType() {
		delete[]arr;
	}
};

int main()
{
	arrayQueueType q1(5);
	q1.addQueue(10);
	q1.addQueue(20);
	q1.addQueue(30);
	q1.addQueue(40);
	q1.addQueue(50);
	q1.printQueue();
	return 0;
}
