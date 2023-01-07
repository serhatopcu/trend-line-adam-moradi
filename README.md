# trend-line-adam-moradi

I developed an indicator for trader Adam Moradi.

https://tr.tradingview.com/i/7nYt1gP8/

The Pine Script strategy that plots pivot points and trend lines on a chart. The strategy allows the user to specify the period for calculating pivot points and the number of pivot points to be used for generating trend lines. The user can also specify different colors for the up and down trend lines.

The script starts by defining the input parameters for the strategy and then calculates the pivot high and pivot low values using the pivothigh() and pivotlow() functions. It then stores the pivot points in two arrays called trend_top_values and trend_bottom_values. The script also has two arrays called trend_top_position and trend_bottom_position which store the positions of the pivot points.

The script then defines a function called add_to_array() which takes in three arguments: apointer1, apointer2, and val. This function adds val to the beginning of the array pointed to by apointer1, and adds bar_index to the beginning of the array pointed to by apointer2. It then removes the last element from both arrays.

The script then checks if a pivot high or pivot low value has been calculated, and if so, it adds the value and its position to the appropriate arrays using the add_to_array() function.

Next, the script defines two arrays called bottom_lines and top_lines which will be used to store trend lines. It also defines a variable called starttime which is set to the current time.

The script then enters a loop to calculate and plot the trend lines. It first deletes any existing trend lines from the chart. It then enters two nested loops which iterate over the pivot points stored in the trend_bottom_values and trend_top_values arrays. For each pair of pivot points, the script calculates the slope of the line connecting them and checks if the line is a valid trend line by iterating over the price bars between the two pivot points and checking if the line is above or below the close price of each bar. If the line is found to be a valid trend line, it is plotted on the chart using the line.new() function.

Finally, the script colors the trend lines using the colors specified by the user.



Tutorial Content

'PivotPointNumber' is an input parameter for the script that specifies the number of pivot points to consider when calculating the trend lines. The value of 'PivotPointNumber' is set by the user when they configure the script. It is used to determine the size of the arrays that store the values and positions of the pivot points, as well as the number of pivot points to loop through when calculating the trend lines.

'up_trend_color' is an input parameter for the script that specifies the color to use for drawing the trend lines that are determined to be upward trends. The value of 'up_trend_color' is set by the user when they configure the script and is passed to the color parameter of the line.new() function when drawing the upward trend lines. It determines the visual appearance of the upward trend lines on the chart.

'down_trend_color' is an input parameter for the script that specifies the color to use for drawing the trend lines that are determined to be downward trends. The value of 'down_trend_color' is set by the user when they configure the script and is passed to the color parameter of the line.new() function when drawing the downward trend lines. It determines the visual appearance of the downward trend lines on the chart.

'pivothigh' is a variable in the script that stores the value of the pivot high point. It is calculated using the pivothigh() function, which returns the highest high over a specified number of bars. The value of 'pivothigh' is used in the calculation of the trend lines.

'pivotlow' is a variable in the script that stores the value of the pivot low point. It is calculated using the pivotlow() function, which returns the lowest low over a specified number of bars. The value of 'pivotlow' is used in the calculation of the trend lines.


'trend_top_values' is an array in the script that stores the values of the pivot points that are determined to be at the top of the trend. These are the pivot points that are used to calculate the upward trend lines.

'trend_top_position'  is an array in the script that stores the positions (i.e., bar indices) of the pivot points that are stored in the 'trend_top_values' array. These positions correspond to the locations of the pivot points on the chart.

'trend_bottom_values'  is an array in the script that stores the values of the pivot points that are determined to be at the bottom of the trend. These are the pivot points that are used to calculate the downward trend lines.

'trend_bottom_position' is an array in the script that stores the positions (i.e., bar indices) of the pivot points that are stored in the 'trend_bottom_values' array. These positions correspond to the locations of the pivot points on the chart.


apointer1 and apointer2 are variables used in the add_to_array() function, which is defined in the script. They are both pointers to arrays, meaning that they hold the memory addresses of the arrays rather than the arrays themselves. They are used to manipulate the arrays by adding new elements to the beginning of the arrays and removing elements from the end of the arrays.


apointer1 is a pointer to an array of floating-point values, while apointer2 is a pointer to an array of integers. The specific arrays that they point to depend on the arguments passed to the add_to_array() function when it is called. For example, if add_to_array(trend_top_values, trend_top_posisiton, pivothigh) is called, then apointer1 would point to the tval array and apointer2 would point to the tpos array.

'bottom_lines' (short for "Bottom Lines") is an array in the script that stores the line objects for the downward trend lines that are drawn on the chart. Each element of the array corresponds to a different trend line.

'top_lines' (short for "Top Lines") is an array in the script that stores the line objects for the upward trend lines that are drawn on the chart. Each element of the array corresponds to a different trend line.

Both 'bottom_lines' and 'top_lines' are arrays of type "line", which is a data type in PineScript that represents a line drawn on a chart. The line objects are created using the line.new() function and are used to draw the trend lines on the chart. The variables are used to store the line objects so that they can be manipulated and deleted later in the script.

//loop

maxline is a variable in the script that specifies the maximum number of trend lines that can be drawn on the chart. It is used to determine the size of the bottom_lines and top_lines arrays, which store the line objects for the trend lines.

The value of maxline is set to 3 at the beginning of the script, meaning that at most 3 trend lines can be drawn on the chart at a time. This value can be changed by the user if desired by modifying the assignment statement "maxline = 3".


'count_line_low' (short for "Count Line Low") is a variable in the script that keeps track of the number of downward trend lines that have been drawn on the chart. It is used to ensure that the maximum number of trend lines (as specified by the maxline variable) is not exceeded.

'count_line_high' (short for "Count Line High") is a variable in the script that keeps track of the number of upward trend lines that have been drawn on the chart. It is used to ensure that the maximum number of trend lines (as specified by the maxline variable) is not exceeded.

Both 'count_line_low' and 'count_line_high' are initialized to 0 at the beginning of the script and are incremented each time a new trend line is drawn. If either variable exceeds the value of maxline, then no more trend lines are drawn.


'pivot1', 'up_val1', 'up_val2', up1, and up2 are variables used in the loop that calculates the downward trend lines in the script. They are used to store intermediate values during the calculation process.

'pivot1' is a loop variable that is used to iterate through the pivot points (stored in the trend_bottom_values and trend_bottom_position arrays) that are being considered for use in the trend line calculation.

'up_val1' and 'up_val2' are variables that store the values of the pivot points that are used to calculate the downward trend line.

up1 and up2 are variables that store the positions (i.e., bar indices) of the pivot points that are stored in 'up_val1' and 'up_val2', respectively. These positions correspond to the locations of the pivot points on the chart.

'value1' and 'value2' are variables that are used to store the values of the pivot points that are being compared in the loop that calculates the trend lines in the script. They are used to determine whether a trend line can be drawn between the two pivot points.

For example, if 'value1' is the value of a pivot point at the top of the trend and 'value2' is the value of a pivot point at the bottom of the trend, then a trend line can be drawn between the two points if 'value1' is greater than 'value2'. The values of 'value1' and 'value2' are used in the calculation of the slope and intercept of the trend line.


'position1' and 'position2' are variables that are used to store the positions (i.e., bar indices) of the pivot points that are being compared in the loop that calculates the trend lines in the script. They are used to determine the distance between the pivot points, which is necessary for calculating the slope of the trend line.

For example, if 'position1' is the position of a pivot point at the top of the trend and 'position2' is the position of a pivot point at the bottom of the trend, then the distance between the two points is given by 'position1' - 'position2'. This distance is used in the calculation of the slope of the trend line.


'different', 'high_line', 'low_location', 'low_value', and 'valid' are variables that are used in the loop that calculates the downward trend lines in the script. They are used to store intermediate values during the calculation process.

'different' is a variable that stores the slope of the downward trend line being calculated. It is calculated as the difference in value between the two pivot points (stored in up_val1 and up_val2) divided by the distance between the pivot points (calculated using their positions, stored in up1 and up2).

'high_line' is a variable that stores the current value of the trend line being calculated at a given point in the loop. It is initialized to the value of the second pivot point (stored in up_val2) and is updated on each iteration of the loop using the value of different.

'low_location' is a variable that stores the position (i.e., bar_index) on the chart of the point where the trend line being calculated first touches the low price. It is initialized to the position of the second pivot point (stored in up2) and is updated on each iteration of the loop if the trend line touches a lower low.

'low_value' is a variable that stores the value of the trend line at the point where it first touches the low price. It is initialized to the value of the second pivot point (stored in up_val2) and is updated on each iteration of the loop if the trend line touches a lower low.

'valid' is a Boolean variable that is used to indicate whether the trend line being calculated is valid. It is initialized to true and is set to false if the trend line does not pass through all the lows between the pivot points. If valid is still true after the loop has completed, then the trend line is considered valid and is drawn on the chart.


d_value1, d_value2, d_position1, and d_position2 are variables that are used in the loop that calculates the upward trend lines in the script. They are used to store intermediate values during the calculation process.

d_value1 and d_value2 are variables that store the values of the pivot points that are used to calculate the upward trend line.

d_position1 and d_position2 are variables that store the positions (i.e., bar indices) of the pivot points that are stored in d_value1 and d_value2, respectively. These positions correspond to the locations of the pivot points on the chart.

The variables d_value1, d_value2, d_position1, and d_position2 have the same function as the variables uv1, uv2, up1, and up2, respectively, but for the calculation of the upward trend lines rather than the downward trend lines. They are used in a similar way to store intermediate values during the calculation process.
