# Car Park Registration System

A command-line based parking management system built with Python that manages student parking registrations, parking slot assignments, and user authentication.

## Features

### Core Functionality
- **User Authentication**: Login and registration system for administrators
- **Student Records Management**:
  - Add new student parking registrations
  - Modify existing records
  - Delete records
  - Search records by multiple criteria
  - View all registered students
- **Parking Slot Management**:
  - Visual 3-level parking lot display (45 total slots)
  - Real-time parking slot availability tracking
  - Automatic slot assignment and release
- **Registration Management**:
  - 120-day registration period
  - Automatic expiry date calculation
  - Date validation and formatting

### Search Capabilities
Search for student records by:
- Student TP number
- First name
- Last name
- Phone number
- Email address
- Car plate number
- Registration date

## System Requirements

- Python 3.x
- Windows OS (uses Windows-specific console commands)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd python-parkingSystem
```

2. Ensure Python 3.x is installed:
```bash
python --version
# or
python3 --version
```

3. Run the application:
```bash
python Carpark-SELF-EDIT.py
# or on Mac/Linux
python3 Carpark-SELF-EDIT.py
```

## How to Run This Application

### Step 1: Start the Application
When you run the program, you'll see the home screen:
```
------- WELCOME TO APU CAR PARK REGISTRATION SYSTEM -------

1. Login
2. Register
3. Exit
```

### Step 2: Login
Use the default administrator credentials:
- **UserID**: `admin`
- **Password**: `1234`

**Note**: After first login, you can create additional user accounts via the Register option.

### Step 3: Navigate the Main Menu
After successful login, you'll see:
```
------- WELCOME TO CARPARK REGISTRATION SYSTEM -------

1. Add a New Record
2. Modify a record
3. Delete a record
4. Search a record
5. View All records
6. Display parking slots
7. Log out
8. Quit
```

## Sample Data to Enter

### Adding Your First Student Record

When you select **Option 1 (Add a New Record)**, you'll be prompted to enter:

#### Example 1: Valid Student Registration
```
Enter Student's TP number: TP038850
Enter Student's First Name: Rachel
Enter Student's Last Name: Lim
Enter Student's Mobile Number: 91234567
Enter Student's E-mail address: rachel.lim@student.apu.edu.my
Enter Student's Car Plate Number: WYA4804
Enter a date in DD-MM-YYYY format: 07-01-2026
Enter Parking Space ID: L101
```

#### Example 2: Another Valid Record
```
Enter Student's TP number: TP041234
Enter Student's First Name: John
Enter Student's Last Name: Tan
Enter Student's Mobile Number: 98765432
Enter Student's E-mail address: john.tan@student.apu.edu.my
Enter Student's Car Plate Number: SJK9876
Enter a date in DD-MM-YYYY format: 07-01-2026
Enter Parking Space ID: L102
```

#### Example 3: International Student
```
Enter Student's TP number: TP055678
Enter Student's First Name: Sarah
Enter Student's Last Name: Wong
Enter Student's Mobile Number: 87654321
Enter Student's E-mail address: sarah.wong@gmail.com
Enter Student's Car Plate Number: ABC1234
Enter a date in DD-MM-YYYY format: 10-01-2026
Enter Parking Space ID: L201
```

## What to Expect

### Input Validation
The system now validates all inputs:

✅ **TP Number**: Must follow format `TPxxxxxx` (e.g., TP038850)
- ❌ Invalid: `TP123` (too short)
- ❌ Invalid: `tp038850` (wrong case - but auto-corrected)
- ✅ Valid: `TP038850`

✅ **Phone Number**: Must be 8-15 digits
- ❌ Invalid: `1234` (too short)
- ❌ Invalid: `abcd1234` (contains letters)
- ✅ Valid: `91234567`

✅ **Email**: Must be valid email format
- ❌ Invalid: `test@` (incomplete)
- ❌ Invalid: `test.com` (missing @)
- ✅ Valid: `student@apu.edu.my`

✅ **Parking Slot**: Must exist and be available
- ❌ Invalid: `L199` (doesn't exist)
- ❌ Invalid: `****` (already taken)
- ✅ Valid: `L101`, `L201`, `L301`

### Automatic Features

1. **Expiry Date Calculation**
   - Registration period: 120 days
   - If you register on `07-01-2026`, expiry date will be `06-05-2026`

2. **Data Persistence**
   - All student records are saved to `parking_data.json`
   - All user accounts are saved to `users_data.json`
   - Data persists between sessions

3. **Parking Slot Management**
   - Selected slots are marked as `****` and become unavailable
   - Deleting a record frees up the parking slot automatically

### Viewing Parking Slots (Option 6)

When you select **Display parking slots**, you'll see:
```
------- PARKING SLOTS -------

----- LEVEL 1 -----
L101   |   L102   |   L103   |   L104   |   L105
****   |   L107   |   L108   |   L109   |   L110
L111   |   L112   |   L113   |   L114   |   L115

----- LEVEL 2 -----
L201   |   L202   |   L203   |   L204   |   L205
...
```
- `****` indicates the slot is occupied
- Parking slot IDs show available slots

### Searching Records (Option 4)

You can search by:
1. TP number (e.g., `TP038850`)
2. First Name (e.g., `Rachel`)
3. Last Name (e.g., `Lim`)
4. Phone (e.g., `91234567`)
5. Email (e.g., `rachel@student.apu.edu.my`)
6. Carplate (e.g., `WYA4804`)
7. Registration date (e.g., `07-01-2026`)

### Security Features

1. **Password Hashing**: Passwords are hashed using SHA-256
2. **Duplicate Prevention**:
   - Cannot register same TP number twice
   - Cannot create duplicate usernames
3. **Secure Authentication**: Username and password must match

### Parking Lot Layout
- **Level 1**: Slots L101 - L115 (15 slots)
- **Level 2**: Slots L201 - L216 (16 slots)
- **Level 3**: Slots L301 - L316 (14 slots)
- **Total**: 45 parking slots

### Student Information Stored
- Student ID (TP number)
- First Name
- Last Name
- Phone Number
- Email Address
- Car Plate Number
- Registration Date
- Expiry Date (auto-calculated as Registration Date + 120 days)
- Assigned Parking Slot ID

## Project Structure

```
python-parkingSystem/
├── Carpark-SELF-EDIT.py    # Main application file
├── Pseudocode.docx          # Planning documentation
└── README.md                # This file
```

## Data Files

The system creates two JSON files to store data:

1. **`parking_data.json`**: Stores all student parking registrations
   - Student details (ID, name, contact info)
   - Car information
   - Registration and expiry dates
   - Parking slot assignments

2. **`users_data.json`**: Stores user account information
   - User IDs and hashed passwords
   - User names

**Note**: These files are created automatically on first save. Don't edit them manually unless you know what you're doing!

## Troubleshooting

### Problem: "Module not found" error
**Solution**: The system uses only built-in Python modules. Ensure you're using Python 3.x.

### Problem: Data not saving
**Solution**: Check that you have write permissions in the directory where the program is running.

### Problem: Can't see parking slots properly
**Solution**:
- On Windows: The console is auto-sized
- On Mac/Linux: Maximize your terminal window for best display

### Problem: Forgot admin password
**Solution**: Delete the `users_data.json` file. The default admin account will be recreated on next startup.

## Recent Improvements (Version 2.0)

### ✅ Fixed Issues
1. **Security Bug**: Fixed authentication vulnerability - passwords now properly validated
2. **TP Number Bug**: Fixed string slicing error that caused incorrect TP number formatting
3. **Data Persistence**: All data now saved to JSON files automatically
4. **Cross-Platform**: Now works on Windows, Mac, and Linux
5. **Input Validation**: Added validation for TP numbers, emails, and phone numbers
6. **Password Security**: Passwords are now hashed using SHA-256
7. **Duplicate Prevention**: Cannot register duplicate TP numbers or usernames

### 🔧 Technical Improvements
- Added regex validation for all inputs
- Improved error handling with try-except blocks
- Auto-save after every add/modify/delete operation
- Cross-platform clear screen function
- Better user feedback for invalid inputs

## Future Enhancements

### Planned Features
1. **Export Functionality**: Generate reports in PDF/Excel format
2. **Email Notifications**: Send registration confirmations and expiry reminders
3. **Payment Integration**: Add payment tracking for parking fees
4. **GUI Interface**: Create a graphical user interface
5. **Advanced Search**: Filter by multiple criteria simultaneously
6. **Expiry Alerts**: Automatic notifications for expiring registrations
7. **Audit Log**: Track all changes for security purposes

## License

This project is available for educational purposes.

## Contact

For questions or suggestions, please open an issue in the repository.
