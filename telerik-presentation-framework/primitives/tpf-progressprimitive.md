---
title: ProgressBarPrimitive
page_title: ProgressBarPrimitive
description: ProgressBarPrimitive
slug: tpf-primitives-progressprimitive
tags: progressbarprimitive
published: True
position: 11
---

# ProgressBarPrimitive



## 

ProgressBarPrimitive is a specialized descendant of [FillPrimitive]({%slug tpf-primitives-fillprimitive%}) that 
        indicates the state of progress in a long running process. The fill area is controlled by the __GradientStyle__and the 
          __BackColor__..__BackColor4__ properties. The fill covers the percentage area between 
          __Minimum__and __Maximum__specified by the __Value1__property. 
          __Value1__ is rendered using up to all four colors. __Value2__ displays in the __BackColor__ at 
          25% opacity. __Orientation__controls the starting point of the fill and can originate from __Left__, 
          __Right__, __Top__or __Bottom__. The example below shows a Linear fill for 
          __Value1__(set to 20), and a pale Aqua for __Value2__(set to 70).![tpf-primitives-progressprimitive 001](images/tpf-primitives-progressprimitive001.png)

#### __[C#] Creating a ProgressBarPrimitive__

{{source=..\SamplesCS\TPF\Primitives\ProgressBarPrimitive1\MyProgressBarPrimitiveElement.cs region=myProgressBarPrimitiveElement}}
	    public class MyProgressBarPrimitiveElement : RadElement
	    {
	        protected override void CreateChildElements()
	        {
	            BorderPrimitive borderPrimitive = new BorderPrimitive();
	            borderPrimitive.BoxStyle = BorderBoxStyle.OuterInnerBorders;
	            borderPrimitive.GradientStyle = GradientStyles.Solid;
	            borderPrimitive.ForeColor = Color.Blue;
	            borderPrimitive.InnerColor = Color.LightSkyBlue;  
	            ProgressBarPrimitive progressBarPrimitive = new ProgressBarPrimitive();
	            progressBarPrimitive.GradientStyle = GradientStyles.Linear;
	            progressBarPrimitive.NumberOfColors = 4;
	            progressBarPrimitive.Orientation = ProgressOrientation.Left;
	            progressBarPrimitive.Value1 = 20;
	            progressBarPrimitive.Value2 = 70;
	            progressBarPrimitive.Minimum = 1;
	            progressBarPrimitive.Maximum = 100;
	            progressBarPrimitive.BackColor = Color.Aqua;
	            progressBarPrimitive.BackColor2 = Color.Blue;
	            progressBarPrimitive.BackColor3 = Color.SkyBlue;
	            progressBarPrimitive.BackColor4 = Color.LightSkyBlue;
	            borderPrimitive.ZIndex = 1;
	            this.Children.Add(borderPrimitive);
	            this.Children.Add(progressBarPrimitive);
	            base.CreateChildElements();
	        }
	    }
	{{endregion}}



#### __[VB.NET] Creating a ProgressBarPrimitive__

{{source=..\SamplesVB\TPF\Primitives\ProgressBarPrimitive1\MyProgressBarPrimitiveElement.vb region=myProgressBarPrimitiveElement}}
	Public Class MyProgressBarPrimitiveElement
	    Inherits RadElement
	    Protected Overrides Sub CreateChildElements()
	        Dim borderPrimitive As New BorderPrimitive()
	        borderPrimitive.BoxStyle = BorderBoxStyle.OuterInnerBorders
	        borderPrimitive.GradientStyle = GradientStyles.Solid
	        borderPrimitive.ForeColor = Color.Blue
	        borderPrimitive.InnerColor = Color.LightSkyBlue
	        Dim progressBarPrimitive As New ProgressBarPrimitive()
	        progressBarPrimitive.GradientStyle = GradientStyles.Linear
	        progressBarPrimitive.NumberOfColors = 4
	        progressBarPrimitive.Orientation = ProgressOrientation.Left
	        progressBarPrimitive.Value1 = 20
	        progressBarPrimitive.Value2 = 70
	        progressBarPrimitive.Minimum = 1
	        progressBarPrimitive.Maximum = 100
	        progressBarPrimitive.BackColor = Color.Aqua
	        progressBarPrimitive.BackColor2 = Color.Blue
	        progressBarPrimitive.BackColor3 = Color.SkyBlue
	        progressBarPrimitive.BackColor4 = Color.LightSkyBlue
	        borderPrimitive.ZIndex = 1
	        Me.Children.Add(borderPrimitive)
	        Me.Children.Add(progressBarPrimitive)
	        MyBase.CreateChildElements()
	    End Sub
	End Class
	{{endregion}}

