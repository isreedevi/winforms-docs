---
title: Busy Indicators
page_title: Busy Indicators | UI for WinForms Documentation
description: Busy Indicators
slug: winforms/virtualgrid/busy-indicators
tags: virtualgrid, busy, indicators
published: True
position: 16
---

# Busy Indicators

There are two ways to indicate that the grid need time to perform a specific operation. The first one is to show a waiting bar in front of __RadVirtualGrid__. This way the entire control will be unaccessible while the time consuming operation is executed. The second one is to show a waiting icon in the row header. This way you can indicate that a the data for a specific row is still not loaded.

## WatingBar

While this indicator is shown the entire grid is disabled. It is useful when the initial data loading requires more time.

![virtualgrid-busy-indicators001](images/virtualgrid-busy-indicators001.gif)        

The following snippet shows how you can show/hide the waiting bar:

{{source=..\SamplesCS\VirtualGrid\VirtualGridWaitingIndicators.cs region=WaitingBar}} 
{{source=..\SamplesVB\VirtualGrid\VirtualGridWaitingIndicators.vb region=WaitingBar}}
````C#
radVirtualGrid1.MasterViewInfo.IsWaiting = true;
radVirtualGrid1.MasterViewInfo.IsWaiting = false;

````
````VB.NET
radVirtualGrid1.MasterViewInfo.IsWaiting = True
radVirtualGrid1.MasterViewInfo.IsWaiting = False

```` 

{{endregion}}


## Waiting icon

The waiting icon can be shown in each row header. With it you can indicate that the row data is still not loaded.

![virtualgrid-busy-indicators002](images/virtualgrid-busy-indicators002.gif)


The following snippet shows how you can show/hide the waiting icon:

{{source=..\SamplesCS\VirtualGrid\VirtualGridWaitingIndicators.cs region=icon}} 
{{source=..\SamplesVB\VirtualGrid\VirtualGridWaitingIndicators.vb region=icon}}
````C#
radVirtualGrid1.MasterViewInfo.StartRowWaiting(5);
radVirtualGrid1.MasterViewInfo.StopRowWaiting(5);

````
````VB.NET
radVirtualGrid1.MasterViewInfo.StartRowWaiting(5)
radVirtualGrid1.MasterViewInfo.StopRowWaiting(5)

```` 

{{endregion}}