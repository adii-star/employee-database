# employee-database
 c program to create employee database
 #include <stdio.h>
struct Employee
{
	int id;
    char name[50];	
    float salary;
}; 
int main() {
    struct Employee emp[100], temp;
	int n, i, j; 
    printf("Enter number of employees: ");
    scanf("%d", &n); 
	for (i = 0; i < n; i++) {
        printf("\nEnter details for employee %d:\n", i + 1);
        printf("Employee ID: ");
        scanf("%d", &emp[i].id);
        printf("Name: ");
        scanf(" %[^\n]s", emp[i].name);  
        printf("Salary: ");
        scanf("%f", &emp[i].salary);
	}
	for (i = 0; i < n - 1; i++) {
        for (j = i + 1; j < n; j++) {
            if (emp[i].salary < emp[j].salary ||
               (emp[i].salary == emp[j].salary && emp[i].id > emp[j].id)) {
            	temp = emp[i];
            	emp[i] = emp[j];
            	emp[j] = temp;
            }
        }
	}
 
    printf("\n--- Employee Details (Sorted by Salary) ---\n");
    printf("%-10s %-20s %-10s\n", "ID", "Name", "Salary");
    printf("--------------------------------------------\n"); 
	for (i = 0; i < n; i++) {
        printf("%-10d %-20s %-10.2f\n", emp[i].id, emp[i].name, emp[i].salary);
	} 
    return 0;
}

