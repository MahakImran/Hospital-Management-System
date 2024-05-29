#include <iostream>
#include <conio.h>
#include <string>
#include <windows.h>
#include <ctime>
using namespace std;
/* run this program using the console pauser or add your own getch, system("pause") or input loop */
class hospital_login{
public:
    int userid;
    string username;
    string password;
    string confirmpassword;
    string email;
    string user;
    string a;
    string purchasername;
    string purchaserid;
};
class signing_up : public hospital_login  {
public:
    int sign_up() {
        cout << "enter user name :" << endl;
        cin >> username;
        cout << "enter password :" << endl;
        for (int i = 0; i < 1000; i++) {
            char c = _getch();
            if (c == '\r')
                break;
            cout << "*";
            password += c;
        }
        cout << endl;
        cout << "please confirm your password :" << endl;
        for (int i = 0; i < 1000; i++) {
            char c = _getch();
            if (c == '\r')
                break;
            cout << "*";
            confirmpassword += c;
        }
        cout << endl;
        cout << "enter email" << endl;
        cin >> email;
        if (password == confirmpassword) {
            cout << "              signed up" << endl;
            return 1;
        } else {
            cout << "passwords donot match please retry" << endl;
            return 0;
        }
    }
};
class login : public signing_up  {
public:
    int input() {
        cout << "enter username :" << endl;
        cin >> user;
        cout << "enter password :" << endl;
        for (int i = 0; i < 1000; i++) {
            char c = _getch();
            if (c == '\r')
                break;
            cout << "*";
            a += c;
        }
       if (user == username &&a == password){
	 cout << "successful insertion" << endl;
            return 4;  }
			else if( user == "aneesa"&&a == "aneesa11" ){
            	cout << "successful insertion"<<endl;
            return 1;
			} else if( user == "sana" && a == "sa2na"){
            cout << "successful insertion" << endl;
            return 1;
        } 
		 else if (user=="doctor"&&a=="doctor12"){
		  cout << "successful insertion" << endl;
            return 2;
		 }
		 else if(user=="admin"&&a=="admin1212"){
		 	  cout << "successful insertion" << endl;
            return 3;
		 }
		 else {
            cout << "wrong password" << endl;
            return 0;
        }
    }
};
class Appointment{
	public:
		string name;
		int age;
		int cnic;
		string gender;
		string symptom;
		string time;
		string date;
	void addAptDetails(){
		cout<<"enter the name of the patient "<<endl;
		cin>>name;
		cout<<"enter cnic of the patient"<<endl;
		cin>>cnic;
		cout<<"enter the age of the patient "<<endl;
		cin>>age;
		cout<<"enter the gender of the patient "<<endl;
		cin>>gender;
		cout<<"enter the symptoms of the patient "<<endl;
		cin>>symptom;
		cout<<"enter the date for the appointment "<<endl;
		cin>>date;
		cout<<"enter the time for the appointment "<<endl;
		cin>>time;
	}};
struct qNode{
Appointment a1;
	qNode*next;
};
class queue{
	public:
		qNode*rear;
		qNode*front;
		queue(){
			front=NULL;
			rear=NULL;
		}
			void insert(string n,int a,int c,string g,string s,string t,string d){
			qNode*temp=new qNode;
			temp->a1.name=n;
		temp->a1.age=a;
		temp->a1.cnic=c;
		temp->a1.gender=g;
		temp->a1.symptom=s;
		temp->a1.time=t;
		temp->a1.date=d;
			temp->next=NULL;
			if(front == NULL){
				rear=temp;
				front=temp;
			}
			else{
			rear->next=temp;
				rear=temp;
			}
		}
		
		void enqueue(){
			qNode*temp=new qNode;
			temp->a1.addAptDetails();
			temp->next=NULL;
			if(front == NULL){
				rear=temp;
				front=temp;
			}
			else{
			rear->next=temp;
				rear=temp;
			}
		}
string dequeue(){
		qNode*temp=front;
			string f;
			f=front->a1.name;
			qNode*t=front;
			front=front->next;
			delete t;
			return f;		
		}
    int display() {
        qNode* temp = front;
        while (temp != NULL) {
		cout<<"Name: "<<temp->a1.name<<endl;
		cout<<"Age: "<<temp->a1.age<<endl;
		cout<<"Gender: "<<temp->a1.gender<<endl;
		cout<<"symptom: "<<temp->a1.symptom<<endl;
		cout<<"CNIC: "<<temp->a1.cnic<<"\tDate: "
		<<temp->a1.date<<"\tTime: "<<temp->a1.time<<endl;
            temp = temp->next;
        }
    
    }
};
struct tnode{
  	string name,gender,symptom;
	int age,mob_no;
	long cnic;
	tnode*left;
	tnode*right;
};
class tree{
public:
 tnode*root;
	tree(){
		root=NULL;
	}
	tnode*insert(tnode*temp,string n,string g,string s,int a,int m,long c){
	    if (temp==NULL){	 
		 temp=new tnode;
	     temp->name=n;
		 temp->gender=g;
		 temp->symptom=s;
	     temp->age=a;
	     temp->mob_no=m;
         temp->cnic=c;
	     temp->left =NULL;
		 temp->right=NULL;
		 if(root==NULL){
		   root=temp;}		
}      else if (temp->cnic>c) {
	temp->left=insert(temp->left,n,g,s,a,m,c);
	}
	 else  {
	 	
	 temp->right=insert(temp->right,n,g,s,a,m,c);
	}
	return temp;
	}
	void indisplay(tnode*temp){
		if(temp!=NULL){
		indisplay(temp->left);
		cout<<"Name of the patient :"<<temp->name<<endl;
		cout<<"Cnic no:"<<temp->cnic<<endl;
		cout<<"Age of the patient :"<<temp->age<<endl;
		cout<<"Gender of the patient :"<<temp->gender<<endl;
		cout<<"Mobile number"<<temp->mob_no<<endl;
		cout<<"Symptoms of the patient \n"<<temp->symptom<<endl;
		indisplay(temp->right);
		}
	}
	void search(tnode*temp,int d){
		if(temp!=NULL){
			if(temp->cnic==d){
				cout<<"Name of the patient :"<<temp->name<<endl;
		cout<<"Cnic no:"<<temp->cnic<<endl;
		cout<<"Age of the patient :"<<temp->age<<endl;
		cout<<"Gender of the patient :"<<temp->gender<<endl;
		cout<<"Mobile number"<<temp->mob_no<<endl;
		cout<<"Symptoms of the patient "<<temp->symptom<<endl;
			}
			else if(temp->cnic>d){
				search(temp->left,d);
			}
			else if(temp->cnic<d){
				search(temp->right,d);
			}
	}}
void update(tnode* temp, int d) {
        if (temp != NULL) {
            if (d == temp->cnic) {
                string x;
                cout << "Please select what data you want to update" << endl;
                cout << "Name of the patient press \"n\"\nCNIC of the patient press \"c\"\n "
                    << "Age of the patient press \"a\"\nMobile number press \"m\"\n"
                    << "Symptoms of the patient press \"s\"\n"
                    << endl;
                cin >> x;
                if (x == "n") {
                    string n;
                    cout << "Enter updated new name: ";
                    cin >> n;
                    temp->name = n;
                } else if (x == "c") {
                    int c;
                    cout << "Enter updated CNIC: ";
                    cin >> c;
                    temp->cnic = c;
                } else if (x == "a") {
                    int a;
                    cout << "Enter updated age: ";
                    cin >> a;
                    temp->age = a;
                } else if (x == "m") {
                    int m;
                    cout << "Enter updated mobile: ";
                    cin >> m;
                    temp->mob_no = m;
                } else if (x == "s") {
                    string s;
                    cout << "Enter new symptoms: ";
                    cin >> s;
                    temp->symptom = s;
                } else {
                    cout << "No such option" << endl;
                }
            } else if (temp->cnic > d) {
                update(temp->left, d);
            } else if (temp->cnic < d) {
                update(temp->right, d);
            }
        } else {
            cout << "No such CNIC in the system" << endl;
        }
    }
};
struct node{
	int dosage;
	string med_name;
	int duration;
	int frequency;
	node *ptr;
};
class prescription{
	node *head;
	node *tail;
	public:
		prescription(){
			head=NULL;
			tail=NULL;
		}
	// creating prescription
		void addmedication(){
			node *temp=new node;
			cout<<"enter medication\n";
			cin>>temp->med_name;
			cout<<"enter dosage(in mg)\n";
			cin>>temp->dosage;
			cout<<"enter frequency(how many times a day medicine will be taken)\n";
			cin>>temp->frequency;
			cout<<"enter duration(how many days medicine will be taken)\n";
			cin>>temp->duration;
			temp->ptr=NULL;
			if (head==NULL){
				head=temp;
				tail=temp;
			}
			else
			tail->ptr=temp;
			tail=temp;
		}
	// displaying prescription
		void displayprescription(){
			node *temp=head;
			while (temp!=NULL){
				cout<<"Medication: "<<temp->med_name<<endl;
				cout<<"Dosage: "<<temp->dosage<<"mg "<<endl;
				cout<<"Frequency: "<<temp->frequency<<" times a day "<<endl;
				cout<<"Duration: "<<temp->duration<<" days "<<endl;
				temp=temp->ptr;
			}
		}	
};
int main(int argc, char** argv){
cout<<" ______________________________________________"<<endl;
cout<<"|                                              |"<<endl;
cout<<"|            E-HOSPITAL MANAGEMENT             |"<<endl;
cout<<"|______________________________________________|\n"<<endl;
cout<<"                  LOGIN  OR SIGNUP  "<<endl;
cout<<"      --------------------------------"<<endl;
  tree t1;
  t1.insert(t1.root,"hamna","female","headache\tfever",21,49356,42201681);
  t1.insert(t1.root,"aneesa","female","fever",20,34603,346036583);
  t1.insert(t1.root,"samiullah","male","vomit\tcough\tflu",7,35748,87868);
  t1.insert(t1.root,"hamza","male","swelling\tskin rash",22,96983,354762);
  t1.insert(t1.root,"abdullah","male","spain in body",36,12346,6543221);
   t1.insert(t1.root,"mudha","female","sore throat",17,96765,23768);
  t1.insert(t1.root,"hafsa","female","swelling\tskin rash",48,63747,2352568);
  queue q1;
  q1.insert("hamna",21,2345634,"female","fever","12:00 pm","12/01/2024");
  q1.insert("aqsa",24,4657832,"female","hepatitus","01:00 pm","12/01/2024");
  q1.insert("mahak",17,6544788,"female","cough","02:00 pm","12/01/2024");
  q1.insert("fatima",27,4732788,"female","cough\tflu","12:00 pm","13/01/2024");
  q1.insert("samiullah",18,876534,"female","fever","01:00 pm","13/01/2024");
  q1.insert("fiza",45,4567975,"female","skin rash","02:00 pm","13/01/2024");
  prescription p1;
   cout << "please press \"s\" for signing up into the account \nif you already have an account press \"l\" for login"
         << endl;
    string x;
    login li;
    int n;
    cin >> x;
    if (x == "s") {
        n = li.sign_up();
        if (n == 1) {
            n = li.input();
            if (n == 4) {
             long a;
			cout<<"please select optoin"<<endl;
		cout<<"\n\"m\"to make appointment\n\"\"s\"to search\"u\"to update";
		string b;
		cin>>b;
		if(b=="m"){
    time_t currentTime = time(NULL);
   string currentTimeStr = ctime(&currentTime);
    cout << "         " << currentTimeStr;

		 q1.enqueue();
		 q1.display();}
		 else if(b=="s"){
		 	cout<<"enter cnic to search"<<endl;
		 	cin>>a;
		 t1.search(t1.root,a);}
		 else if(b=="u"){
		 	cin>>a;
		 	t1.update(t1.root,a);
		 }
            }
     }
}
else if(x=="l"){
	n=li.input();
	if(n==1){
			cout<<"please select optoin"<<endl;
		cout<<"\n\"m\"to make appointment\n\"\"s\"to search\"u\"to update";
		string b;
		cin>>b;
		long a;
		if(b=="m"){
    time_t currentTime = time(NULL);
    string currentTimeStr = ctime(&currentTime);
    cout << "            " << currentTimeStr<<endl;

		 q1.enqueue();
		 q1.display();
		 }
		 else if(b=="s"){
		 	cout<<"enter cnic to search"<<endl;
		 	cin>>a;
		 t1.search(t1.root,a);}
		 else if(b=="u"){
		 	cout<<"enter cnic to update"<<endl;
		 	cin>>a;
		 	t1.update(t1.root,a);
		 }
	}
	else if(n==2) {
		cout<<"please select optoin"<<endl;
		cout<<"\n\"d\"to see all patient\n\"m\"for medicine prescription";
		string b;
		cin>>b;
		if(b=="d"){
			t1.indisplay(t1.root);
		}
		if(b=="m"){
			int a;
			cout<<"enter cnic to search"<<endl;
			cin>>a;
		t1.search(t1.root,a);
			int n;
    cout<<"how many medicines are you going to suggest\n";
    cin>>n;
    for (int i=0;i<n;i++) {
        p1.addmedication();
    }
    p1.displayprescription();
		}
	}
	else if(n==3){
		cout<<"please select optoin"<<endl;
		cout<<"\n\"d\"to see all patient details\n\"s\"to search patient\n\"a\"to see appointments";
		string b;
		cin>>b;
		if(b=="d"){
		t1.indisplay(t1.root);}
		if(b=="s"){
		int a;
		cout<<"enter to search"<<endl;
		cin>>a;
		t1.search(t1.root,a);
	}
	if(b=="a"){
		q1.display();
		cout<<"do you want to send message to person having appoint first"<<endl;
		string z;
		cin>>z;
		if(z=="yes"){
			string d;
			d=q1.dequeue();
			cout<<"message sended to "<<d<<endl;
			cout<<"do you want to send message to person having appoint first"<<endl;
			cin>>z;
			if(z=="yes"){
				d=q1.dequeue();
			cout<<"message sended to "<<d<<endl;
			}
			
		}else{
			cout<<"thank you!"<<endl;
		}
	}}
	}
	else{
		cout<<"no such option"<<endl;
	}
return 0;
}
