# Habit Tracker: Drinking Water Tracker

## Overview
This is a simple command-line application that tracks daily water intake. It allows users to:
- **View all records**: See a list of all water intake records.
- **Insert a new record**: Add a record of water consumption (date and quantity).
- **Delete a record**: Remove a record based on its unique ID.
- **Update a record**: Modify an existing record's date and quantity.

The application uses **SQLite** as the database to store the water intake records, providing persistence across sessions.

---

## Features
- **Database**: The app uses an SQLite database (`habit-Tracker.db`) to store records in a table called `drinking_water`.
- **Main Menu**: Users can interact with the program through a text-based menu that allows them to view, insert, delete, or update records.
- **Date Format**: Dates are entered in `dd-MM-yy` format (e.g., `10-11-24` for November 10, 2024).
- **Quantity**: Users specify the quantity of water consumed (e.g., number of glasses or another unit).

---

## Installation

### Prerequisites
- **.NET SDK** (if you want to build the project yourself):
  - Download and install .NET SDK: [https://dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)
- **SQLite** (this application uses SQLite for data storage):
  - SQLite is included via the `Microsoft.Data.Sqlite` NuGet package, which is automatically managed by the project.

### Setting up the project
1. Clone the repository to your local machine:
    ```bash
    git clone https://github.com/yourusername/habit_tracker.git
    cd habit_tracker
    ```
2. Open the project in Visual Studio or any C# compatible IDE.
3. Ensure you have the necessary NuGet package:
    ```bash
    dotnet add package Microsoft.Data.Sqlite
    ```
4. Build and run the application:
    ```bash
    dotnet build
    dotnet run
    ```

The application will create a new SQLite database file (`habit-Tracker.db`) if one doesn't exist already.

---

## Usage

### Main Menu
When the application starts, the following menu will be displayed:


- **Option 0**: Closes the application.
- **Option 1**: Displays all records in the `drinking_water` table.
- **Option 2**: Prompts the user to input the date and quantity for a new record.
- **Option 3**: Prompts the user to select a record by its `Id` and delete it.
- **Option 4**: Prompts the user to select a record by its `Id` and update the date or quantity.

### Example Input and Output

- **Insert Record**:
    ```
    Please insert the date: (Format: dd-mm-yy). Type 0 to return to main menu.
    10-11-24

    Please insert number of glasses or other measure of your choice (no decimals allowed)
    8
    ```
    The record `10-11-24 | 8` will be inserted into the database.

- **View All Records**:
    ```
    1 - 10-Nov-2024 - Quantity: 8
    2 - 11-Nov-2024 - Quantity: 7
    3 - 12-Nov-2024 - Quantity: 6
    ```

- **Delete Record**:
    ```
    Please type the Id of the record you want to delete or type 0 to go back to Main Menu
    1
    Record with Id 1 was deleted.
    ```

---

## Database Structure

The app uses an SQLite database called `habit-Tracker.db`. It contains a table called `drinking_water` with the following structure:

```sql
CREATE TABLE IF NOT EXISTS drinking_water (
    Id INTEGER PRIMARY KEY AUTOINCREMENT,
    Date TEXT,
    Quantity INTEGER
);

#Error Handling
Invalid Date: If the user inputs an invalid date format, they will be prompted to re-enter the date until a valid format (dd-MM-yy) is provided.
Invalid Number: If the user inputs an invalid number for the quantity, they will be prompted to re-enter a valid number.