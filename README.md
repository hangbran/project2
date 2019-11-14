# project2

#include <iostream>
#include <fstream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int main() {

    //delcaring all variables
    string user_input, common, file_input;
    vector<string> vect;
    int user_size, file_size, vect_size, ocurrence, difference = 0;
    int min_ocurence = 9999;
    ifstream file;

    //promting user for password and opening file
    cout << "Give me a password:" << endl;
    cin >> user_input;
    file.open("common_passwords.txt");
    cout << "You provided a password of " << user_input << endl;
    cout << "The most similar passwords to " << user_input << " are: " << endl;

    //intiating sizes and substrings and vector
    user_size = user_input.size();
    
    //adds the user password
    // vect.push_back(user_input);

   

    //runs through the input file to compare all common passwords
    while(file >> file_input) {
        // getline(file, file_input);
        ocurrence = 0;
        //for loop with multiple conditions
        //https://www.sololearn.com/Discuss/1330194/multiple-conditions-in-for-loop-c
        file_size = file_input.size();
        for(int x = 0; x < file_size && x < user_size; x++) {
            if (user_input[x] == file_input[x]) {
                ocurrence++;
            }
        }
       
        // ocurrence = file_size - ocurrence;
        if(file_size >= user_size) {
            difference = file_size - ocurrence;
        }
        
        if(file_size <= user_size) {
            difference = user_size - ocurrence;
        }
        
        //prints password if similar enough
        if (difference <= min_ocurence) {
            if (min_ocurence > difference){
                min_ocurence = difference;
                
            }
            vect.push_back(file_input);

        }

    }

   file.close();
   
   //sorts all passwords
   sort(vect.begin(), vect.end());
   vect_size = vect.size();
   
   for (int x = 0; x < vect_size; x++) {
       
       ocurrence = 0;
       int vector_sizes = vect.at(x).size(); 
        
        for(int y = 0; y < vector_sizes; y++) {
            if (user_input[y] == (vect.at(x)).at(y)) {
                ocurrence++;
            }
        }
        
        difference = vect.at(x).size() - ocurrence;
        if (difference == min_ocurence && vect.at(x).size() < user_input.size()){
            difference = user_input.size() - vect.at(x).size() + ocurrence;
        }
        
        // cout << vect.at(x) << " " << difference  << " " << min_ocurence<< endl;
    
        if(difference <= min_ocurence){
            // cout << vect.at(x) << " " << difference  << " " << min_ocurence<< endl;

            cout << vect.at(x) << ", ";
        }
        

    }
   cout << endl;
   cout << "All of which are " << min_ocurence << " character(s) different." << endl;

}
