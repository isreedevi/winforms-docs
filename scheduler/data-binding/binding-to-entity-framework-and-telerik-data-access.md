---
title: Binding to EntityFramework and Telerik Data Access
page_title: Binding to EntityFramework and Telerik Data Access
description: Binding to EntityFramework and Telerik Data Access
slug: scheduler-data-binding-binding-to-entity-framework-and-telerik-data-access
tags: binding,to,entityframework,and,telerik,data,access
published: True
position: 13
---

# Binding to EntityFramework and Telerik Data Access



Binding to an ORM is similar to binding to a [DataSet]({%slug scheduler-data-binding-using-datasource-property%}). First you will need to create the models out of an existing database.
        You can read how to do that for Entity Framework [
            here
          ](
            http://msdn.microsoft.com/en-us/data/jj206878.aspx
          ). And for Telerik Data Access [
            here
          ](
            http://docs.telerik.com/data-access/getting-started/getting-started-root-generating-model-mappings-taking-database-first-approach
          ).
      

For the purpose of this tutorial you can download a sample database from the [
            here
          ](
            http://www.telerik.com/docs/default-source/ui-for-winforms/schedulerdatasql.zip
          ).
      

## 

After you have mapped your database to local entities your tables should look like this:![scheduler data binding binding to entity framework and telerik data access001](images/scheduler-data-binding-binding-to-entity-framework-and-telerik-data-access001.png)

Now, you need to create a form and add a RadScheduler, in this tutorial it is named *scheduler*. After this we will need to access out data from the database. For this we will need a [DbContext](http://msdn.microsoft.com/en-us/library/system.data.entity.dbcontext(v=vs.113).aspx) reference. In my case my DbContext is of type __SchedulerDataEntities1__, so we can create it as follows:
        

#### __[C#] __

{{source=..\SamplesCS\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.cs region=DbContext}}
	        private SchedulerDataEntities1 dbContext = new SchedulerDataEntities1();
	{{endregion}}



#### __[VB.NET] __

{{source=..\SamplesVB\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.vb region=DbContext}}
	    Private dbContext As New SchedulerDataEntities1()
	{{endregion}}



Then, we will need a __SchedulerBindingDataSource__, __AppointmentMappingInfo__ and __ResourceMappingInfo__ which we will use to map our data. You can create them in the Form's constructor.
        

#### __[C#] __

{{source=..\SamplesCS\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.cs region=Mappings}}
	            SchedulerBindingDataSource schedulerBindingSource = new SchedulerBindingDataSource();
	            AppointmentMappingInfo appointmentMappingInfo = new AppointmentMappingInfo();
	            ResourceMappingInfo resourceMappingInfo = new ResourceMappingInfo();
	{{endregion}}



#### __[VB.NET] __

{{source=..\SamplesVB\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.vb region=Mappings}}
	        Dim schedulerBindingSource As New SchedulerBindingDataSource()
	        Dim appointmentMappingInfo As New AppointmentMappingInfo()
	        Dim resourceMappingInfo As New ResourceMappingInfo()
	{{endregion}}



Now you just need to setup the mappings. The approaches for *Entity Framework* and *Telerik Data Access* are a bit different.
        

Below you can see the code you need to use with *Entity Framework*:
        

#### __[C#] __

{{source=..\SamplesCS\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.cs region=EFCode}}
	            dbContext.Appointments.Load();
	            dbContext.Resources.Load();
	
	            appointmentMappingInfo.BackgroundId = "BackgroundID";
	            appointmentMappingInfo.Description = "Description";
	            appointmentMappingInfo.End = "End";
	            appointmentMappingInfo.Exceptions = "FK_Appointments_Appointments";
	            appointmentMappingInfo.Location = "Location";
	            appointmentMappingInfo.MasterEventId = "ParentID";
	            appointmentMappingInfo.RecurrenceRule = "RecurrenceRule";
	            appointmentMappingInfo.ResourceId = "ID";
	
	            appointmentMappingInfo.Resources = "Resources";
	
	            appointmentMappingInfo.Start = "Start";
	            appointmentMappingInfo.StatusId = "StatusID";
	            appointmentMappingInfo.Summary = "Summary";
	            appointmentMappingInfo.Visible = "Visible";
	
	            schedulerBindingSource.EventProvider.Mapping = appointmentMappingInfo;
	
	            resourceMappingInfo.Id = "ID";
	            resourceMappingInfo.Name = "ResourceName";
	            schedulerBindingSource.ResourceProvider.Mapping = resourceMappingInfo;
	
	            schedulerBindingSource.ResourceProvider.DataSource = dbContext.Resources.Local.ToBindingList();
	            schedulerBindingSource.EventProvider.DataSource = dbContext.Appointments.Local.ToBindingList();
	{{endregion}}



#### __[VB.NET] __

{{source=..\SamplesVB\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.vb region=EFCode}}
	        dbContext.Appointments.Load()
	        dbContext.Resources.Load()
	
	        appointmentMappingInfo.BackgroundId = "BackgroundID"
	        appointmentMappingInfo.Description = "Description"
	        appointmentMappingInfo.[End] = "End"
	        appointmentMappingInfo.Exceptions = "FK_Appointments_Appointments"
	        appointmentMappingInfo.Location = "Location"
	        appointmentMappingInfo.MasterEventId = "ParentID"
	        appointmentMappingInfo.RecurrenceRule = "RecurrenceRule"
	        appointmentMappingInfo.ResourceId = "ID"
	
	        appointmentMappingInfo.Resources = "Resources"
	
	        appointmentMappingInfo.Start = "Start"
	        appointmentMappingInfo.StatusId = "StatusID"
	        appointmentMappingInfo.Summary = "Summary"
	        appointmentMappingInfo.Visible = "Visible"
	
	        schedulerBindingSource.EventProvider.Mapping = appointmentMappingInfo
	
	        resourceMappingInfo.Id = "ID"
	        resourceMappingInfo.Name = "ResourceName"
	        schedulerBindingSource.ResourceProvider.Mapping = resourceMappingInfo
	
	        schedulerBindingSource.ResourceProvider.DataSource = dbContext.Resources.Local.ToBindingList()
	        schedulerBindingSource.EventProvider.DataSource = dbContext.Appointments.Local.ToBindingList()
	{{endregion}}



>importantIn order to use the __Load__ extension method you need to add *System.Data.Entity* to your usings(C#) or Imports(VB).
          

And the following code needs to be used with *Telerik Data Access*:
        

#### __[C#] __

{{source=..\SamplesCS\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.cs region=TDACode}}
	            appointmentMappingInfo.BackgroundId = "BackgroundID";
	            appointmentMappingInfo.Description = "Description";
	            appointmentMappingInfo.End = "End";
	            appointmentMappingInfo.Exceptions = "FK_Appointments_Appointments";
	            appointmentMappingInfo.Location = "Location";
	            appointmentMappingInfo.MasterEventId = "ParentID";
	            appointmentMappingInfo.RecurrenceRule = "RecurrenceRule";
	            appointmentMappingInfo.ResourceId = "ResourceID";
	            appointmentMappingInfo.Resources = "AppointmentsResources";
	            appointmentMappingInfo.Start = "Start";
	            appointmentMappingInfo.StatusId = "StatusID";
	            appointmentMappingInfo.Summary = "Summary";
	            appointmentMappingInfo.Visible = "Visible";
	            
	            this.schedulerBindingSource.EventProvider.Mapping = appointmentMappingInfo1;
	            
	            resourceMappingInfo.Id = "ID";
	            resourceMappingInfo.Name = "ResourceName";
	            schedulerBindingSource.ResourceProvider.Mapping = resourceMappingInfo1;
	
	            schedulerBindingDataSource.ResourceProvider.DataSource = entityContext.Resources.ToList();
	            schedulerBindingDataSource.EventProvider.DataSource = entityContext.Appointments.ToList();
	{{endregion}}



#### __[VB.NET] __

{{source=..\SamplesVB\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.vb region=TDACode}}
	        appointmentMappingInfo.BackgroundId = "BackgroundID"
	        appointmentMappingInfo.Description = "Description"
	        appointmentMappingInfo.[End] = "End"
	        appointmentMappingInfo.Exceptions = "FK_Appointments_Appointments"
	        appointmentMappingInfo.Location = "Location"
	        appointmentMappingInfo.MasterEventId = "ParentID"
	        appointmentMappingInfo.RecurrenceRule = "RecurrenceRule"
	        appointmentMappingInfo.ResourceId = "ResourceID"
	        appointmentMappingInfo.Resources = "AppointmentsResources"
	        appointmentMappingInfo.Start = "Start"
	        appointmentMappingInfo.StatusId = "StatusID"
	        appointmentMappingInfo.Summary = "Summary"
	        appointmentMappingInfo.Visible = "Visible"
	
	        Me.schedulerBindingSource.EventProvider.Mapping = appointmentMappingInfo1
	
	        resourceMappingInfo.Id = "ID"
	        resourceMappingInfo.Name = "ResourceName"
	        schedulerBindingSource.ResourceProvider.Mapping = resourceMappingInfo1
	
	        schedulerBindingDataSource.ResourceProvider.DataSource = entityContext.Resources.ToList()
	        schedulerBindingDataSource.EventProvider.DataSource = entityContext.Appointments.ToList()
	{{endregion}}



The last step that you need to take in order to complete the binding process is to assign the DataSource property of RadScheduler and group it by resource:
        

#### __[C#] __

{{source=..\SamplesCS\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.cs region=DataSourceAndGroup}}
	            this.scheduler.DataSource = schedulerBindingSource;
	            this.scheduler.GroupType = GroupType.Resource;
	{{endregion}}



#### __[VB.NET] __

{{source=..\SamplesVB\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.vb region=DataSourceAndGroup}}
	        Me.scheduler.DataSource = schedulerBindingSource
	{{endregion}}



Saving changes to the database happens when the __SaveChanges__ method of the DbContext is invoked. You can invoke it on a button click or when the form is closing:
        

#### __[C#] __

{{source=..\SamplesCS\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.cs region=Closing}}
	        protected override void OnClosing(CancelEventArgs e)
	        {
	            this.dbContext.SaveChanges();
	            base.OnClosing(e);
	        }
	{{endregion}}



#### __[VB.NET] __

{{source=..\SamplesVB\Scheduler\DataBinding\BindingToEntityFrameworkAndTelerikDataAccess.vb region=Closing}}
	    Protected Overrides Sub OnClosing(e As CancelEventArgs)
	        Me.dbContext.SaveChanges()
	        MyBase.OnClosing(e)
	    End Sub
	{{endregion}}

