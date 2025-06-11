# Submariner Calculation Test App - Development Brief

## Project Overview
Build a prototype HTML application for submariners to practice range calculations. The app presents ship identification scenarios where users calculate range based on ship height and observation time.

## Core Functionality

### Calculation Formula
```
Range = (Ship Height / Minutes Pulled) × 1000
```

### User Flow
1. App displays a randomly selected ship type with its height
2. App displays a randomly generated "minutes pulled" value (2-30 minutes)
3. User calculates and enters the range value
4. App validates input and shows feedback:
   - **Correct**: Green indicator + "Next" button to generate new problem
   - **Incorrect**: Red indicator + "Try Again" (same problem persists)

## Technical Requirements

### Tech Stack
- **HTML5** with semantic markup
- **Stimulus.js** for JavaScript functionality
- **Tailwind CSS** for styling
- **Modern browsers only** (ES6+ support assumed)

### Architecture
- **Multiple Stimulus Controllers** approach:
  - `calculation-controller`: Manages problem generation and calculation logic
  - `feedback-controller`: Handles answer validation and UI feedback
  - `ship-data-controller`: Manages ship information
- **Use Stimulus Outlets** for cross-controller communication when needed
- **No backend required** - fully client-side application

### Data Structure
Create a hardcoded JavaScript array of ship objects with data:
```javascript
const SHIPS = [
  { name: "Small Fishing Vessel", height: 20 },
  { name: "Large Fishing Vessel", height: 50 },
  { name: "Warship 110", height: 110 },
  { name: "Warship 40", height: 40 },
  { name: "Small Merchant Vessel", height: 80 },
  { name: "Medium Merchant Vessel", height: 60 },
  { name: "Large Merchant Vessel", height: 150 },
  { name: "VL MV 200", height: 200 },
];
```

### Input Specifications
- **Minutes Pulled Range**: 2-30 (randomly generated)
- **User Input Field**: HTML `type="number"` for automatic validation
- **Answer Matching**: Exact match required (no margin of error)
- **Input Validation**: Basic numeric validation via HTML input type

## User Interface Requirements

### Layout
- Clean, functional design (prototype-level styling)
- Clear presentation of:
  - Current ship type and height
  - Minutes pulled value
  - Calculation input field
  - Feedback area
  - Action buttons (Next/Try Again)

### Styling Guidelines
- **Tailwind CSS** utility classes only
- **Minimal but functional** appearance
- **Color coding**:
  - Green for correct answers
  - Red for incorrect answers
- **Responsive design** not critical for prototype
- **Focus on functionality** over visual polish

## Functional Specifications

### Problem Generation
- Randomly select ship from predefined array
- Randomly generate minutes pulled (2-30 inclusive)
- Calculate correct answer using provided formula
- Display ship name, height, and minutes pulled to user

### Answer Processing
- Accept user input via number field
- Compare user answer to calculated correct answer
- Provide immediate feedback with appropriate color coding
- Show relevant action button based on result

### Session Management
- **Current scope**: Page refresh to restart
- **Future consideration**: Formal session reset functionality
- **Future consideration**: Problem completion tracking

## Development Notes

### Code Organization
- Keep controllers focused and single-responsibility
- Use Stimulus data attributes for configuration
- Implement clean separation between data, logic, and presentation
- Add basic error handling for edge cases

### Browser Compatibility
- Target modern browsers with ES6+ support
- No legacy browser compatibility required
- Use modern JavaScript features as appropriate

### Extensibility Considerations
While building prototype-level functionality, structure code to accommodate future enhancements:
- Session tracking capabilities
- Enhanced feedback with correct answer display
- Formal restart/reset functionality
- Additional ship data fields
- Answer tolerance ranges

## Deliverable
Single HTML file containing:
- Complete HTML structure
- Embedded Stimulus JavaScript controllers
- Tailwind CSS styling (via CDN)
- Hardcoded ship data with placeholders
- Full working prototype functionality

## Success Criteria
- [ ] App randomly generates calculation problems
- [ ] User can input numeric answers
- [ ] Correct answers show green feedback with Next button
- [ ] Incorrect answers show red feedback with Try Again option
- [ ] Next button generates new random problem
- [ ] All calculations use exact formula provided
- [ ] Clean, functional interface using Tailwind CSS
- [ ] Multiple Stimulus controllers with proper separation of concerns