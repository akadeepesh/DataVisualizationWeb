 # Real-Time Audio Visualizer

**Visualize audio signals from your microphone in real-time using Simple Html and JS!**

## Project Overview

This project creates a dynamic waveform display that visualizes audio captured from your microphone. It leverages the `Smoothie Charts` library for displaying smooth live time lines.

1. Run the server (Please note that this code will only work in a server environment due to the use of `getUserMedia`)

2. Allow microphone access and make sure that input and output devices are connected.

3. Observe the real-time audio waveform on the plot.

## Workflow

1. **Initialize AudioContext**: The `AudioContext` is initialized to handle audio operations in the web browser. It's an interface of the Web Audio API.
2. **Access Microphone**: The `navigator.mediaDevices.getUserMedia` method is used to request access to the user's microphone. This returns a Promise that resolves to a MediaStream object.
3. **Create MediaStreamSource and Analyser**: A `MediaStreamSource` is created from the MediaStream object (which represents the microphone input). An `AnalyserNode`, which is used to expose audio time and frequency data, is also created.
4. **Connect Source and Analyser**: The `MediaStreamSource` (source) is connected to the `AnalyserNode` (analyser). This means the audio data from the microphone will flow through the analyser.
5. **Create TimeSeries for SmoothieChart**: A `TimeSeries` object is created to hold the audio data that will be visualized on the SmoothieChart.
6. **Draw Function**: A `draw` function is defined and called. This function does the following:
   - It calls itself repeatedly using `requestAnimationFrame`, creating a loop.
   - It gets the frequency data from the analyser and stores it in an array (`dataArray`).
   - It calculates the average frequency value.
   - It appends the average frequency value to the `TimeSeries` object, along with the current timestamp.
   - It adds the `TimeSeries` object to the SmoothieChart.
7. **Initialize and Stream to SmoothieChart**: A `SmoothieChart` object is created and the chart is streamed to a `<canvas>` element in the HTML.


## Reference

- [**Smoothie Documentation**](http://smoothiecharts.org/tutorial.html)

## Images
Normal And Audio State:
![Normal](https://github.com/akadeepesh/DataVisualizationWeb/assets/100466756/904ffe0b-4425-4bc2-b855-3fc9956081f4)


Real Time Detection:
![Visualizer](https://github.com/akadeepesh/DataVisualizationWeb/assets/100466756/7ebc042b-d6c3-4744-a342-efc23dca68c0)


