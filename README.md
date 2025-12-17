# Water Tank Problem - Trapping Rain Water

A frontend web application that solves the classic "Trapping Rain Water" algorithm problem with interactive visualization using Vanilla JavaScript, HTML, and CSS.

## Problem Statement

Given **n** block heights (always greater than -1), compute the units of water that can be stored between the blocks. The solution provides both the calculated result and a visual representation using SVG graphics.

### Example

**Input:** `[0,4,0,0,0,6,0,6,4,0]`

**Output:** `18 Units`

## Features

- **Interactive Input**: Enter custom block heights as comma-separated values
- **Real-time Calculation**: Computes trapped water instantly using an optimized two-pointer algorithm
- **SVG Visualization**: Dynamic visual representation showing:
  - Block heights (yellow bars)
  - Trapped water (translucent blue overlay)
  - Scale and proportions
- **Responsive Design**: Clean, modern UI with dark theme
- **No Dependencies**: Pure Vanilla JavaScript implementation

## Algorithm

The solution uses the **Two-Pointer Approach** for optimal performance:

- **Time Complexity**: O(n)
- **Space Complexity**: O(n)

### How It Works

1. Initialize two pointers at the start (`left`) and end (`right`) of the array
2. Track the maximum heights seen from both sides (`leftMax`, `rightMax`)
3. Move pointers inward, always processing the side with the smaller height
4. Calculate water trapped at each position: `max(0, maxHeight - currentHeight)`
5. Continue until pointers meet

This approach ensures each element is processed exactly once, achieving linear time complexity.

## Installation & Usage

### Prerequisites

- Any modern web browser (Chrome, Firefox, Safari, Edge)
- No server or build tools required

### Running the Application

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd water-tank-problem
   ```

2. **Open the HTML file:**
   - Simply open `water_tank_algorithm.html` in your web browser
   - Or use a local server (optional):
     ```bash
     # Using Python 3
     python -m http.server 8000
     
     # Using Node.js
     npx serve
     ```

3. **Use the application:**
   - Enter block heights as comma-separated numbers (e.g., `0,4,0,0,0,6,0,6,4,0`)
   - Click "Compute Water" button
   - View the result and visual representation

## Code Structure

```
water-tank-problem/
│
├── water_tank_algorithm.html    # Main application file
│   ├── HTML Structure           # Input form and SVG container
│   ├── CSS Styles              # Dark theme styling
│   └── JavaScript Logic        # Algorithm and visualization
│
└── README.md                    # This file
```

## Key Functions

### `trapRainWater(height)`
Core algorithm that calculates total water trapped and water at each position.

**Parameters:**
- `height` (Array): Array of block heights

**Returns:**
- Object containing:
  - `water` (Number): Total units of water trapped
  - `waterAt` (Array): Water trapped at each position

### `solve()`
Processes user input, validates data, and triggers calculation and visualization.

### `drawChart(blocks, waterAt)`
Generates SVG visualization showing blocks and trapped water.

**Parameters:**
- `blocks` (Array): Block heights
- `waterAt` (Array): Water trapped at each position

## Technical Details

### Input Validation
- Splits input by commas
- Parses integers
- Filters out invalid values (NaN, negative numbers)
- Handles empty or malformed input gracefully

### Visualization
- SVG-based rendering for crisp, scalable graphics
- Color coding:
  - **Yellow (#facc15)**: Block walls
  - **Blue (#38BDF8)**: Trapped water (with 80% opacity)
  - **Gray (#64748b)**: Base blocks
- Automatic scaling based on maximum height
- Responsive bar width based on number of blocks

## Browser Compatibility

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

## Example Test Cases

```javascript
// Test Case 1: Original example
Input: [0,4,0,0,0,6,0,6,4,0]
Output: 18 Units

// Test Case 2: Simple valley
Input: [3,0,2,0,4]
Output: 7 Units

// Test Case 3: Ascending stairs
Input: [1,2,3,4,5]
Output: 0 Units

// Test Case 4: Descending stairs
Input: [5,4,3,2,1]
Output: 0 Units

// Test Case 5: Multiple valleys
Input: [4,2,0,3,2,5]
Output: 9 Units
```

## Assignment Requirements

✅ **Requirement Met**: Compute water units stored between blocks

✅ **Requirement Met**: Web application using Vanilla JavaScript

✅ **Requirement Met**: HTML/CSS frontend solution

✅ **Requirement Met**: SVG shape representation (preferred method)

✅ **Requirement Met**: Handle input where n > -1

## Future Enhancements

-  Add animation showing water filling process
-  Export visualization as PNG/SVG
-  Multiple color themes
-  Display water at each position in a table view
-  Step-by-step algorithm visualization
-  Pre-loaded example datasets
-  Mobile-responsive controls

## License

This project is created as an interview assignment solution.

## Author

Created as a solution to the Water Tank Problem coding challenge.

---

**Note**: This is a pure frontend solution with no backend dependencies. All calculations and rendering happen in the browser using Vanilla JavaScript.
