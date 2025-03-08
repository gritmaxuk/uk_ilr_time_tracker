# ILR Absence Calculator

This web application helps track and calculate absence days for ILR (Global Talent) visa requirements in the UK. It implements the algorithm described in the provided documentation to ensure compliance with the 180-day absence limit in any 12-month period.

## Features

- **Multiple user profiles**: Create and manage different profiles for multiple people
- **Visual timeline**: See a 5-year visual representation of your presence/absence in the UK
- **Rolling 12-month window**: Automatically calculates the rolling 12-month period from the current date
- **Absence summary**: Shows total days absent in the last 12 months and remaining allowance
- **Trip management**: Add, edit, and delete trips with departure and return dates
- **JSON profile storage**: Profiles are stored as JSON files in the profiles/ directory

## File Structure

```
ilr-absence-calculator/
├── index.html           # Main HTML file with UI
├── js/                  # JavaScript directory
│   └── app.js           # Application logic
├── profiles/            # Directory for JSON profile files
│   └── example.json     # Example profile file
└── README.md            # Documentation and usage instructions
```

## Setup

1. Create a `profiles/` directory in the same location as your `index.html` file
2. Place any existing profile JSON files in this directory
3. Open `index.html` in a web browser
4. Create profiles as needed - they will be saved to the profiles/ directory

## How to Use

1. **Managing Profiles**:
   - Create a new profile by entering a name and clicking "Create Profile"
   - Save the generated JSON file to the `profiles/` directory
   - Use the "Refresh Profiles" button to scan the profiles/ directory for new files
   - Select an existing profile from the dropdown

2. **Setting Up Profile**:
   - Enter your first entry date in the UK
   - Save the profile

3. **Adding Trips**:
   - Enter departure date (when you left the UK)
   - Enter return date (when you came back), or leave empty for ongoing trips
   - Click "Add Trip"

4. **Viewing Data**:
   - The absence summary shows your status at a glance
   - The timeline visualization shows your entire 5-year period with color coding:
     - Green: Present in the UK
     - Red: Absent from the UK
     - Gray: Future dates
     - Blue outline: Current rolling 12-month window

## Profile JSON Format

Each profile is stored as a separate JSON file with the following structure:

```json
{
  "firstEntry": "YYYY-MM-DD",  // Date of first entry to the UK
  "trips": [
    {
      "departure": "YYYY-MM-DD",  // Date left the UK
      "return": "YYYY-MM-DD"      // Date returned to the UK (or null if not returned)
    },
    // Additional trips...
  ]
}
```

## Calculation Logic

- The application follows the ILR absence calculation rules:
  - Counts any day outside the UK as an absence day
  - Calculates absences within rolling 12-month periods
  - Tracks against the 180-day limit in any consecutive 12-month period
  - Handles absence periods that cross over different 12-month periods

## Requirements

- Modern web browser with JavaScript enabled
- Web server or file server for automatic profile detection
- (When using directly from the filesystem, you may need to create profiles manually)