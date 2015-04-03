---
title: Auto-Generated Editors
page_title: Auto-Generated Editors | UI for ASP.NET AJAX Documentation
description: Auto-Generated Editors
slug: grid/data-editing/grid-editors/auto-generated-editors
tags: auto-generated,editors
published: True
position: 0
---

# Auto-Generated Editors



Editable columns inside a __RadGrid__ control supply a default editor that enables users to edit the values in the column. The editor is specified by the __ColumnEditor__ property of the column, which is of type __IGridColumnEditor__.

>note Editable columns are columns that implement the __IGridEditableColumn__ interface.
>


## Default Column Editors

The following table lists the default column editors for each of the built-in editable column types:


>caption  

| Column type | Default column editor | Column editor base class |
| ------ | ------ | ------ |
|GridBoundColumn|GridTextBoxColumnEditor|GridTextColumnEditor|
|GridDropDownColumn|GridDropDownListColumnEditor|GridDropDownColumnEditor|
|GridCheckBoxColumn|GridCheckBoxListColumnEditor|GridBoolColumnEditor|
|GridDateTimeColumn|GridDateTimeColumnEditor|GridTextColumnEditor|
|GridNumericColumn|GridNumericColumnEditor|GridTextColumnEditor|
|GridMaskedColumn|GridMaskedColumnEditor|GridTextColumnEditor|
|GridHTMLEditorColumn|GridHTMLEditorColumnEditor|GridTextColumnEditor|
|GridTemplateColumn|GridTemplateColumnEditor|GridColumnEditorBase|
|GridBinaryImageColumn|GridBinaryImageColumnEditor|GridColumnEditorBase|



>caution The purpose of column editors is to define the style of the controls in edit mode. Note that using column editors for modifying the functionality of the edit controls is not recommended.
>


## Accessing the column editors programmatically

The autogenerated column editor is available when the item is in *edit* mode.

>tabbedCode

````XML
	<MasterTableView ...>
	  <Columns>
	    <telerik:GridNumericColumn UniqueName="MyNumericColumn" DataField="ItemNumber" ... />
	  </Columns>
	</MasterTableView>			
````



````C#
	    protected void RadGrid1_ItemCreated(object sender, GridItemEventArgs e)
	    {
	        if (e.Item.IsInEditMode)
	        {
	            GridEditableItem item = e.Item as GridEditableItem;
	            GridNumericColumnEditor numericEditor = (GridNumericColumnEditor)item.EditManager.GetColumnEditor("MyNumericColumn");
	        }
	    }
````



````VB.NET
	    Protected Sub RadGrid1_ItemCreated(ByVal sender As Object, ByVal e As GridItemEventArgs) Handles RadGrid1.ItemCreated
	        If e.Item.IsInEditMode Then
	            Dim item As GridEditableItem = TryCast(e.Item, GridEditableItem)
	            Dim numericEditor As GridNumericColumnEditor = DirectCast(item.EditManager.GetColumnEditor("MyNumericColumn"), GridNumericColumnEditor)
	        End If
	    End Sub
````


>end

## Custom column editors

You can replace the default column editor with a [custom editor]({%slug grid/data-editing/grid-editors/custom-editors-extending-auto-generated-editors%}). By supplying a custom column editor, you can provide a column with enhanced functionality such as validation, rich-text editing, third-party controls, and so on.

Once created, you can easily re-use your custom column editors for other grid implementations.