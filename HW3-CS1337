

#include <iostream>
#include <vector>
#include <cstdlib>
#include <ctime>
#include <algorithm>

using namespace std;

// Function to display the contents, size, and capacity of a vector
void showVector(const string& header, const vector<int>& vec) {
    cout << header << " - Size: " << vec.size() << ", Capacity: " << vec.capacity() << "\n";
    for (int num : vec) {
        cout << num << " ";
    }
    cout << "\n";
    // Debug: cout << "Displayed vector: " << header << "\n"; // Uncomment to debug
}

// Bubble sort algorithm implementation for sorting vector elements
void bubbleSort(vector<int>& vec) {
    bool swapped;
    do {
        swapped = false;
        // Traverse through all elements
        for (size_t i = 1; i < vec.size(); i++) {
            // Debug: cout << "Comparing: " << vec[i-1] << " and " << vec[i] << "\n"; // Uncomment to debug
            if (vec[i - 1] > vec[i]) {
                swap(vec[i - 1], vec[i]);
                swapped = true;
                // Debug: cout << "Swapped: " << vec[i-1] << " with " << vec[i] << "\n"; // Uncomment to debug
            }
        }
        // Continue until no swaps are needed
    } while (swapped);
    // Debug: cout << "Bubble sort completed.\n"; // Uncomment to debug
}

// Performs binary search on the vector to find a number and count its occurrences
int binarySearchAndCount(const vector<int>& vec, int number, int& count) {
    int low = 0, high = vec.size() - 1, mid;
    bool found = false;
    
    // Binary search algorithm
    while (low <= high) {
        mid = low + (high - low) / 2;
        // Debug: cout << "Searching... Mid: " << mid << ", Number: " << vec[mid] << "\n"; // Uncomment to debug
        if (vec[mid] == number) {
            found = true;
            count = 1; // Initial count for the found number
            int left = mid - 1; // Count occurrences to the left of the mid point
            
            while (left >= 0 && vec[left] == number) {
                count++;
                left--;
            }
            
            int right = mid + 1;
            while (right < vec.size() && vec[right] == number) {
                count++;
                right++;
            }
            return mid; // Return the index of one occurrence of the number
        } else if (vec[mid] < number) {
            low = mid + 1; // Adjust search to the right half
        } else {
            high = mid - 1; // Adjust search to the left half
        }
    }
    // If number was not found, set count to 0
    if (!found) {
        count = 0;
    }
    return -1; // Indicate number not found
    // Debug: cout << "Binary search completed. Found: " << found << "\n"; // Uncomment to debug
}
// Removes duplicate elements from a sorted vector
void removeDuplicates(vector<int>& vec) {
    vector<int> temp; // Temporary vector to hold unique elements
    for (size_t i = 0; i < vec.size(); i++) {
        // Add the first element and any element that is not a duplicate
        if (i == 0 || vec[i] != vec[i - 1]) {
            temp.push_back(vec[i]);
        }
    }
    vec = temp; // Copy the unique elements back to the original vector
    // Debug: cout << "Duplicates removed.\n"; // Uncomment to debug
}

void fillVectorWithRandomNumbers(vector<int>& vec, int numNumbers, int maxNumber) {
    //filling the vector with random numbers
    for (int& num : vec) {
        num = rand() % (maxNumber + 1);
        // Debug: cout << "Generated random number: " << num << "\n"; // Uncomment to debug
    }
}

void performSearches(const vector<int>& vec) {
    for (int i = 0; i < 5; ++i) {
        int searchNum, count;
        cout << "Enter a number to search for: ";
        cin >> searchNum;
        
        // Perform searches and count occurrences of input numbers
        int index = binarySearchAndCount(vec, searchNum, count);
        if (index != -1) {
            cout << "Number " << searchNum << " found at index " << index << ", Count: " << count << "\n";
        } else {
            cout << "Number " << searchNum << " not found.\n";
        }
        // Debug: cout << "Search completed for number: " << searchNum << "\n"; // Uncomment to debug
    }
}

void getInput(int& numNumbers, int& maxNumber) {
    //Ensuring the max number does not exceed 20 for 
    cout << "Enter the number of random numbers to generate (suggest 30-40): ";
    cin >> numNumbers;

    do {
        cout << "Enter the maximum size for random numbers (no larger than 20): ";
        cin >> maxNumber;
    } while (maxNumber > 20);
    // Debug: cout << "Input received. numNumbers: " << numNumbers << ", maxNumber: " << maxNumber << "\n"; // Uncomment to debug
}

int main() {
    srand(static_cast<unsigned>(time(0))); //seed for random numbers
    // Debug: cout << "Random seed initialized.\n"; // Uncomment to debug
    
    int numNumbers, maxNumber;
    getInput(numNumbers, maxNumber);

    vector<int> vec1(numNumbers);
    fillVectorWithRandomNumbers(vec1, numNumbers, maxNumber);

    showVector("Unsorted vector", vec1);

    vector<int> vec2(vec1); // Make a copy of vec1 to sort with bubble sort
    sort(vec1.begin(), vec1.end());
    showVector("Sorted vector (vec1)", vec1);

    bubbleSort(vec2);
    showVector("Sorted vector (vec2)", vec2);

    performSearches(vec1);

    removeDuplicates(vec1);
    showVector("Vector after removing duplicates", vec1);

    return 0;
}

