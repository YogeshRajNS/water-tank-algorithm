# 💧 Water Tank Problem - Trapping Rain Water

A visual web application that solves the classic "Trapping Rain Water" algorithm problem using Vanilla JavaScript, HTML, and CSS with interactive SVG visualization.

![JavaScript](https://img.shields.io/badge/javascript-ES6+-yellow.svg)
![HTML5](https://img.shields.io/badge/html5-latest-orange.svg)
![CSS3](https://img.shields.io/badge/css3-latest-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

## 📋 Problem Statement

Given **n** block heights (always greater than -1), compute the units of water that can be stored/trapped between the blocks. This classic algorithm problem simulates rain water collection between elevation blocks.

**Example:**
- **Input:** `[0,4,0,0,0,6,0,6,4,0]`
- **Output:** `18 Units`

The water collects in valleys between taller blocks, and the amount of water at each position is determined by the minimum of the maximum heights on its left and right sides.

## 🎯 Features

- **Interactive Web Interface**: Clean, modern dark-themed UI
- **SVG Visualization**: Real-time graphical representation of blocks and water
- **Two-Pointer Algorithm**: Efficient O(n) time complexity solution
- **Color-Coded Display**:
  - 🟡 Yellow: Block walls/structures
  - 🔵 Blue: Trapped water (with transparency)
  - ⚫ Dark background for contrast
- **Responsive Design**: Works across different screen sizes
- **Input Validation**: Filters invalid inputs automatically
- **Real-Time Calculation**: Instant results as you input data

## 🧮 Algorithm Explanation

### Two-Pointer Approach

The solution uses an efficient **two-pointer technique** with O(n) time complexity and O(n) space complexity.

#### How It Works:

1. **Initialize Pointers**: Start with `left` at the beginning and `right` at the end
2. **Track Maximum Heights**: Maintain `leftMax` and `rightMax` for heights seen so far
3. **Move Pointers Inward**: 
   - If `height[left] < height[right]`: Process left side
     - Update `leftMax`
     - Calculate water: `waterAt[left] = max(0, leftMax - height[left])`
     - Move `left++`
   - Else: Process right side
     - Update `rightMax`
     - Calculate water: `waterAt[right] = max(0, rightMax - height[right])`
     - Move `right--`
4. **Continue**: Repeat until pointers meet

#### Why It Works:

The key insight is that the water level at any position is determined by the minimum of the maximum heights on both sides. By processing from both ends, we can efficiently determine this without scanning the entire array multiple times.

#### Complexity Analysis:
- **Time Complexity**: O(n) - Single pass through the array
- **Space Complexity**: O(n) - Array to store water at each position
- **Optimality**: This is the optimal solution for this problem

### Example Walkthrough

For input `[0,4,0,0,0,6,0,6,4,0]`:

```
Position:  0  1  2  3  4  5  6  7  8  9
Height:    0  4  0  0  0  6  0  6  4  0
Water:     0  0  4  4  4  0  2  0  0  0
Total: 0+0+4+4+4+0+2+0+0+0 = 18 units
```

Visual representation:
```
6 |       █     █
5 |       █     █
4 |   █   █     █   █
3 |   █ W █ W   █   █
2 |   █ W █ W   █ W █
1 |   █ W █ W   █ W █
0 | _ █ W █ W █ █ W █ _ 
    0 1 2 3 4 5 6 7 8 9

█ = Block (Yellow)
W = Water (Blue)
```

## 🚀 Installation & Usage

### Option 1: Direct Usage (Recommended)

1. **Clone the repository**
```bash
git clone https://github.com/YogeshRajNS/Water_Tank_Algorithm.git
cd Water_Tank_Algorithm
```

2. **Open in Browser**
```bash
# Simply open the HTML file in your browser
open water_tank_algorithm.html
# Or on Windows
start water_tank_algorithm.html
# Or on Linux
xdg-open water_tank_algorithm.html
```

That's it! No installation or dependencies required.

### Option 2: Using Live Server (Development)

1. **Install Live Server** (if using VS Code)
   - Install the "Live Server" extension
   - Right-click on `water_tank_algorithm.html`
   - Select "Open with Live Server"

2. **Or use Python's HTTP server**
```bash
python -m http.server 8000
# Then open http://localhost:8000/water_tank_algorithm.html
```

## 💻 How to Use

1. **Enter Block Heights**: Input comma-separated numbers in the text field
   - Example: `0,4,0,0,0,6,0,6,4,0`
   - Example: `3,0,2,0,4`
   - Example: `0,1,0,2,1,0,1,3,2,1,2,1`

2. **Click "Compute Water"**: The application will:
   - Calculate total water trapped
   - Display the result
   - Generate an interactive SVG visualization

3. **View Results**:
   - Total water units displayed above the chart
   - SVG chart shows blocks (yellow) and water (blue)
   - Visual representation makes it easy to verify the solution

## 🎨 Visualization Details

### Color Scheme
- **Background**: Dark navy (`#0f172a`)
- **Blocks/Walls**: Yellow (`#facc15`)
- **Water**: Light blue (`#38BDF8`) with 80% opacity
- **Axis**: Gray (`#475569`)

### SVG Components
- **Chart Area**: 800x300 pixels (responsive)
- **Block Width**: Dynamically calculated based on input length
- **Height Scaling**: Proportional to maximum block height
- **Water Overlay**: Rendered above blocks with transparency

## 📁 Project Structure

```
Water_Tank_Algorithm/
│
├── water_tank_algorithm.html    # Complete web application (HTML/CSS/JS)
├── README.md                     # This documentation
```

## 🛠️ Technologies Used

- **HTML5**: Structure and layout
- **CSS3**: Styling and visual design
- **Vanilla JavaScript**: Logic and interactivity
- **SVG (Scalable Vector Graphics)**: Data visualization

### Why Vanilla JavaScript?

This project uses pure JavaScript without any frameworks or libraries to:
- ✅ Demonstrate core JavaScript skills
- ✅ Keep the solution lightweight and fast
- ✅ Ensure no external dependencies
- ✅ Make it easy to understand and modify

## 🧪 Test Cases

### Test Case 1
**Input:** `[0,4,0,0,0,6,0,6,4,0]`  
**Expected Output:** `18 Units`  
**Explanation:** Water fills valleys between heights 4, 6, and 6

### Test Case 2
**Input:** `[3,0,2,0,4]`  
**Expected Output:** `7 Units`  
**Explanation:** Water trapped: 0+3+1+3+0 = 7

### Test Case 3
**Input:** `[0,1,0,2,1,0,1,3,2,1,2,1]`  
**Expected Output:** `6 Units`  
**Explanation:** Multiple small valleys trap water

### Test Case 4
**Input:** `[4,2,0,3,2,5]`  
**Expected Output:** `9 Units`  
**Explanation:** Large valley between heights 4 and 5

### Edge Cases
**Input:** `[5,5,5,5]` → **Output:** `0 Units` (flat surface, no valleys)  
**Input:** `[1,2,3,4,5]` → **Output:** `0 Units` (ascending, no trapping)  
**Input:** `[5,4,3,2,1]` → **Output:** `0 Units` (descending, no trapping)

## 🎯 Code Highlights

### Core Algorithm Function
```javascript
function trapRainWater(height) {
    let left = 0, right = height.length - 1;
    let leftMax = 0, rightMax = 0;
    let water = 0;
    let waterAt = new Array(height.length).fill(0);

    while (left < right) {
        if (height[left] < height[right]) {
            leftMax = Math.max(leftMax, height[left]);
            waterAt[left] = Math.max(0, leftMax - height[left]);
            water += waterAt[left];
            left++;
        } else {
            rightMax = Math.max(rightMax, height[right]);
            waterAt[right] = Math.max(0, rightMax - height[right]);
            water += waterAt[right];
            right--;
        }
    }
    return { water, waterAt };
}
```

### Input Validation
```javascript
const values = document.getElementById("input").value
    .split(',')
    .map(v => parseInt(v.trim()))
    .filter(v => !isNaN(v) && v >= 0);
```

## 🌐 Browser Compatibility

- ✅ Chrome (recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ✅ Opera

**Requirements**: Modern browser with SVG support (all major browsers since 2015+)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License.

## 👤 Author

**Yogesh Raj NS** - [@YogeshRajNS](https://github.com/YogeshRajNS)

Project Link: [https://github.com/YogeshRajNS/Water_Tank_Algorithm](https://github.com/YogeshRajNS/Water_Tank_Algorithm)

## 🙏 Acknowledgments

- Problem based on **"Water Tank Problem"** interview assignment
- Classic **"Trapping Rain Water"** algorithm from LeetCode
- Inspired by data structure and algorithm challenges
- SVG visualization technique for algorithm understanding

## 🔮 Future Enhancements

-  Add animation showing water filling process
-  Display step-by-step algorithm execution
-  Add different visualization styles (3D, isometric)
-  Export results as image/PDF
-  Compare different algorithm approaches (brute force vs two-pointer)
-  Add preset examples dropdown
-  Mobile-responsive touch interactions
-  Show time complexity visualization

---

⭐ If you found this project helpful, please consider giving it a star!
