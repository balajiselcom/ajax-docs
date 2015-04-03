---
title: Data Binding Overview
page_title: Overview | UI for ASP.NET AJAX Documentation
description: Overview
slug: scheduler/data-binding/overview
tags: overview
published: True
position: 0
---

# Data Binding Overview



## 

__RadScheduler__ requires some sort of data binding so that it can store and retrieve the informationit displays about appointments. At a minimum, the data for the scheduler must include for each appointment a__Subject__, a __Start time__, and an __End time__.Optionally, it can include fields for __Description, Reminder__ and for handling appointmentrecurrence: the __Recurrence rule__, the __Recurrence state__, and the__RecurrenceParentID__. It can also include fields for any custom resources and attributes youwant to include. If you are including custom resources, there must also be additional data binding to supply the schedulerwith the possible values for each custom resource type.

You can bind the scheduler to either a standard ASP.NET data source control, or to a custom provider. There are three waysof binding __RadScheduler__ to its data:

* Using [ASP.NET 2.0 declarative data source controls]({%slug scheduler/data-binding/declarative-data-binding%}). This method lets you use the [ Data Source Configuration Wizard ]({%slug scheduler/design-time/data-source-configuration-wizard%}) to set up the data binding in the designer. It is the simplest method of data binding. When using declarative data source controls, you can't assign multiple resource values to a single appointment.

* Using the [DataSource property]({%slug scheduler/data-binding/using-the-data-source-property%}). This method lets you bind the scheduler to any object that implements the IListSource or IEnumerable interface. However, when binding the scheduler in this way, you must either make the scheduler read-only, or implement the code to insert, update, and delete appointments using the __RadScheduler__ server-side events. When using the __DataSource__ property, you can't assign multiple resource values to a single appointment.

* Using a [Data Provider]({%slug scheduler/data-binding/providers/using-a-data-provider%}). This method is the most flexible, but also the most complicated to implement. This is the only method that lets you assign multiple resource values to a single appointment.