---
title: Alternating Row Color
page_title: Alternating Row Color | UI for WinForms Documentation
description: Alternating Row Color
slug: winforms/virtualgrid/rows/alternating-row-colors
tags: virtualgrid, rows, alternating, color
published: True
position: 2
---

# Alternating Row Color

__RadVirtualGrid__ supports an alternating row color. It can be enabled by simply setting the __EnableAlternatingRowColor__ to *true*.

>caption Fig.1 Alternating Row color
![virtualgrid-rows-alternating-row-color001](images/virtualgrid-rows-alternating-row-color001.png)

{{source=..\SamplesCS\VirtualGrid\Rows\VirtualGridRowsAlternatingRownColor.cs region=Settings}} 
{{source=..\SamplesVB\VirtualGrid\Rows\VirtualGridRowsAlternatingRownColor.vb region=Settings}} 

````C#
this.radVirtualGrid1.EnableAlternatingRowColor = true;
this.radVirtualGrid1.TableElement.AlternatingRowColor = Color.LightBlue;

````
````VB.NET
Me.RadVirtualGrid1.EnableAlternatingRowColor = True
Me.RadVirtualGrid1.TableElement.AlternatingRowColor = Color.LightBlue

````

{{endregion}}