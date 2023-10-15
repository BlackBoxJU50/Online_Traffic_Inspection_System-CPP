
#include <bits/stdc++.h>
#include <string>
#include <vector>

using namespace std;

string pas;
  bool valid_login = false;
namespace UniversityRecommendation
{
bool readUserCredentials(const  string& filename, const  string& username,   string& password)
{
    //pas=password;

    ifstream file(filename);
    if (file)
    {
        string line;
        while ( getline(file, line))
        {
            string::size_type pos = line.find(' ');
            if (pos !=  string::npos)
            {
                string user = line.substr(0, pos);
                string pass = line.substr(pos + 1);
                if (user == username)
                {
                    password =pass;
                    return true;
                }
            }
        }
    }
    file.close();
    return false;
}


class Sergent
{
protected:
    string username;
    string password;
public:
    Sergent() {}
    Sergent(const string& username, const string& password) : username(username), password(password) {}

    virtual ~Sergent() {}

    string getUsername() const
    {
        return username;
    }

    enum AuthenticateResult
    {
        AUTH_OK,
        AUTH_INVALID_USERNAME,
        AUTH_INVALID_PASSWORD
    };

    int authenticate(const string& passs) const
    {
        string correctPassword;
        if (readUserCredentials("users.txt", username, correctPassword)||passs==pas)

            if (passs == pas)
            {
                return 1;
            }
            else
            {
                return 2;
            }


    }
};
class Admin : public Sergent
{

public:
    Admin() {}
    Admin(const  string& username, const  string& password)
        : Sergent(username, password) {}

    virtual ~Admin() {}


    void* operator new(size_t size)
    {
        cout << "Admin object created" <<  endl;
        return ::operator new(size);
    }

    void operator delete(void* ptr)
    {
        cout << "Admin object deleted" <<  endl;
        ::operator delete(ptr);
    }
    friend void signup();
};
vector<Admin*> Admins;

void signup()
{
    string username, password;

    cout << "Enter a username: ";
    cin >> username;
    cout << "Enter a password: ";
    cin >> password;
    pas=password;

    Admins.push_back(new Admin(username, password));
    cout << "Signup successful." <<  endl;
}


void login()
{
    Sergent s1;
    string username, password;
    int attempts = 3;

    while (attempts > 0 && !valid_login)
    {
        cout << "Enter your username: ";
        cin >> username;
        cout << "Enter your password: ";
        cin >> password;
        int i=0;



       if( s1.authenticate(password)==1)
            {
                cout << "\n\tLogin successful." <<  endl;
                cout << "\n\tWelcome, " << username << "!" <<  endl;
                valid_login = true;
               // break;
            }


       if (!valid_login)
        {
            cout << "Incorrect username or password. " << attempts - 1 << " attempts left." << endl;
            attempts--;
        }
    }
}

}



// Define classes
class User {
public:
    User(string n, string e, string p) : name(n), email(e), password(p) {}

    string getName() {
        return name;
    }

    string getEmail() {
        return email;
    }

    string getPassword() {
        return password;
    }

private:
    string name;
    string email;
    string password;
};

class RegNumber {
private:
    string regNum;
public:
    RegNumber(string num) : regNum(num) {}
    bool operator ==(RegNumber r)
    {
        return regNum==r.regNum;
    }
    string getRegNum()const {
        return regNum;
    }


};

class Penalty {
public:
    Penalty(string d, int a) : description(d), amount(a) {}

    string getDescription() {
        return description;
    }

    int getAmount() {
        return amount;
    }

private:
    string description;
    int amount;
};

class Vehicle {
public:
    int year;
    RegNumber regNum;
    User* const owner;
    vector<Penalty> penalties;
public:
    // ...
   Vehicle(int yr, RegNumber r, User* o) : year(yr),regNum(r),owner(o)
   {

   }
    virtual ~Vehicle() {}

    virtual void printInfo() = 0;

    void addPenalty(Penalty p) {
        penalties.push_back(p);
    }

    RegNumber getRegNumber() const {  // Marking this function as const
        return regNum;
    }

    User* getOwner() const {  // Marking this function as const
        return owner;
    }

    bool operator==(const RegNumber &other) const {
        return regNum.getRegNum() == other.getRegNum();
    }

    // Define operator+ to add a penalty to a vehicle
    Vehicle& operator+(Penalty p) {
    addPenalty(p);
    return *this;
}

};



class Car : public Vehicle {
public:
    Car(int yr, RegNumber r, User* o, int nd) :
        Vehicle(yr, r, o), numDoors(nd) {}

    void printInfo() {
        cout << "Registration number: " << regNum.getRegNum() << endl;
        cout << "Year: " << year << endl;
        cout << "Number of doors: " << numDoors << endl;
        cout << "Owner's name: " << owner->getName() << endl;
        cout << "Owner's email: " << owner->getEmail() << endl;
        cout << "Owner's password: " << owner->getPassword() << endl;
        cout << "Penalties: " << endl;
        for (Penalty p : penalties) {
            cout << "- " << p.getDescription() << " (" << p.getAmount() << ")" << endl;
        }
    }

private:
    int numDoors;
};

class Motorcycle : public Vehicle {
public:
    Motorcycle(int yr, RegNumber r, User* o, int es) :
        Vehicle(yr, r, o), engineSize(es) {}

    void printInfo() {
        cout << "Registration number: " << regNum.getRegNum() << endl;
        cout << "Year: " << year << endl;
        cout << "Engine size: " << engineSize << " cc" << endl;
        cout << "Owner's name: " << owner->getName() << endl;
        cout << "Owner's email: " << owner->getEmail() << endl;
        cout << "Owner's password: " << owner->getPassword() << endl;
        cout << "Penalties: " << endl;
        for (Penalty p : penalties) {
            cout << "- " << p.getDescription() << " (" << p.getAmount() << ")" << endl;
        }
    }

private:
    int engineSize;
};

int main() {

cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------"<<endl;
cout<<"|///////////////////////////////////////////////////////////////////////////////////////////////////////////////|"<<endl;
cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n"<<endl;

cout<<"\n\n\n           **********----WELLCOME TO RAPID TRAFFIC INSPECTION SYSTEM----***********\n\n\n"<<endl;

    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------"<<endl;
    cout<<"|///////////////////////////////////////////////////////////////////////////////////////////////////////////////|"<<endl;
cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n\n"<<endl;
system("Pause");
    system("cls");
    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------"<<endl;
    cout<<"|///////////////////////////////////////////////////////////////////////////////////////////////////////////////|"<<endl;
cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n\n"<<endl;
cout<<"\t\n ********____ HELLO SERGENT ____ \n\n ******______ At First you have to sign up if you have no account otherwise you have to Login ____********** "<<endl;

int choice;
    do
    {
       system("cls");

         cout<<"\n-----------*--------------*----------------*--------------*-----------------*------------------*-----------------"<<endl;
         cout<<"|///////////////////////////////////////////////////////////////////////////////////////////////////////////////|"<<endl;
cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n\n"<<endl;
        cout<<"\n\tEnter your Choice \n"<<endl;
        cout << "\t1. Signup As a SERGENT\a\n\n" <<  endl;
        cout << "\t2. Login As a SERGENT \a\n\n" <<  endl;
        cout << "\t3. Exit\a\n\n" <<  endl;
        cout << "Enter your choice: ";
        cin >> choice;
        switch (choice)
        {
        case 1:
            UniversityRecommendation::signup();
            break;
        case 2:
            UniversityRecommendation::login();
            break;
        case 3:
            cout << "Goodbye!" <<  endl;
            break;
        default:
            cout << "Invalid choice." <<  endl;

        }
    }
    while (choice !=2&&choice!=3);

if(!valid_login)
{
    return 0;
}

system("Pause");
    system("cls");
    // Create users
    User user1("HASIB", "hasib@gmail.com", "123");
    User user2("Bob", "bob@example.com", "password456");

    // Create vehicles
    Car car1(2010, RegNumber("ABC123"), &user1, 4);
    Motorcycle bike1(2015, RegNumber("XYZ789"), &user2, 500);
    int k;
    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n"<<endl;
    cout<<"|///////////////////////////////////////////////////////////////////////////////////////////////////////////////|"<<endl;
    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n"<<endl;
    cout<<"\nWhich Kind of Vehicle??\n\n 1.CAR\n\n 2.MOTORBIKE \n\n"<<endl;
    cin>>k;
    system("Pause");
    system("cls");
    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n"<<endl;
    cout<<"|///////////////////////////////////////////////////////////////////////////////////////////////////////////////|"<<endl;
    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n"<<endl;
    if(k==1)
    {
    cout<<"\t\t GIVE THE INFORMATION OF THE CAR "<<endl;

    }
    else
    {
       cout<<"\t\t GIVE THE INFORMATION OF THE MOTORBIKE "<<endl;
    }


    // Log in
    string email, password;
    cout << "\n\t Enter Owner's email: ";
    cin >> email;
    cout<<endl;
    cout << "\n\tEnter Owner's password: ";
    cin >> password;
    cout<<endl;

    User* currentUser = nullptr;
    if (email == user1.getEmail() && password == user1.getPassword()) {
        currentUser = &user1;
    } else if (email == user2.getEmail() && password == user2.getPassword()) {
        currentUser = &user2;
    } else {
        cout << "\n\tInvalid email or password.\n" << endl;
        return 1;
    }

    // Input registration number
    string regNumStr;
    cout << "\n\t Enter Vehicle's registration number: ";
    cin >> regNumStr;

    RegNumber regNum(regNumStr);

    // Check if vehicle with given registration number exists
    Vehicle* vehicle = nullptr;
    if (car1 == regNum) {
        vehicle = &car1;
        vehicle->printInfo();
    } else if (bike1 == regNum) {
        vehicle = &bike1;
        vehicle->printInfo();
    } else {
        cout << "Vehicle not found." << endl;
        return 1;
    }
    system("Pause");
    system("cls");
    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n"<<endl;
    cout<<"|///////////////////////////////////////////////////////////////////////////////////////////////////////////////|"<<endl;
    cout<<"-----------*--------------*----------------*--------------*-----------------*------------------*-----------------\n"<<endl;
int m;
cout<<"\t Panalty with cause : \n 1.Red Light Violation. \n 2.Speeding Ticket \n 3.Invalid License\n"<<endl;
cin>>m;
if(m==1)
    {


    // Update penalty section
    int penaltyAmount;
    string penaltyDescription="Red Light Violation.";
    cout << "\n\tEnter penalty amount: ";
    cin >> penaltyAmount;
    cout << "\n\tPenalty description: "<<penaltyDescription<<endl;


    Penalty penalty(penaltyDescription, penaltyAmount);
    *vehicle + penalty;

    // Print updated vehicle info
    cout << "\n\tUpdated vehicle info:\n" << endl;
    vehicle->printInfo();

    }
    else if(m==2)
    {
       int penaltyAmount;
    string penaltyDescription="Speeding Ticket.";
    cout << "\n\tEnter penalty amount: ";
    cin >> penaltyAmount;
    cout << "\n\tPenalty description: "<<penaltyDescription<<endl;


    Penalty penalty(penaltyDescription, penaltyAmount);
    *vehicle + penalty;

    // Print updated vehicle info
    cout << "\n\tUpdated vehicle info:\n" << endl;
    vehicle->printInfo();
    }
    else
    {
        int penaltyAmount;
    string penaltyDescription="Invalid License.";
    cout << "\n\tEnter penalty amount: ";
    cin >> penaltyAmount;
    cout << "\n\tPenalty description: "<<penaltyDescription<<endl;


    Penalty penalty(penaltyDescription, penaltyAmount);
    *vehicle + penalty;

    // Print updated vehicle info
    cout << "\n\tUpdated vehicle info:\n" << endl;
    vehicle->printInfo();
    }



    return 0;
}

