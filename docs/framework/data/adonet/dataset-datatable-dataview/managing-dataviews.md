---
title: DataView Yönetme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: c6dcc206775866fd9136e4f6f5f038d021d11433
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204678"
---
# <a name="managing-dataviews"></a>DataView Yönetme
<xref:System.Data.DataViewManager> Bir<xref:System.Data.DataView>içindeki tüm tablolar için görünüm ayarlarını yönetmek üzere bir kullanabilirsiniz. İlişkilerde gezinen bir kılavuz gibi birden çok tabloya bağlamak istediğiniz bir denetiminiz varsa, bir **DataViewManager** idealdir.  
  
 **DataViewManager** , içindeki <xref:System.Data.DataViewSetting> <xref:System.Data.DataSet>tabloların görünüm ayarını ayarlamak için kullanılan nesnelerin bir koleksiyonunu içerir. , <xref:System.Data.DataViewSettingCollection> Bir **veri kümesindeki**her tablo için bir <xref:System.Data.DataViewSetting> nesne içerir. Başvurulan tablonun varsayılan **ApplyDefaultSort**, **Sort**, **RowFilter**ve **RowStateFilter** özelliklerini **DataViewSetting**kullanarak ayarlayabilirsiniz. Belirli bir tablo için, ada veya sıralı başvuruya göre veya ilgili tablo nesnesine bir başvuru geçirerek **DataViewSetting** 'a başvurabilirsiniz. **DataViewSettings** özelliğini kullanarak **DataViewManager** içindeki **DataViewSetting** nesneleri koleksiyonuna erişebilirsiniz.  
  
 Aşağıdaki kod örneği bir **veri kümesini** SQL Server **Northwind** veritabanı tabloları **müşteriler**, **siparişler**ve **sipariş ayrıntıları**ile doldurur, tablolar arasındaki ilişkileri oluşturur, bir **DataViewManager** kullanır Varsayılan **DataView** ayarlarını ayarlayın ve bir **DataGrid** ' i **DataViewManager**öğesine bağlar. Örnek, **veri kümesindeki** tüm tablolar için varsayılan **DataView** ayarlarını tablosunun birincil anahtarına (**ApplyDefaultSort** = **true**) göre sıralar ve ardından **müşteriler** tablosunun sıralama düzenini değiştirir. **CompanyName**'e göre sıralayın.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
