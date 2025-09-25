#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
#include <cctype>
using namespace std;

// Define a class called Bag
class Bag {
public:
    string collection;         // name of the collection
    vector<string> items;      // vector that stores all items
    int numOfItems;            // number of items stored

    // Constructor that takes a vector of strings and initializes items and numOfItems
    Bag(vector<string> listOfItems){
        items = listOfItems;                                 // copy the list into items
        numOfItems = static_cast<int>(listOfItems.size());   // store how many items
    }

    // Display all items in the vector
    void displayAll() {
        
        for(int i = 0; i < items.size(); i++){
            cout << items[i] << endl;
        }
    }

    // search function
    string search(){
        string input;  // will hold the user input
        cout << "-------------------\n""------------------\n""| Search: |\n""-------------------\n""------------------\n";
        displayAll();
        getline(cin, input);    // get user input as the search term
        cout << "-------------------\n""------------------\n""| Search: " << input <<"|\n""-------------------\n""------------------\n";

        // if statement to see how many characters the user puts, if the input is less than 3 characters, just display everything again
        if (input.size() < 3){
            displayAll();
        }
        else {
            for(int i = 0; i < items.size(); i++){ // check if input matches the beginning of each item
                if (input == items[i].substr(0, input.size())){
                    cout << items[i] + "\n";
                }
            }
            
        }
        
        return input;  // return the user’s search string
    }
    
};

int main(){
    // create a vector of Knicks players
    vector<string> players = {"Jalen Brunson", "Julius Randle", "OG Anunoby", "Donte DiVincenzo", "Mitchell Robinson", "Josh Hart", "Miles McBride", "Bojan Bogdanovic",
        "Precious Achiuwa", "Alec Burks", "Jericho Sims", "Charlie Brown Jr.",
        "Patrick Ewing", "Walt Frazier", "Allan Houston", "John Starks",
        "Latrell Sprewell", "Iman Shumpert", "Amar'e Stoudemire",
        "Carmelo Anthony", "Kristaps Porzingis", "Moses Brown"};

    Bag b = Bag(players);         // create a Bag object containing the players
    string searchResult = b.search();  // call search and store the result
}
