# Audio-Lab
CS 5323: Mobile Apps Sensing &amp; Learning In-Class Assignment 2

Created by: Reece Iriye, Chris Miller, Rafe Forward, Ethan Haugen

For Thought Questions:
1. If you made the FFT Magnitude Buffer a larger array, would your program still work properly? If yes, why? If not, what would you need to change?

It would still work properly because we use `fftData.count` in the `AudioModel` with the following line:

```{swift}
let windowSize = fftData.count / 20
```
This line determines our bucket sizes, and we do not hard-code any buffer size. However, if we were to change the magnitude array size from 20 to another size, we would have issues because we hard coded it to 20 buckets. The only change necessary would be to change the math to use fft magnitude array's size.

3. Is pausing the audioManager object better than deallocating it when the view has disappeared (explain your reasoning)?

   Pausing is better than deallocating because that way we can save our place in the audio file and keep all of the data withing the buffers. Plus, it doesn't make sense to deallocate it every time the view disappears when a user has the ability to toggle in and out of the view freely.
