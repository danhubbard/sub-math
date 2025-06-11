# Submariner Calculation Test App - Development Brief

## Project Overview
Build a prototype HTML application for submariners to practice range calculations. The app presents ship identification scenarios where users calculate range based on ship height and observation time.

## Core Functionality

### Calculation Formulas
```
Range = (Ship Height / Minutes Pulled) × 1000
DOT = Range × ATB Decimal Value
```

### User Flow
1. App displays a randomly selected ship type with its height
2. App displays a randomly generated "minutes pulled" value (2-30 minutes)
3. App displays a randomly selected "Angle on the Bow (ATB)" value with unit 'S'
4. User calculates and enters both the Range and DOT values
5. Submit button remains disabled until both fields have values
6. App validates both inputs and shows feedback:
   - **Both Correct**: Green indicators for both fields + "Next" button
   - **One or Both Incorrect**: Red indicators for incorrect field(s) + "Try Again"
   - User must get both calculations correct to proceed to next problem

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
Create hardcoded JavaScript arrays with placeholder data:
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

const ATB_VALUES = [
  { angle: 0, decimal: 0 },
  { angle: 6, decimal: 0.10 },
  { angle: 10, decimal: 0.166 },
  { angle: 12, decimal: 0.20 },
  { angle: 15, decimal: 0.25 },
  { angle: 20, decimal: 0.33 },
  { angle: 30, decimal: 0.50 },
  { angle: 40, decimal: 0.65 },
  { angle: 50, decimal: 0.75 },
  { angle: 60, decimal: 0.85 },
  { angle: 70, decimal: 0.95 },
  { angle: 80, decimal: 1.00 },
  { angle: 90, decimal: 1.00 }
];
```

### Input Specifications
- **Minutes Pulled Range**: 2-30 (randomly generated)
- **ATB Values**: Randomly selected from predefined list [0,6,10,12,15,20,30,40,50,60,70,80,90]S
- **User Input Fields**: 
  - Range: HTML `type="number"` 
  - DOT: HTML `type="number"`
- **Answer Matching**: Exact match required for both calculations
- **Submit Button**: Disabled until both fields contain values
- **Input Validation**: Basic numeric validation via HTML input types

## User Interface Requirements

### Layout
- Clean, functional design (prototype-level styling)
- Clear presentation of:
  - Current ship type and height
  - Minutes pulled value
  - Angle on the Bow (ATB) value with 'S' unit
  - Range calculation input field
  - DOT calculation input field (positioned below Range field)
  - Feedback area for both calculations
  - Submit button (disabled until both fields populated)
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
- Randomly select ATB value from predefined list
- Calculate correct Range using: (Ship Height / Minutes Pulled) × 1000
- Calculate correct DOT using: Range × ATB Decimal Value
- Display ship name, height, minutes pulled, and ATB value to user

### Answer Processing
- Accept user inputs for both Range and DOT via number fields
- Keep submit button disabled until both fields contain values
- On submit, compare both user answers to calculated correct answers
- Provide immediate feedback with appropriate color coding for each field
- Show "Next" button only when both calculations are correct
- Show "Try Again" for same problem when one or both answers are incorrect

### Session Management
- **Current scope**: Page refresh to restart
- **Future consideration**: Formal session reset functionality
- **Future consideration**: Problem completion tracking

## Development Notes

### Code Organization
- Extend existing controllers to handle dual-calculation functionality
- Consider adding a form validation controller if complexity warrants it
- Keep controllers focused and single-responsibility
- Use Stimulus data attributes for configuration
- Implement clean separation between data, logic, and presentation
- Add basic error handling for edge cases

### Extension Implementation
- **IMPORTANT**: The Range calculation functionality has already been built and should remain unchanged
- Extend the existing implementation to add:
  - ATB data structure and random selection
  - DOT calculation logic
  - Dual input validation and feedback
  - Submit button state management
  - Enhanced problem generation including ATB values

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
- [ ] App randomly generates calculation problems with ship, minutes pulled, and ATB values
- [ ] User can input both Range and DOT numeric answers
- [ ] Submit button is disabled until both fields contain values
- [ ] Range calculation uses existing formula: (Ship Height / Minutes Pulled) × 1000
- [ ] DOT calculation uses formula: Range × ATB Decimal Value
- [ ] Correct answers show green feedback for respective fields
- [ ] Incorrect answers show red feedback for respective fields
- [ ] Next button appears only when both calculations are correct
- [ ] Try Again option appears when one or both answers are incorrect
- [ ] Next button generates new random problem with all new values
- [ ] All calculations use exact formulas provided
- [ ] Clean, functional interface using Tailwind CSS
- [ ] Existing Range functionality remains unchanged and operational