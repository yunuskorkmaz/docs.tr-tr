---
title: DataView Yönetme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: c07f521b94f23b479281b0314d6b89a095ee9624
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181251"
---
# <a name="managing-dataviews"></a>DataView Yönetme

Bir <xref:System.Data.DataViewManager> içindeki tüm tablolar için görünüm ayarlarını yönetmek üzere bir kullanabilirsiniz <xref:System.Data.DataView> . İlişkilerde gezinen bir kılavuz gibi birden çok tabloya bağlamak istediğiniz bir denetiminiz varsa, bir **DataViewManager** idealdir.  
  
 **DataViewManager** , <xref:System.Data.DataViewSetting> içindeki tabloların görünüm ayarını ayarlamak için kullanılan nesnelerin bir koleksiyonunu içerir <xref:System.Data.DataSet> . , <xref:System.Data.DataViewSettingCollection> <xref:System.Data.DataViewSetting> Bir **veri kümesindeki**her tablo için bir nesne içerir. Başvurulan tablonun varsayılan **ApplyDefaultSort**, **Sort**, **RowFilter**ve **RowStateFilter** özelliklerini **DataViewSetting**kullanarak ayarlayabilirsiniz. Belirli bir tablo için, ada veya sıralı başvuruya göre veya ilgili tablo nesnesine bir başvuru geçirerek **DataViewSetting** 'a başvurabilirsiniz. **DataViewSettings** özelliğini kullanarak **DataViewManager** içindeki **DataViewSetting** nesneleri koleksiyonuna erişebilirsiniz.  
  
 Aşağıdaki kod örneği bir **veri kümesini** SQL Server **Northwind** veritabanı tabloları **müşteriler**, **siparişler**ve **sipariş ayrıntıları**ile doldurur, tablolar arasındaki ilişkileri oluşturur, varsayılan **DataView** ayarlarını ayarlamak için bir **DataViewManager** kullanır ve bir **DataGrid** 'i **DataViewManager**öğesine bağlar. Örnek, **veri kümesindeki** tüm tablolar için varsayılan **DataView** ayarlarını tablosunun birincil anahtarına (**ApplyDefaultSort**  =  **true**) göre sıralar ve ardından, **Customers** tablosunun sıralama düzenini **CompanyName**olarak değiştirir.  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
