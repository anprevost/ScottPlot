# ScottPlot

***ScottPlot is an open-source interactive graphing library for .NET written in C#.*** The core of this project is a portable class library which allows a user to supply figure dimensions and scale information and plot data directly on a bitmap buffer relying on ScottPlot to handle unit-to-pixel conversions, drawing of axis labels, tick marks, grid lines, etc. Although ScottPlot was designed with highspeed interactive graphing of large datasets in a GUI environment, its core can generate graphs from within console applications. ScottPlot was loosely inspired by matplotlib for Python.

> **WARNING: THIS PROJECT IS NOT READY FOR WIDESPREAD USE!** ScottPlot is still in the very early stages of development. Its API has not yet solidified, so building projects around it is not yet recommended. At this time, this repository is intended to track the development of this projet (rather than distribute it).

### Example:
```C#
Figure fig = new Figure(640, 480);
fig.title = "ScottPlot Demonstration";
fig.xLabel = "Elapsed Time (years)";
fig.yLabel = "Total Awesomeness (cool units)";
fig.Axis(-15, 35, -10, 110); // x1, x2, y1, y2

// update the Frame (axis labels, tick marks, etc)
fig.RedrawFrame();

// draw a line directly on the Graphics object in AXIS units
Point pt1 = new Point(fig.xAxis.UnitToPx(0), fig.yAxis.UnitToPx(13));
Point pt2 = new Point(fig.xAxis.UnitToPx(32), fig.yAxis.UnitToPx(98));
fig.gfxGraph.DrawLine(new Pen(new SolidBrush(Color.Blue), 5), pt1, pt2);

// save the file
fig.Save("test.png");
```

### Output:
<img src="/doc/test.png" width="640">
