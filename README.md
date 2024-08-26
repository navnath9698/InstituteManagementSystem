#include<iostream>
#include<string.h>
#define MAX_STUDENTS 100
#define MAX_COURSES 10
#define MAX_TRAINERS 5
#define MAX_Developing 6
#define MAX_AddAdmin 10
using namespace std;
int i;
struct Student
{
	int id,age;
	string name,Address,city;
};
struct courseDetails
{
	string courseID,courseName;
	int courseFees;
	float courseDuration;
};
struct trainingDepartment
{
	float salary;
    string id,name,designation;
};
struct developingDepartment
{
    string id,name,designation,project,technology;
    float salary;
};
struct addAdminDepartment
{
	string id,name,role;
	float salary;
};
struct Student students[MAX_STUDENTS];
int numStudents=0;
void addStudent();
void displayStudent();
void searchStudent();
void updateStudent();
void updateById();
void updateByName();
void updateByCourse();
void updateByCity();
void updateByAddress();

struct courseDetails newCourse[MAX_COURSES];
int numCourses=0;
void addCourse();
void displayCourse();
void searchCourse();
void searchCourseById();
void searchCourseByName();
void deleteCourseById();
void updateCourse();

struct trainingDepartment newTrainer[MAX_TRAINERS];
int numTrainers=0;
void training();
void addTrainers();
void displayTrainers();
void searchTrainers();
void deleteTrainers();

struct developingDepartment newDevelopers[MAX_Developing];
void developing();
int numDevelopers=0;
void addDeveloping();
void displayDeveloping();
void searchDeveloping();
void deleteDeveloping();
void admin();

struct addAdminDepartment newaddAdmin[MAX_AddAdmin];
int numaddAdmin=0;
void addAdmin();
void displayAdmin();
void searchAdmin();
void deleteAdmin();

void reportDetails();

int main()
{
	int choice;
	do
	{
		cout<<"Welcome to Code IT institute"<<endl;
		cout<<"1.Student INFO System"<<endl;
		cout<<"2.Course INFO System"<<endl;
		cout<<"3.Department Info System"<<endl;	
		cout<<"4.Report Details"<<endl;	
		cout<<"5.exit"<<endl;
		cout<<"Enter Your Choice:-";
		cin>>choice;
		system("clear"); 
		switch(choice)
		{
			case 1:
				int ch;
				do
				{
					cout<<"Welcome to Code IT institute"<<endl<<endl;
					cout<<"1.Student INFO System"<<endl;
					cout<<"\t1.Add Student Details"<<endl;
					cout<<"\t2.Display All Student Details"<<endl;
					cout<<"\t3.Search Student Details"<<endl;
					cout<<"\t4. Update Student Details"<<endl;
					cout<<"\t5.exit"<<endl;
					cout<<"Enter Your Choice:-";
					cin>>ch;
				
					switch(ch)
					{
						case 1:
							addStudent();
							break;
						case 2:
							displayStudent();
							break;
						case 3:
							searchStudent();
							break;
						case 4:
							updateStudent();
							break;
						case 5:
							cout<<"Exit...";
							break;
						default:
							cout<<"Invalid Choice";
							
					}
				}while(ch!=5);
				break;
			case 2:
				int choice;
				do
				{
					cout<<"Welcome to Code IT institute"<<endl<<endl;
					cout<<"Course Details are"<<endl;
					cout<<"\t1.Addcourse"<<endl;
					cout<<"\t2.displaycourse"<<endl;
					cout<<"\t3.searchcourse"<<endl;
					cout<<"\t4.deletecourse"<<endl;
					cout<<"\t5.updatecourse"<<endl;
					cout<<"\t6.exit"<<endl;
					cout<<"Enter the choice:-";
					cin>>choice;
					system("clear");
					switch(choice)
					{
						case 1:
							addCourse();
						break;
						case 2:
							displayCourse();
						break;
						case 3:
							searchCourse();
						break;
						case 4:
							deleteCourseById();
						break;
						case 5:
		//					updateCourse();
						break;
						case 6:
							cout<<"Exiting the line"<<endl;
							break;
						break;
						default:
						cout<<"invalid choice";
						break;
					}
						
			}while(choice!=6);
			break;			
 			case 3:
				int cho;
				do
				{
					cout<<"Welcome to Code IT institute"<<endl<<endl;
					cout<<"Department Details are"<<endl;
					cout<<"\t1.Training Department"<<endl;
					cout<<"\t2.Developing Department"<<endl;
					cout<<"\t3.Admin Department"<<endl;
					cout<<"Enter the choice:-";
					cin>>cho;
					system("cls");
					switch(cho)
					{
					
						case 1:
							training();
						    break;
						case 2:
							developing();
						    break;
						case 3:
							admin();
						    break;
						case 4:
							cout<<"Exiting the line"<<endl;
							break;
						default:
						cout<<"invalid choice"<<endl;
					}
					break;
				}while(cho!=4);
				break;
			case 4:
				reportDetails();
			break;
			case 5:
				cout<<"Exiting....";
				break;
			default:
			cout<<"Wrong choice...";
// 		 while(choice!=4);
 		  break;
	}
	}while(choice!=5);
	return 0;
}
void addStudent()
{
    int count=0;
	if(numStudents>=MAX_STUDENTS)
	{
		cout<<"Error:Maximum number of students reached"<<endl;
		return ;
	}
	struct Student newStudent;
	identity:
		cout<<"Enter the student ID:-";
		cin>>newStudent.id;
		for(int i=0;i<numStudents;i++)
		{
			if(students[i].id==newStudent.id)
			{
				count++;
				cout<<"Id alreday existed.."<<endl;
				goto identity;
			}
		}
			cout<<"Enter Student name:-";
			cin>>newStudent.name;
			cout<<"Enter Student age:-";
			cin>>newStudent.age;
			cout<<"Enter Student city:-";
			cin>>newStudent.city;
			cout<<"Enter Student address:-";
			cin>>newStudent.Address;
			students[numStudents++]=newStudent;
			cout<<"student added successfully"<<endl;
}
void displayStudent()
{
	if(numStudents==0)
	{
		cout<<"Record not found"<<endl;
		return;
		
	}
	cout<<"Student details are As Below:-"<<endl;
	cout<<"ID\tName\tAge\tCity\t\tAddress"<<endl;
	for(i=0;i<numStudents;i++)
	{
		cout<<students[i].id<<"\t"<<students[i].name<<"\t"<<students[i].age<<"\t"<<students[i].city<<"\t\t"<<students[i].Address<<"\t"<<endl;
	}
}

    void searchStudent() 
	{
	    int searchId;
	    bool found=false;
	    cout<<"Enter student ID to search";
	    cin>>searchId;
		cout<<"ID\tName\tAge\tCity\tAddress"<<endl;

	    for (int i = 0; i < numStudents; i++)
		 {
	        if (students[i].id == searchId)
	        {
	        	found=true;
	            cout<<"Student found"<<endl;
	            cout<<students[i].id<<"\t"<<students[i].name<<"\t\t"<<students[i].age<<"\t\t"<<students[i].city<<"\t\t"<<students[i].Address<<endl;
	            break;
	        }
	    }
	    if(!found)
		{
			cout<<searchId<<" not existed..";
		}
}
void updateStudent()
{
	int ch;
	do
	{
		cout<<"1.Update by student Id"<<endl;
		cout<<"2.Update by studnet Name"<<endl;
		cout<<"3.Update by student City"<<endl;
		cout<<"4.Update by student Address"<<endl;
		cout<<"Enter your choice"<<endl;
		cin>>ch;
		switch(ch)
		{
				case 1:
					updateById();
				break;
				case 2:
					updateByName();
				break;
				case 3:
					updateByCity();
				break;
				case 4:
					updateByAddress();
				break;
				case 5:
					cout<<"Exiting";
				break;
				default:
					cout<<"Invalid choice";			
		}
	}while(ch!=5);
}
void updateById()
{
		int updateId;
	    bool found=false;
	    cout<<"Enter student ID to update:-";
	    cin>>updateId;
		cout<<"ID\tName\tAge\tCity\tAddress"<<endl;

	    for (int i = 0; i < numStudents; i++)
		 {
	        if (students[i].id == updateId)
	        {
	        	found=true;
	            cout<<"Student found"<<endl;
	            if(found==true)
	            {
	            	cout<<"Enter Id For Update:-";
	    			cin>>updateId;
	    			students[i].id=updateId;
				}
	            cout<<updateId<<"\t"<<students[i].name<<"\t"<<students[i].age<<"\t"<<students[i].city<<"\t"<<students[i].Address<<endl;	            
	    	}
	    }
		{
	    if(!found)
			cout<<updateId<<" Not existed.....";
		}	
}
void updateByName()
{
		string updateName;
	    bool found=false;
	    cout<<"Enter student Name to update:-";
	    cin>>updateName;
	    for(i=0;i<numStudents;i++)
	    {
	    	if(students[i].name==updateName);
	    	{
	    		found=true;
	    		cout<<"Student Found"<<endl;
	    		if(found==true)
	            {
	            	cout<<"Enter Name For Update:-";
	    			cin>>updateName;
	    			students[i].name=updateName;
				}
	            cout<<students[i].id<<"\t"<<updateName<<"\t"<<students[i].age<<"\t"<<students[i].city<<"\t"<<students[i].Address<<endl;	
			}
			
		}
		if(!found)
		cout<<updateName<<" Not existed.....";
}
void updateByCity()
{
		string updateCity;
	    bool found=false;
	    cout<<"Enter student city to update:-";
	    cin>>updateCity;
	    for(i=0;i<numStudents;i++)
	    {
	    	if(students[i].city==updateCity);
	    	{
	    		found=true;
	    		cout<<"Student Found"<<endl;
	    		if(found==true)
	            {
	            	cout<<"Enter City For Update:-";
	    			cin>>updateCity;
	    			students[i].city=updateCity;
				}
	            cout<<students[i].id<<"\t"<<students[i].name<<"\t"<<students[i].age<<"\t"<<updateCity<<"\t"<<students[i].Address;	
			}
			
		}
		if(!found)
		cout<<updateCity<<" Not existed.....";
}
void updateByAddress()
{
		string updateAddress;
	    bool found=false;
	    cout<<"Enter student Address to update:-";
	    cin>>updateAddress;
	    for(i=0;i<numStudents;i++)
	    {
	    	if(students[i].Address==updateAddress);
	    	{
	    		found=true;
	    		cout<<"Address Found"<<endl;
	    		if(found==true)
	            {
	            	cout<<"Enter Address For Update:-";
	    			cin>>updateAddress;
	    			students[i].Address=updateAddress;
				}
	            cout<<students[i].id<<"\t"<<students[i].name<<"\t"<<students[i].age<<"\t"<<students[i].city<<updateAddress<<"\t"<<endl;	
			}
			
		}
		if(!found)
		cout<<updateAddress<<" Not existed.....";
}
void addCourse()
{
	struct courseDetails temp;
	struct Student st;
	if(numCourses>MAX_COURSES)
	{
		cout<<"Error:Maximum number of courses reached"<<endl;
		return;
	}
	cout<<"Enter student id:-";
	cin>>st.id;
	for(i=0;i<numStudents;i++)
	{
		if(students[i].id==st.id)
		{
			identity:
			cout<<"Enter the course ID:-";
			cin>>temp.courseID;
			
			for(int i=0;i<numCourses;i++)
			{
				if(newCourse[i].courseID==temp.courseID)
				{
					cout<<"Id alreday existed.."<<endl;
					goto identity;
				}
			}
				cout<<"Enter Course name:-";
				cin>>temp.courseName;
				cout<<"Enter Course fees-";
				cin>>temp.courseFees;
				cout<<"Enter Course Duration:-";
				cin>>temp.courseDuration;
				newCourse[numCourses++]=temp;
				cout<<"Course added successfully"<<endl;
	
		}
	}
	
	}
void displayCourse()
{
	if(numCourses==0)
	{
		cout<<"Record not found"<<endl;
			return;
			
		}
		cout<<"Course details are As Below:-"<<endl;
		cout<<"Student Id\tCourse Id\tCourse Name\tCourse Fees\tCourse Duration"<<endl;
		
		for(i=0;i<numCourses;i++)
		{
			cout<<students[i].id<<"\t"<<newCourse[i].courseID<<"\t\t"<<newCourse[i].courseName<<"\t\t"<<newCourse[i].courseFees<<"\t\t"<<newCourse[i].courseDuration<<endl;
	    }	
	
}
void searchCourseById() 
	{
	    string searchCourse;
	    bool found=false;
	    cout<<"Enter course Id to search:- ";
	    cin>>searchCourse;
	    for (int i = 0; i < numCourses; i++)
		 {
	        if (newCourse[i].courseID == searchCourse)
	        {
	        //	cout<<"Course found"<<endl;
	        	found=true;
	        	cout<<"Course found"<<endl<<endl
				;
	            cout<<"Course Id\tCourse Name\tCourse Fees\tCourse Duration"<<endl;
	            cout<<newCourse[i].courseID<<"\t\t"<<newCourse[i].courseName<<"\t\t"<<newCourse[i].courseFees<<"\t\t"<<newCourse[i].courseDuration<<endl;
	           
	            break;
	        }
	    }
	    if(!found)
		{
			cout<<searchCourse<<" not existed..";
		}
}
void searchCourseByName()
{
	string searchCourse;
	    bool found=false;
	    cout<<"Enter course name to search:- ";
	    cin>>searchCourse;
		cout<<"Course Id\tCourse Name\tCourse Fees\tCourse Duration"<<endl;

	    for (int i = 0; i < numCourses; i++)
		 {
	        if (newCourse[i].courseName == searchCourse)
	        {
	        	//cout<<"Course found"<<endl;
	        	found=true;
	            //cout<<"Course found"<<endl;
	            cout<<newCourse[i].courseID<<"\t\t"<<newCourse[i].courseName<<"\t\t"<<newCourse[i].courseFees<<"\t\t"<<newCourse[i].courseDuration<<endl;
	            cout<<"Course found"<<endl;
	            break;
	        }
	    }
	    if(!found)
		{
			cout<<searchCourse<<" not existed.."<<endl;
		}
}
		
void searchCourse() 
{
		
            int ch;
            do
            {
        		cout<<"Press 1 for: Search By ID"<<endl;
				cout<<"Press 2 for: Search By Name"<<endl;
				cout<<"Press 3 For : Exit...."<<endl;
				cout<<"Enter Your Choice";
				cin>>ch;
	            switch(ch)
	            {
	            	case 1:
	            		searchCourseById();
	            		break;
	            	case 2:
	            		searchCourseByName();
	            		break;
	            	case 3:
	            		cout<<"Exiting.....";
	            		break;
	            	default:
	            		cout<<"invalid Choice";
	            }
	        }while(ch!=3);
	        	   
}
void deleteCourseById()
{
	string deleteId;
	int pos=0;
	cout<<"Enter course Id to delete";
	cin>>deleteId;
	int found=0;
	for(int i=0;i<numCourses;i++)
	{
		if(newCourse[i].courseID==deleteId)
		{
			found=1;
			pos=i;
			break;
		}
	}
	if(found==1)
	{
		numCourses--;
	}
	if(!found)
	{
		cout<<"Course Id not found"<<endl;
	}
}
void training()
{
    int choice;
    do
    {
        cout<<"Department details are:-"<<endl;
        cout<<"\t1. Add trainer's Details"<<endl;
        cout<<"\t2. Display trainer's Details "<<endl;
        cout<<"\t3. Search trainer's Details"<<endl;
        cout<<"\t4. Delete trainer's Details "<<endl;
        cout<<"\t5. Exit"<<endl;
        cout<<"Enter your choice:- "<<endl;
        cin>>choice;
        switch(choice)
        {
            case 1:
                addTrainers();
            break;
            case 2:
                displayTrainers();
            break;
            case 3:
                searchTrainers();
            break;
            case 4:
                deleteTrainers();
            break;
            case 5:
                cout<<"exiting ..."<<endl;
            break;
            default:
                cout<<"Invalid choice"<<endl;
                break;
        }//break; 
    }while(choice!=5);
    //break;
    
}
void addTrainers()
{
    struct trainingDepartment temp;
     if(numTrainers>MAX_TRAINERS)
 	{
 		cout<<"Error:Maximum number of Trainers Are reached"<<endl;
 		return ;
 	}
 	identity:
		cout<<"Enter the Trainers ID:-";
		cin>>temp.id;
 		for(int i=0;i<numTrainers;i++)
 		{
 			if(temp.id==newTrainer[i].id)
 			{
 				cout<<"Id Alreday Existed.."<<endl;
 				goto identity;
 			}
 		}
            cout<<"Enter the trainers Name:-";
            cin>>temp.name;
            cout<<"Enter the trainers Salary:-";
            cin>>temp.salary;
            cout<<"Enter the trainers Designation";
            cin>>temp.designation;
            newTrainer[numTrainers++]=temp;
			cout<<"Trainee added successfully"<<endl;
}
void displayTrainers()
{ 
	bool flag=false;
	int count=0;
	if(numTrainers==0)
	{
		flag=true;
		cout<<"No record found"<<endl;
	}
	else{
	cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Designation"<<endl;
	for(int i=0;i<numTrainers;i++)
	{
		count++;
		cout<<newTrainer[i].id<<"\t"<<newTrainer[i].name<<"\t"<<newTrainer[i].salary<<"\t"<<newTrainer[i].designation<<endl;
	}
	}
}
void searchTrainers()
{
	string searchId;
	bool ok=false;
	cout<<"Enter Id to Search Trainer:-";
	cin>>searchId;
    if(numTrainers==0)
    {
	 	cout<<"Trainers Not Found"<<endl;  
	}
		for(i=0;i<=numTrainers;i++)
	    {
	    	if(newTrainer[i].id==searchId)
			{
				ok=true;
				cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Designation"<<endl;				
				cout<<newTrainer[i].id<<"\t"<<newTrainer[i].name<<"\t"<<newTrainer[i].salary<<"\t"<<newTrainer[i].designation<<endl;
			}
		}ok!=true;
		{
			cout<<"Trainer Id Not Found"<<endl;
		}
}
void deleteTrainers()
{
    string deleteId;
	int pos=0;
	cout<<"Enter Trainer Id to delete";
	cin>>deleteId;
	int found=0;
	for(int i=0;i<numTrainers;i++)
	{
		if(newTrainer[i].id==deleteId)
		{
			found=1;
			pos=i;
			break;
		}
	}
	if(found==1)
	{
		numTrainers--;
	}
	if(!found)
	{
		cout<<"Trainers Id not found"<<endl;
	}
}
void developing()
{ 
    int choice;
    do
    {
        cout<<"Department details are:-"<<endl;
        cout<<"\t1. Add developing"<<endl;
        cout<<"\t2. Display developing details"<<endl;
        cout<<"\t3. Search developing details"<<endl;
        cout<<"\t4.  Delete developing details "<<endl;
        cout<<"\t5.Exit"<<endl;
        cout<<"Enter your choice:- "<<endl;
        cin>>choice;
        switch(choice)
        {
            case 1:
                addDeveloping();
            break;
            case 2:
                displayDeveloping();
            break;
            case 3:
                searchDeveloping();
            break;
            case 4:
                deleteDeveloping();
            break;
            case 5:
                cout<<"exiting ..."<<endl;
            break;
            default:
                cout<<"Invalid choice"<<endl;
                break;
        }
      // break; 
    }while(choice!=5);
    //break;
}
void addDeveloping()
{
    struct developingDepartment temp;
    identity:
    cout<<"Enter Developers Id:-";
    cin>>temp.id;
    
 		for(int i=0;i<numDevelopers;i++)
 		{
 			if(temp.id==newDevelopers[i].id)
 			{
 				cout<<"Id Alreday Existed.."<<endl;
 				goto identity;
 			}
 		}
 		
            cout<<"Enter the Developers Name:-";
            cin>>temp.name;
            cout<<"Enter the Developers Salary:-";
            cin>>temp.salary;
            cout<<"Enter the Developers Designation:-";
            cin>>temp.designation;
            cout<<"Enter the Developers Project:-";
            cin>>temp.project;
            cout<<"Enter the Developers Technology:-";
            cin>>temp.technology;
            newDevelopers[numDevelopers++]=temp;
			cout<<"Developers added successfully"<<endl;
    
}		
void displayDeveloping()
{
   bool flag=false;
	if(numDevelopers==0)
	{
		flag=true;
		cout<<"No record found"<<endl;
	}
	else{
	cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Designation"<<"\t"<<"Project"<<"\t"<<"Technology"<<endl;
	for(int i=0;i<numDevelopers;i++)
	{
		cout<<newDevelopers[i].id<<"\t"<<newDevelopers[i].name<<"\t"<<newDevelopers[i].salary<<"\t"<<newDevelopers[i].designation<<"\t""\t"<<newDevelopers[i].project<<"\t"<<newDevelopers[i].technology<<"\t"<<endl;
	}
	}
}
void searchDeveloping()
{
    string searchId;
	bool ok=false;
	cout<<"Enter to Search Developers Id:-";
	cin>>searchId;
	//cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Designation"<<"\t"<<"project"<<"\t"<<"technology"<<endl;	
    
		for(i=0;i<=numDevelopers;i++)
	    {
	    	if(newDevelopers[i].id==searchId)
			{
				ok=true;
				cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Designation"<<"\t"<<"project"<<"\t"<<"technology"<<endl;		
				cout<<newDevelopers[i].id<<"\t"<<newDevelopers[i].name<<"\t"<<newDevelopers[i].salary<<"\t"<<newDevelopers[i].designation<<"\t""\t"<<newDevelopers[i].project<<"\t"<<newDevelopers[i].technology<<"\t"<<endl;
			}
		}ok!=true;
		
			if(numDevelopers==0)
			{
	 			cout<<"Developers Not Found"<<endl;
			
			}
	}
		
void deleteDeveloping()
{
    string deleteId;
	int pos=0;
	cout<<"Enter Developers Id to delete";
	cin>>deleteId;
	int found=0;
	for(int i=0;i<numDevelopers;i++)
	{
		if(newDevelopers[i].id==deleteId)
		{
			found=1;
			pos=i;
			break;
		}
	}
	if(found==1)
	{
		numDevelopers--;
	}
	if(!found)
	{
		cout<<"Developers Id not found"<<endl;
	}
}
void admin()
{
    int choice;
    do
    {
        cout<<"Department details are:-"<<endl;
        cout<<"\t1. Add admin  "<<endl;
        cout<<"\t2. Display admin details "<<endl;
        cout<<"\t3. Search admin details"<<endl;
        cout<<"\t4.  Delete admin details "<<endl;
        cout<<"\t5. Exit"<<endl;
        cout<<"Enter your choice:- "<<endl;
        cin>>choice;
        switch(choice)
        {
            case 1:
                addAdmin();
            break;
            case 2:
                displayAdmin();
            break;
            case 3:
                searchAdmin();
            break;
            case 4:
                deleteAdmin();
            break;
            case 5:
                cout<<"exiting ..."<<endl;
            break;
            default:
                cout<<"Invalid choice"<<endl;
        		 break;
        }
       //break; 
    }while(choice!=5);
    //break;
}
void addAdmin()
{
    struct addAdminDepartment temp;
    identity:
    cout<<"Enter Id:-";
    cin>>temp.id;
    
 		for(int i=0;i<numaddAdmin;i++)
 		{
 			if(temp.id==newaddAdmin[i].id)
 			{
 				cout<<"Id Alreday Existed.."<<endl;
 				goto identity;
 			}
 		}
 		
            cout<<"Enter the  Name:-";
            cin>>temp.name;
            cout<<"Enter the  Salary:-";
            cin>>temp.salary;
            cout<<"Enter the role:-";
            cin>>temp.role;
            newaddAdmin[numaddAdmin++]=temp;
			cout<<"Admin added successfully"<<endl;
}		
void displayAdmin()
{
   bool flag=false;
	if(numaddAdmin==0)
	{
		flag=true;
		cout<<"No record found"<<endl;
	}
	else{
	cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Role"<<endl;
	for(int i=0;i<numaddAdmin;i++)
	{
		cout<<newaddAdmin[i].id<<"\t"<<newaddAdmin[i].name<<"\t"<<newaddAdmin[i].salary<<"\t"<<newaddAdmin[i].role<<endl;
	}
	}
}
void searchAdmin()
{
    string searchId;
	bool ok=false;
	cout<<"Enter to Search Admin Id:-";
	cin>>searchId;
		for(i=0;i<=numaddAdmin;i++)
	    {
	    	if(newaddAdmin[i].id==searchId)
			{
				ok=true;
				cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Roll"<<"\t"<<endl;		
				cout<<newaddAdmin[i].id<<"\t"<<newaddAdmin[i].name<<"\t"<<newaddAdmin[i].salary<<"\t"<<newaddAdmin[i].role<<endl;
			}
		}ok!=true;
		if(numaddAdmin==0)
		{
 			cout<<"Admin Not Found"<<endl;
		
		}
}
void deleteAdmin()
{
    string deleteId;
	int pos=0;
	cout<<"Enter Admin Id to delete";
	cin>>deleteId;
	int found=0;
	for(int i=0;i<numaddAdmin;i++)
	{
		if(newaddAdmin[i].id==deleteId)
		{
			found=1;
			pos=i;
			break;
		}
	}
	if(found==1)
	{
		numaddAdmin--;
	}
	if(!found)
	{
		cout<<"Admin Id not found"<<endl;
	}
} 
void reportDetails()
{
    //int count=1;
    cout<<"CODE IT Software Training Institute....."<<endl<<endl;
    if(numStudents!=0)
    {
        cout<<"Total No.of Students are:-"<<i+1<<"and Details :-"<<endl<<endl;
        cout<<"ID\tName\tAge\tCity\t\tAddress"<<endl;
    	for(i=0;i<numStudents;i++)
    	{
    		cout<<students[i].id<<"\t"<<students[i].name<<"\t"<<students[i].age<<"\t"<<students[i].city<<"\t\t"<<students[i].Address<<"\t"<<endl;
    		//count++;
    	}
    }
    if(numCourses!=0)
	{
	    cout<<"Total No.of Courses are:-"<<i+1<<"and Details :-"<<endl;
    	cout<<"Student Id\tCourse Id\tCourse Name\tCourse Fees\tCourse Duration"<<endl;
    		for(i=0;i<numCourses;i++)
    		{
    			cout<<students[i].id<<"\t"<<newCourse[i].courseID<<"\t\t"<<newCourse[i].courseName<<"\t\t"<<newCourse[i].courseFees<<"\t\t"<<newCourse[i].courseDuration<<endl;
    	    }	
	}
    if(numaddAdmin!=0)
    {
        cout<<"Total No.of Admin are:-"<<i+1<<"and Details :-"<<endl;
        cout<<"Admin Details are:-"<<endl;
    	cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Role"<<endl;
    	for(int i=0;i<numaddAdmin;i++)
    	{
    		cout<<newaddAdmin[i].id<<"\t"<<newaddAdmin[i].name<<"\t"<<newaddAdmin[i].salary<<"\t"<<newaddAdmin[i].role<<endl;
    	}
    }
    if(numDevelopers!=0)
    {
    	cout<<"Total No.of Developers are:-"<<i+1<<"and Details :-"<<endl;
    	cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Designation"<<"\t"<<"Project"<<"\t"<<"Technology"<<endl;
    	for(int i=0;i<numDevelopers;i++)
    	{
    		cout<<newDevelopers[i].id<<"\t"<<newDevelopers[i].name<<"\t"<<newDevelopers[i].salary<<"\t"<<newDevelopers[i].designation<<"\t""\t"<<newDevelopers[i].project<<"\t"<<newDevelopers[i].technology<<"\t"<<endl;
    	}
    }
    if(numTrainers!=0)
    {
    	cout<<"Total No.of Trainers are:-"<<i+1<<" Details :-"<<endl;
    	cout<<"Id"<<"\t"<<"Name"<<"\t"<<"Salary"<<"\t"<<"Designation"<<endl;
    	for(int i=0;i<numTrainers;i++)
    	{
    		cout<<newTrainer[i].id<<"\t"<<newTrainer[i].name<<"\t"<<newTrainer[i].salary<<"\t"<<newTrainer[i].designation<<endl;
    	}
    }
}
