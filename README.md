# Lab-9: This program generates 25 random numbers in an array. It then finds and prints both the highest and lowest values in the array and their positions, and also finds and prints the average of the values in the array. The program also prints a table that displays the position of the value, the value, and the difference between the value and the average.

#include <iostream>
#include <cstdlib>

using namespace std;

void generateRandomNumbers(int arr[], int size);
void findAndPrintHighest(int arr[], int size);
void findAndPrintLowest(int arr[], int size);
double findAndGetAverage(int arr[], int size);
void printDifferences(int arr[], int size, double average);

int main()
{
	const int SIZE = 25;

	int arr[SIZE];

	generateRandomNumbers(arr, SIZE);
	findAndPrintHighest(arr, SIZE);
	findAndPrintLowest(arr, SIZE);

	double average = findAndGetAverage(arr, SIZE);

	printDifferences(arr, SIZE, average);

	cout << endl;
	return 0;
}

void generateRandomNumbers(int arr[], int size)
{
	for (int i = 0; i < size; i++)
	{
		arr[i] = 1 + rand() % 100;
	}
}

void findAndPrintHighest(int arr[], int size)
{
	int highest = arr[0];
	int highestPos = 0;

	for (int i = 1; i < size; i++)
	{
		if (arr[i] > highest)
		{
			highest = arr[i];
			highestPos = i;
		}
	}

	cout << "Highest number in the array: " << highest << ", positioned at " << highestPos << endl;
}

void findAndPrintLowest(int arr[], int size)
{
	int lowest = arr[0];
	int lowestPos = 0;

	for (int i = 1; i < size; i++)
	{
		if (arr[i] < lowest)
		{
			lowest = arr[i];
			lowestPos = i;
		}
	}

	cout << "Lowest number in the array: " << lowest << ", positioned at " << lowestPos << endl;
}

double findAndGetAverage(int arr[], int size)
{
	double total = 0;

	for (int i = 0; i < size; i++)
	{
		total += arr[i];
	}

	return (total / size);
}

void printDifferences(int arr[], int size, double average)
{
	cout << "Average of the values in the array: " << average << endl;

	cout << "\nPosition \t Value \t Difference from the Average" << endl;
	for (int i = 0; i < size; i++)
	{
		cout << i << "\t\t " << arr[i] << "  \t\t " << (average - arr[i]) << endl;
	}
}
