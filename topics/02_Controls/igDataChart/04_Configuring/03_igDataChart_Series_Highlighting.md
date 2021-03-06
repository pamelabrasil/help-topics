﻿<!--
|metadata|
{
    "fileName": "igdatachart-series-highlighting",
    "controlName": "",
    "tags": []
}
|metadata|
-->

# Configuring the Series Highlighting (igDataChart)



##Topic Overview


### Purpose

This topic provides information on enabling the series highlighting feature along with a listing of the supported series. This topic also explains how to configure the series highlighting using the available events.

### Required background

The following topic is a prerequisite to understanding this topic:


[Adding igDataChart](igDataChart-Adding.html)

This topic demonstrates how to add the `igDataChart`™ control to a page and bind it to data.

### In this topic

This topic contains the following sections:

-   [Series Highlighting](#series-highlighting)
    -   [Overview](#overview)
    -   [Preview](#preview)
    -   [Properties](#properties)
    -   [Example](#example)
-   [Events](#events)
    -   [Overview](#events-overview)
    -   [Event Arguments Properties](#event-arguments-properties)
    -   [Example](#event-example)
-   [Related Content](#related-content)



## <a id="series-highlighting"></a>Series Highlighting


### <a id="overview"></a>Overview

This feature allows you to highlight an entire series or individual items within the series. For example, highlights the entire line in a series such as the `lineSeries` as it is all one shape; however, highlights can be applied to each individual column in a series such as `columnSeries`. Individual markers can be highlighted in all supported series.

Currently the feature only supports highlighting via the mouse.

The series highlighting feature is supported for the following series types:

-   Category Series
-   RangeCategory Series

-   Financial Price Series
-   Financial Indicators

### <a id="preview"></a>Preview

The following screenshot is a preview of the `igDataChart` control with a `columnSeries` and the series highlighting feature enabled.

![](images/jQuery_Series_Highlighting_01.png)

### <a id="properties"></a>Properties

The following table summarizes the properties used for series highlighting. These properties are set on the supported series.

<table class="table">
	<tbody>
		<tr>
			<th>
				Property Name
			</th>

			<th>
				Property Type
			</th>

			<th>
				Description
			</th>
		</tr>

		<tr>
			<td>isHighlightingEnabled</td>

			<td>boolean</td>

			<td>
				Enables the series highlighting feature, by default it is set to False.
			</td>
		</tr>

		<tr>
			<td>highlightingTransitionDuration</td>

			<td>timeSpan</td>

			<td>
				Determines the duration that the highlighting change takes.
			</td>
		</tr>
	</tbody>
</table>



### <a id="example"></a>Example

The screenshot, following the table, demonstrates how a chart with the `isHighlightingEnabled` and  `highlightingTransitionDuration` properties of the `columnSeries` looks as a result of the following settings:

<table class="table">
	<tbody>
		<tr>
			<th>
				Property
			</th>

			<th>
				Value
			</th>
		</tr>

		<tr>
			<td>isHighlightingEnabled</td>

			<td>
				True
			</td>
		</tr>

		<tr>
			<td>highlightingTransitionDuration</td>

			<td>
				00:00:10
			</td>
		</tr>
	</tbody>
</table>



![](images/jQuery_Series_Highlighting_01.png)

Following is the code that implements this example:

```
$("#chart").igDataChart({
   ...
   ...
   series: [
      {
         name: "2005Population",
         type: "line",
         title: "2005",
         xAxis: "NameAxis",
         yAxis: "PopulationAxis",
         valueMemberPath: "Pop2005",
         isHighlightingEnabled: true,
         thickness: 5
      },
      {
         name: "1995Population",
         type: "line",
         title: "1995",
         xAxis: "NameAxis",
         yAxis: "PopulationAxis",
         valueMemberPath: "Pop1995",
         isHighlightingEnabled: true,
         thickness: 5
      }
   ]
});
```
## <a id="events"></a>Events


### <a id="events-overview"></a>Overview

There are two events that are specifically related to the series highlighting feature.

-   `assigningCategoryStyle`
-   `assigningCategoryMarkerStyle`

These events can be configured to achieve the following:

-   Modify the way that the highlighting is represented
-   Modify the appearance properties assigned to the entire series such as a `lineSeries`, or each individual item in the series for the series having individual items such as `columnSeries`.

When using the above series to configure the highlighting on the series, only the properties that are available on that particular series can be used. For example, overriding the fill or `radiusX` property of a `lineSeries` does not have any affect since those properties do not affect the `lineSeries`.

### <a id="event-arguments-properties"></a>Event Arguments Properties

The following table summarizes the properties of the `assigningCategoryStyleEventArgsBase`.

<table class="table table-striped">
	<tbody>
		<tr>
			<th>
				Property Name
			</th>

			<th>
				Property Type
			</th>

			<th>
				Description
			</th>
		</tr>

		<tr>
			<td>startIndex</td>

			<td>int</td>

			<td>
				Start index of the range of data that is currently being highlighted.
			</td>
		</tr>

		<tr>
			<td>endIndex</td>

			<td>int</td>

			<td>
				End index of the range of the data that is currently being highlighted.
			</td>
		</tr>

		<tr>
			<td>startDate</td>

			<td>dateTime</td>

			<td>
				Start date of the range of data that is currently being highlighted.
			</td>
		</tr>

		<tr>
			<td>endDate</td>

			<td>dateTime</td>

			<td>
				End date of the range of data that is currently being highlighted.
			</td>
		</tr>

		<tr>
			<td>getItems</td>

			<td>getCategoryItemsEventHandler</td>

			<td>
				Actual items from the data source being highlighted. However, if there is a lot of data and you called it every time the event was fired, will negatively impact performance.
			</td>
		</tr>

		<tr>
			<td>Fill</td>

			<td>brush</td>

			<td>
				Overrides the default fill property of the series. However, this property only takes affect if the Fill property only affects that particular series.
			</td>
		</tr>

		<tr>
			<td>stroke</td>

			<td>brush</td>

			<td>
				Overrides the default stroke property of the series.
			</td>
		</tr>

		<tr>
			<td>
				opacity
			</td>

			<td>double</td>

			<td>
				Overrides the default the opacity property of the series.
			</td>
		</tr>

		<tr>
			<td>highlightingInfo</td>

			<td>higlightingInfo</td>

			<td>
				Determine the styling of the highlighted series.
			</td>
		</tr>

		<tr>
			<td>maxAllSeriesHighlightingProgress</td>

			<td>double</td>

			<td>
				Progress state of the highlighting of the series. Value from 0 to 1.
			</td>
		</tr>

		<tr>
			<td>sumAllSeriesHighlightingProgress</td>

			<td>double</td>

			<td>
				Progress state of the highlighting of the series.

				Value from 0 to 1.
			</td>
		</tr>

		<tr>
			<td>highlightingHandled</td>

			<td>bool</td>

			<td>
				When set to True the default highlighting does not apply.
			</td>
		</tr>

		<tr>
			<td>HasDateRange</td>

			<td>bool</td>

			<td></td>
		</tr>
	</tbody>
</table>



The following table summarizes the properties of the     `assigningCategoryMarkerStyleEventArgs`

<table class="table table-striped">
	<tbody>
		<tr>
			<th>
				Property Name
			</th>

			<th>
				Property Type
			</th>

			<th>
				Description
			</th>
		</tr>

		<tr>
			<td>strokeThickness</td>

			<td>double</td>

			<td>
				Overrides the default StrokeThickness property of the marker.
			</td>
		</tr>

		<tr>
			<td>strokeDashArray</td>

			<td>doubleCollection</td>

			<td>
				Overrides the default StrokeDashArray property of the marker.
			</td>
		</tr>

		<tr>
			<td>strokeDashCap</td>

			<td>penLineCap</td>

			<td>
				Overrides the default StrokeDashCap property of the marker.
			</td>
		</tr>

		<tr>
			<td>radiusX</td>

			<td>double</td>

			<td>
				Overrides the default RadiusX property.
			</td>
		</tr>

		<tr>
			<td>radiusY</td>

			<td>double</td>

			<td>
				Overrides the default RadiusY property.
			</td>
		</tr>
	</tbody>
</table>



### <a id="event-example"></a>Example

The following screenshot displays an example of using the `assigningCategoryStyle` event to change the highlighting feature to fade non highlighting columns instead of changing the highlighting column.

![](images/jQuery_Series_Highlighting_02.png)

Following is the code implemented for this example:

```
$("#chart").igDataChart({
   ...
   series: [{
      name: "2005Population",
      type: "column",
      title: "2005 Population",  
      isHighlightingEnabled: true,
      isTransitionInEnabled: true,
      xAxis: "NameAxis",
      yAxis: "PopulationAxis",
      valueMemberPath: "Pop2005",
      showTooltip: true,
      isCustomCategoryStyleAllowed: true,
      isAssigningCategoryStyleAssigned: true
   }],
   assigningCategoryStyle: function (e, ui) {
      var minOpacity = .3, opacity = 1.0, curr;
      if (ui.sumAllSeriesHighlightingProgress > 0.0) {
         var progress = 0;
         if (ui.highlightingInfo !== null) {
            progress = ui.highlightingInfo.progress;
         }

         progress = progress - ui.sumAllSeriesHighlightingProgress;
         opacity = minOpacity + (1.0 + progress) * (1.0 - minOpacity);
         ui.opacity = opacity;
         ui.highlightingHandled = true;         
      }
   }
});
```

## <a id="related-content"></a>Related Content


### Topics

The following topic provides additional information related to this topic:


-	[Adding igDataChart](igDataChart-Adding.html):  This topic demonstrates how to add the `igDataChart` control to a page and bind it to data.


### Samples

The following sample provides additional information related to this topic.

-	[Series Highlighting](%%SamplesUrl%%/data-chart/series-highlighting):  This sample demonstrates the series highlighting feature which allows you to highlight either an entire series or individual items within a series.

-	[Series Highlighting (Financial)](%%SamplesUrl%%/data-chart/series-highlighting-financial): This sample demonstrates the series highlighting feature which allows you to highlight the financial series.

-	[Custom Series Highlighting](%%SamplesUrl%%/data-chart/custom-series-highlighting):  This sample demonstrates how to use the `assigningCategoryStyle` event to change the highlighting to fade non highlighted columns instead of changing the highlighted column.





 

 


