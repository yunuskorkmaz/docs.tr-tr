---
title: Bir veri kümesi üzerinde bir XPath sorgusu gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: a1718429360d79c4628e9948eb1b052c3ac01964
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46536783"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Bir veri kümesi üzerinde bir XPath sorgusu gerçekleştirme
Eşitlenen bir alana arasındaki ilişkiyi <xref:System.Data.DataSet> ve <xref:System.Xml.XmlDataDocument> XML'sini yararlanması sağlar erişen gibi hizmetleri XML Path Language (XPath) sorgusu, **XmlDataDocument** ve bazı işlevleri gerçekleştirebilirsiniz erişim değerinden daha rahat **veri kümesi** doğrudan. Örneğin kullanmak yerine **seçin** yöntemi bir <xref:System.Data.DataTable> diğer tablolarla ilişki gitmek için bir **veri kümesi**, bir XPath sorgusu gerçekleştirebileceğiniz bir **XmlDataDocument**  ile eşitlenmiş **veri kümesi**biçiminde XML öğelerinin bir listesini almak için bir <xref:System.Xml.XmlNodeList>. Düğümlerin **XmlNodeList**, noktaya yayın olarak <xref:System.Xml.XmlElement> düğümler, ardından geçilebilir **GetRowFromElement** yöntemi **XmlDataDocument**, eşleşen döndürmek için <xref:System.Data.DataRow> eşitlenmiş tablodaki satırları için başvurular **veri kümesi**.  
  
 Örneğin, aşağıdaki kod örneği, bir "en alt" XPath sorgusu gerçekleştirir. **Veri kümesi** üç tablo ile doldurulur: **müşteriler**, **siparişler**, ve **OrderDetails**. Aşağıdaki örnekte, bir üst-alt ilişkisi ilk arasında oluşturulan **müşteriler** ve **siparişler** tablolar ve arasında **siparişler** ve **OrderDetails** tablolar. Bir XPath sorgusu döndürülecek gerçekleştirilir bir **XmlNodeList** , **müşteriler** düğümleri bir en alt burada **OrderDetails** düğüme sahip bir **ProductID**43 değerini düğümle. Esas olarak, örnek XPath sorgusu sahip ürün hangi müşteriler sipariş belirlemek için kullandığı **ProductID** 43.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],   
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);   
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet ve XmlDataDocument Eşitlemesi](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
