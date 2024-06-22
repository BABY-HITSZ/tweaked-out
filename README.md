//@version=5
indicator("My Custom Index", overlay = true)

// Calculate the index of the current bar
calcBarIndex() =>
    var int index = na
    index := nz(index[1], replacement = -1) + 1

// Define the condition for custom index calculation (every other bar)
condition = bar_index % 2 == 0

// Initialize custom index
var int customIndex = na

// Calculate custom index when the condition is true
if condition
    customIndex := calcBarIndex()

// Plot bar index and custom index
plot(bar_index, "Bar index", color = color.green)
plot(customIndex, "Custom index", color = color.red, style = plot.style_cross)
