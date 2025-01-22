# README: Performance Evaluation of Scatter Plots in Bokeh

## Background

Starrydata contains a vast number of data points, and while the **Starrydata Visualizer** enables users to view this data, datasets with hundreds of thousands of points in a single XY graph result in an initial rendering time of over 10 seconds, which significantly impacts usability. Despite this, Bokeh was chosen as it outperformed other libraries in initial trials (although precise records of these comparisons were not maintained).

---

## Experiment Overview

Four types of HTML files were generated to measure and compare the performance of the following:

1. **Initial Rendering Time**
2. **Highlight Feature Speed**, the main functionality of the Starrydata Visualizer.

---

## Experimental Setup

- **Hardware**: Development & analysis MacBook
  - **Chip**: Apple M3 Max
  - **Memory**: 128GB
  - **OS**: macOS Sonoma 14.5

- **Initial Rendering Time Measurement**:
  Utilized the Google Chrome extension **Page Load Time**.

- **Highlight Feature Speed Measurement**:
  Recorded manually using an iPhone stopwatch.

### Initial Rendering Details

*(This section will be further elaborated upon with specific results or observations.)*
