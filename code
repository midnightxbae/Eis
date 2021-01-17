#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <time.h>

// Variables
FILE *categories, *record, *report;
char category[100];
float cost, total_payment = 0.00, payment = 0.00, tax, discount, travel_tax;
char anothervar = 'y';
int counter = 1, choice = 0, age;
bool want = true;

// Flight Ticketing Report Updates
int reportAmounts[100] = {0};
int quantities[100] = {0};
int reportTax[100] = {0};
int allCategories = 4;
char countries[100][40] = {"Australia", "Indonesia", "Japan", "Singapore", "USA"};

// Function Prototypes
void serveFunc();
bool isWant(char x);

// flight ticketing records
void writeSales(int choice, float payment, int age);
int flightCategory;
int i;

// flight ticketing reports
void writeSalesReport();

int main()
{

    // First file for reading.
    categories = fopen("file.txt", "r");

    // Second file for appending, means it will add what category you chose.
    record = fopen("record.txt", "w");

    system("color f3");

    // if the file is not existing it will appear as error.
    if (categories == NULL)
    {
        printf("Unable to open file.\n");
        return 1;
    }

    // Title
    printf("\t\t DESTINATION CATEGORY \n\n");

    // Headers
    printf("   Destination \t Price per Destination\t Travel Tax\n");

    // Categories
    while(fscanf(categories, "%s %f %f", category, &cost, &tax) != EOF)
    {
        printf("%i. |%-10s | | %-21.2f| | %2.0f%% | \n", counter, category, cost, tax * 100);
        counter++;
    }
    fclose(categories);

    // Yes or no loop
    while (want)
    {
        serveFunc();
        printf("Amount to be paid: %0.2f\n", payment);
        printf("+ Travel Tax: %0.2f\n", travel_tax);
        if (anothervar == 'y' || anothervar == 'Y')
        {
            printf("\nDo you want another service(y/n)? ");
            scanf(" %c", &anothervar);
            want = isWant(anothervar);
            if(anothervar == 'n' || anothervar == 'N')
            {
                system("cls");
                printf("\n\n\t\t\t\t *****PRINTING FLIGHT TICKETING REPORT...***** \n\n\n");
            }
        }
        choice = 0;
    }
    writeSalesReport();
}

// Function for choosing what category and age.
void serveFunc()
{
    if (choice == 0)
        {
            printf("\nSelect the type of category: ");
            scanf("%i", &choice);
            printf("Enter your age: ");
            scanf("%i", &age);

            // Discount logic
            if (age >= 2 && age <= 5)
                discount = 0.1;
            else if (age < 60 && age >= 6)
                discount = 0;
            else if (age >= 60)
                discount = 0.2;
            else
                discount = 1;
        }
        if (choice == 1)
        {
            printf("\nYou picked Australia.\n");
            // Calculation
            total_payment += 30000 - (30000 * discount);
            payment = 30000 - (30000 * discount);
            travel_tax = (payment * tax);
            writeSales(choice, payment, age);

            // Data storing in array
            reportAmounts[0] += payment;
            quantities[0] += 1;
            reportTax[0] += travel_tax;
        }
        else if (choice == 2)
        {
            printf("\nYou picked Indonesia.\n");
            // Calculation
            total_payment += 10000 - (10000 * discount);
            payment = 10000 - (10000 * discount);
            travel_tax = payment * tax;
            writeSales(choice, payment, age);

            // Data storing in array
            reportAmounts[1] += payment;
            quantities[1] += 1;
            reportTax[1] += travel_tax;
        }
        else if (choice == 3)
        {
            printf("\nYou picked Japan.\n");
            // Calculation
            total_payment += 40000 - (40000 * discount);
            payment = 40000 - (40000 * discount);
            travel_tax = payment * tax;
            writeSales(choice, payment, age);

            // Data storing in array
            reportAmounts[2] += payment;
            quantities[2] += 1;
            reportTax[2] += travel_tax;
        }
        else if (choice == 4)
        {
            printf("\nYou picked Singapore.\n");
            // Calculation
            total_payment += 12000 - (12000 * discount);
            payment = 12000 - (12000 * discount);
            travel_tax = payment * tax;
            writeSales(choice, payment, age);

            // Data storing in array
            reportAmounts[3] += payment;
            quantities[3] += 1;
            reportTax[3] += travel_tax;
        }
        else if (choice == 5)
        {
            printf("\nYou picked USA.\n");
            // Calculation
            total_payment += 30000 - (30000 * discount);
            payment = 30000 - (30000 * discount);
            travel_tax = payment * tax;
            writeSales(choice, payment, age);

            // Data storing in array
            reportAmounts[4] += payment;
            quantities[4] += 1;
            reportTax[4] += travel_tax;
        }
        else
        {
            printf("\nError input of choice.\n");
            printf("Please enter the appropriate choice.\n\n");
            total_payment += 0;
            payment = 0;
            travel_tax = 0;
        }
}

// If the user chose no, it will return false and print out new output.
bool isWant(char x)
{
    if (x == 'y' || x == 'Y')
        return true;
    return false;
}


// Choice function that appends in file 2.
void writeSales(int x, float y, int z)
{
  int choice = x - 1;
  char type[5][100] = {"Australia", "Indonesia", "Japan", "Singapore", "USA"};
  fprintf(record, "| %9s |\t| %-5i |\t| %-8.2f | \n", type[choice], z, y);
}

void writeSalesReport()
{
  int totalAmount = 0;
  int totalQuantities = 0;
  int totalTax = 0;
  report = fopen("report.txt", "w");
  system("color f3");

  //print titles
  printf("\t%-20s \t%10s \t%10s %15s", "DESTINATION", "QUANTITY", "AMOUNT", "TRAVEL TAX");
  printf("\n------------------------------------------------------------------------------------------------------------------------");
  fprintf(report, "\t%-20s \t%10s \t%10s %15s", "DESTINATION", "QUANTITY", "AMOUNT", "TRAVEL TAX");
  fprintf(report, "\n------------------------------------------------------------------------------------------------------------------------");
  for (int i = 0; i < 5; i++)
  {
    //print per categories
    printf("\n\n\t%-20s %9d %19d %12d", countries[i], quantities[i], reportAmounts[i], reportTax[i]);
    fprintf(report, "\n\n\t%-20s %9d %19d %12d", countries[i], quantities[i], reportAmounts[i], reportTax[i]);

    //tracking for TOTAL category
    totalAmount += reportAmounts[i];
    totalQuantities += quantities[i];
    totalTax += reportTax[i];
  }
  //Print 'TOTAL' category
  printf("\n------------------------------------------------------------------------------------------------------------------------");
  printf("\n\n\t%-20s %9d %19d %12d\n\n", "TOTAL", totalQuantities, totalAmount, totalTax);
  fprintf(report,"\n------------------------------------------------------------------------------------------------------------------------");
  fprintf(report,"\n\n\t%-20s %9d %19d %12d\n\n", "TOTAL", totalQuantities, totalAmount, totalTax);
  fclose(report);
  printf("\nPrepared by: Concepcion, Angela A. \n\t     Moises, Eisen Lois E.\n");
  time_t t;
  time(&t);
  printf("\nDate Prepared: %s", ctime(&t));
  return;
}
