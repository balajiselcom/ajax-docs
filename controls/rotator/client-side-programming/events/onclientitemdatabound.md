---
title: OnClientItemDataBound
page_title: OnClientItemDataBound | UI for ASP.NET AJAX Documentation
description: OnClientItemDataBound
slug: rotator/client-side-programming/events/onclientitemdatabound
tags: onclientitemdatabound
published: True
position: 12
---

# OnClientItemDataBound



This article demonstrates how the __OnClientItemDataBound__ event can be used to manipulate the items of a __RadRotator__ bound to a client-side data source.

## 

The __OnClientItemDataBound__ event is raised when an item in the Rotator is bound to the provided data source.

The event handler receives two parameters:

1. The __RadRotator__ instance that fired the event.

1. An event arguments object containing the following methods:

* __get_dataItem()__ - returns the client-side data object to the Rotator item.

* __get_item()__ - returns the client-side object of the Rotator item.

__Example 1__ demonstrates how to use a data source field of the bound item to locate the index of the rendered Rotator item,using the __OnClientItemDataBound__ event.

__Example 1__: Using the __OnClientItemDataBound__ event's arguments in Client-side logic.

````ASPNET
		<telerik:RadClientDataSource runat="server" ID="RadClientDataSource1" PageSize="5" AllowPaging="true">
			<DataSource>
				<WebServiceDataSourceSettings BaseUrl="http://demos.kendoui.com/service/">
					<Select Url="Products" DataType="JSONP" />
				</WebServiceDataSourceSettings>
			</DataSource>
		</telerik:RadClientDataSource>
	
		<telerik:RadRotator runat="server" ID="Rotator" ClientDataSourceID="RadClientDataSource1" 
			OnClientItemDataBound="OnClientItemDataBound">
			<ClientTemplate>
	            <span class="productName">#= ProductName #</span>
			</ClientTemplate>
		</telerik:RadRotator>
	
		<script type="text/javascript">
			function OnClientItemDataBound(sender, args) {
				var productID = args.get_dataItem().ProductID; // The ProductID is an existing field in the retrieved data object
				var itemsIndex = args.get_item().get_index();
				alert("Product with ID " + productID + " is bound to the item at position " + (itemsIndex + 1));
			}
		</script>
````



# See Also

 * [RadRotator Client-Side API]({%slug rotator/client-side-programming/overview%})

 * [Client-side Data Binding]({%slug rotator/data-binding/client-side-data-binding%})

 * [OnClientDataBound]({%slug rotator/client-side-programming/events/onclientdatabound%})