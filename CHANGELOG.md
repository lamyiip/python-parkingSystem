# Changelog

## Version 2.0 - 2026-01-07

### 🔒 Security Fixes
- **CRITICAL**: Fixed authentication vulnerability where any password in the system could log in any user
- Implemented SHA-256 password hashing for secure password storage
- Added duplicate username prevention during registration
- Added duplicate TP number prevention during student registration

### 🐛 Bug Fixes
- Fixed TP number string slicing bug (was `temp[2:]`, now correctly `temp[:2]` for "TP" prefix)
- Fixed multiple instances of the same bug in modify and search functions
- Added proper validation to prevent crashes from invalid input

### ✨ New Features
- **Data Persistence**: All data now automatically saved to JSON files
  - `parking_data.json` - Student parking records
  - `users_data.json` - User account data
- **Input Validation**:
  - TP Number format validation (TPxxxxxx)
  - Email format validation
  - Phone number validation (8-15 digits)
  - Parking slot existence check
- **Cross-Platform Support**: Now works on Windows, Mac, and Linux
- Auto-save after every add, modify, and delete operation
- Better error messages for invalid inputs

### 🎨 Improvements
- Cross-platform clear screen function
- Replaced Windows-only `pause` command with cross-platform alternative
- Improved user feedback throughout the application
- Car plates now auto-converted to uppercase
- Names now properly title-cased

### 📝 Documentation
- Comprehensive README with:
  - Step-by-step usage guide
  - Sample data examples
  - Input validation rules
  - Troubleshooting section
  - What to expect guide
- Added this CHANGELOG
- Better inline code comments

### 🔧 Technical Changes
- Added `json`, `re`, and `hashlib` imports
- Created validation functions:
  - `validate_email()`
  - `validate_phone()`
  - `validate_tp_number()`
- Created data persistence functions:
  - `save_parking_data()`
  - `load_parking_data()`
  - `save_users_data()`
  - `load_users_data()`
- Created password hashing function:
  - `hash_password()`
- Data loads automatically on startup
- Parking slots initialize only if loading fails

### 📊 Code Quality
- Improved error handling with try-except blocks
- Better input validation loops
- Consistent code formatting
- Removed commented-out dead code

### ⚠️ Breaking Changes
- Existing user passwords will need to be reset (due to hashing)
- Default admin password remains `1234` but is now hashed
- Old data files (if any) may need manual migration

## Version 1.0 - Original Release
- Basic parking management system
- In-memory data storage
- Windows-only support
- Basic CRUD operations for student records
- Parking slot visualization
- Simple login system
