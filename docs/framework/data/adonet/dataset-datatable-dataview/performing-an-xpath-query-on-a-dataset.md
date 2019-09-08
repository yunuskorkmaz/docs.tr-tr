---
title: DataSet Üzerinde XPath Sorgusu Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 6082a171d24c55ea52c153bbd920bb7486be78a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784367"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>DataSet Üzerinde XPath Sorgusu Gerçekleştirme
Eşitlenmiş <xref:System.Data.DataSet> ve <xref:System.Xml.XmlDataDocument> arasındaki ilişki, **XmlDataDocument** 'e erişen XML Path Language (XPath) sorgusu gibi XML hizmetlerinden yararlanabilirsiniz ve belirli işlevselliği daha kolay bir şekilde gerçekleştirebilir doğrudan **veri kümesine** erişme. Örneğin, bir **veri kümesindeki**diğer tablolarla ilişkilerde gezinmek için bir <xref:System.Data.DataTable> ' ın SELECT metodunu kullanmak yerine, bir veri **kümesiyle**eşitlenen bir **XmlDataDocument** üzerinde bir XPath sorgusu gerçekleştirebilirsiniz. bir <xref:System.Xml.XmlNodeList>biçimindeki XML öğelerinin listesi. **XmlNodeList**içindeki düğümler <xref:System.Xml.XmlElement> , düğüm olarak atama, daha sonra, eşitlenen <xref:System.Data.DataRow> **tablodaki satırlara eşleşen başvuruları döndürmek için XmlDataDocument 'in GetRowFromElement yöntemine geçirilebilir Veri kümesi**.  
  
 Örneğin, aşağıdaki kod örneği bir "ılchild" XPath sorgusu gerçekleştirir. **Veri kümesi** üç tabloyla doldurulmuştur: **Müşteriler**, **siparişler**ve **OrderDetails**. Örnekte, ilk olarak **müşteriler** ve **siparişler** tabloları arasında ve **siparişler** ve **OrderDetails** tabloları arasında bir üst-alt ilişkisi oluşturulur. Daha sonra bir XPath sorgusu, bir alt öğe **OrderDetails** düğümünün 43 değeriyle bir **ProductID** düğümü olduğu **müşteriler** düğümlerinin bir **XmlNodeList** 'i döndürmek için gerçekleştirilir. Temelde, örnek 43 **ProductID** 'sini içeren ürünü hangi müşterilerin sipariş etti belirleyen XPath sorgusunu kullanmaktır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet ve XmlDataDocument Eşitlemesi](dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
