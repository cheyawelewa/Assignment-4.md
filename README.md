# Assignment-4.md

 #include <iostream>  
 #include <unordered_map>  
 #include <vector>  
   
 using namespace std;  
   
 // Function to build the hash table from the array  
 unordered_map<int, int> buildHashTable(const vector<int>& array) {  
     unordered_map<int, int> hashTable;  
     for (size_t i = 0; i < array.size(); i++) {  
         hashTable[array[i]] = i;  
     }  
     return hashTable;  
 }  
   
 // Function to perform O(1) search using the hash table  
 void constantTimeSearch(const unordered_map<int, int>& hashTable, int value) {  
     if (hashTable.find(value) != hashTable.end()) {  
         cout << "Found " << value << " at index " << hashTable.at(value) << endl;  
     } else {  
         cout << value << " not found in the array" << endl;  
     }  
 }  
   
 int main() {  
     // Original array  
     vector<int> array = {200, 400, 100, 50, 350};  
   
     // Build the hash table for constant time lookup  
     unordered_map<int, int> hashTable = buildHashTable(array);  
   
     // Display the original array  
     cout << "Original array: ";  
     for (int value : array) {  
         cout << value << " ";  
     }  
     cout << endl;  
   
     // Search for some values  
     cout << "\nSearch results:" << endl;  
     constantTimeSearch(hashTable, 100);   // Should find it  
     constantTimeSearch(hashTable, 200);   // Should find it  
     constantTimeSearch(hashTable, 999);   // Should not find it  
   
     return 0;  
 }  


2.

 #include <iostream>  
 #include <string>  
 #include <functional>  
   
 using namespace std;  
   
 int main() {  
     // Name to be hashed  
     string name = "Cheyenne";  
   
     // Use std::hash to generate the hash value of the string  
     hash<string> hashFn;  
     size_t hashValue = hashFn(name);  
   
     cout << "The hash value of \"" << name << "\" is: " << hashValue << endl;  
   
     return 0;  
 }  


3.

If we use an open address in hash tables, deletion can cause a distruption in the probe sequence. A tombstone is used to avoid breaking the chain of probes and to mark deleted cells. The main issue with tombstones is that they accumulate overtime. This can degrade the performance sinc ethe search and insertaion operations will scan over tombstones and will reduce the efficiency. 

