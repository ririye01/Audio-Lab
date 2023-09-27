# Audio In-Class Assignment
CS 5323: Mobile Apps Sensing &amp; Learning In-Class Assignment 2

Created by: Reece Iriye, Chris Miller, Rafe Forward, Ethan Haugen

For Thought Questions:
1. If you made the FFT Magnitude Buffer a larger array, would your program still work properly? If yes, why? If not, what would you need to change?

It would still work properly because we use `fftData.count` in the `AudioModel` with the following lines working:

```{swift}
// Window size for each slice of the FFT array
let windowSize = fftData.count / maxDataSize20.count

// Use vDSP_maxv to get the maximum value for each window
for i in 0..<maxDataSize20.count {
   ...
}
```
These lines determine our bucket sizes, and we do not hard-code any buffer size. If we were to change the magnitude array size from 20 to another size, the `windowSize` value change would account for the change in size of the magnitude array, and the loop would iterate through however many times is needed.

2. Is pausing the `audioManager` object better than deallocating it when the view has disappeared (explain your reasoning)?

Pausing the `audioManager` object is generally more favorable than deallocating it when the view disappears. If the user returns to the view, the program would need to reallocate and reinitialize the Novocaine audio resources every single time, leading to a slight potential performance overhead and a possible delay in resuming playback. Especially if the user is repetitvely switching between views, this can be costly when done on repeat. 
