---
title: Data Binding RadChart to a Generic List of Simple Types
page_title: Data Binding RadChart to a Generic List of Simple Types
description: Data Binding RadChart to a Generic List of Simple Types
slug: chart-building-radcharts-data-binding-radchart-to-a-generic-list-of-simple-types
tags: data,binding,radchart,to,a,generic,list,of,simple,types
published: True
position: 8
---

# Data Binding RadChart to a Generic List of Simple Types



The example below is the result of binding a [generic List<>](http://msdn2.microsoft.com/en-us/library/6sh2ey19.aspx)
        of double to the __RadChart__ __DataSource__ property and calling the DataBind() method.

![chart-building-radcharts-data-binding-radchart-to-a-generic-list-of-simple-types 001](images/chart-building-radcharts-data-binding-radchart-to-a-generic-list-of-simple-types001.png)



#### __[C#] Binding to generic list of simple types__

{{source=..\SamplesCS\Chart\DataBindingToGenericListOfSimpleTypes.cs region=bindToGenericListOfSimpleTypes}}
	            List<double> chartData = new List<double>();
	            chartData.Add(34);
	            chartData.Add(45);
	            chartData.Add(56);
	            chartData.Add(67);
	            chartData.Add(78);
	            radChart1.DataSource = chartData;
	{{endregion}}



#### __[VB.NET] Binding to generic list of simple types__

{{source=..\SamplesVB\Chart\DataBindingToGenericListOfSimpleTypes.vb region=bindToGenericListOfSimpleTypes}}
	        Dim chartData As New List(Of Double)()
	        chartData.Add(34)
	        chartData.Add(45)
	        chartData.Add(56)
	        chartData.Add(67)
	        chartData.Add(78)
	        RadChart1.DataSource = chartData
	{{endregion}}

