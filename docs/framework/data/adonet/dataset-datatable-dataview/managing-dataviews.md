---
title: DataView Yönetme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: 5e85fccddf6359791ea702667a36b44f611815dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784496"
---
# <a name="managing-dataviews"></a><span data-ttu-id="5e9e7-102">DataView Yönetme</span><span class="sxs-lookup"><span data-stu-id="5e9e7-102">Managing DataViews</span></span>
<span data-ttu-id="5e9e7-103"><xref:System.Data.DataViewManager> Bir<xref:System.Data.DataView>içindeki tüm tablolar için görünüm ayarlarını yönetmek üzere bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-103">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="5e9e7-104">İlişkilerde gezinen bir kılavuz gibi birden çok tabloya bağlamak istediğiniz bir denetiminiz varsa, bir **DataViewManager** idealdir.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-104">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="5e9e7-105">**DataViewManager** , içindeki <xref:System.Data.DataViewSetting> <xref:System.Data.DataSet>tabloların görünüm ayarını ayarlamak için kullanılan nesnelerin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-105">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5e9e7-106">, <xref:System.Data.DataViewSettingCollection> Bir **veri kümesindeki**her tablo için bir <xref:System.Data.DataViewSetting> nesne içerir.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-106">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="5e9e7-107">Başvurulan tablonun varsayılan **ApplyDefaultSort**, **Sort**, **RowFilter**ve **RowStateFilter** özelliklerini **DataViewSetting**kullanarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-107">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="5e9e7-108">Belirli bir tablo için, ada veya sıralı başvuruya göre veya ilgili tablo nesnesine bir başvuru geçirerek **DataViewSetting** 'a başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-108">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="5e9e7-109">**DataViewSettings** özelliğini kullanarak **DataViewManager** içindeki **DataViewSetting** nesneleri koleksiyonuna erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-109">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="5e9e7-110">Aşağıdaki kod örneği bir **veri kümesini** SQL Server **Northwind** veritabanı tabloları **müşteriler**, **siparişler**ve **sipariş ayrıntıları**ile doldurur, tablolar arasındaki ilişkileri oluşturur, bir **DataViewManager** kullanır Varsayılan **DataView** ayarlarını ayarlayın ve bir **DataGrid** ' i **DataViewManager**öğesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-110">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="5e9e7-111">Örnek, **veri kümesindeki** tüm tablolar için varsayılan **DataView** ayarlarını tablosunun birincil anahtarına (**ApplyDefaultSort** = **true**) göre sıralar ve ardından **müşteriler** tablosunun sıralama düzenini değiştirir. **CompanyName**'e göre sıralayın.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-111">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e9e7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e9e7-112">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [<span data-ttu-id="5e9e7-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="5e9e7-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="5e9e7-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e9e7-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
