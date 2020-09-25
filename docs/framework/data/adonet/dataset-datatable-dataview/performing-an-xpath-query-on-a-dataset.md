---
title: DataSet Üzerinde XPath Sorgusu Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: d7897815874f2e9de2f4c24d3c141d464a296b31
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201245"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>DataSet Üzerinde XPath Sorgusu Gerçekleştirme

Eşitlenen ve arasındaki ilişki, <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> **XmlDataDocument** 'e erişen XML Path Language (XPath) sorgusu gibi XML hizmetlerinden yararlanabilirsiniz ve belirli işlevleri doğrudan **veri kümesine** erişmekten daha kolay gerçekleştirebilir. Örneğin, bir **Select** <xref:System.Data.DataTable> **veri kümesindeki**diğer tablolarla ilişkilerde gezinmek için bir ' ın SELECT metodunu kullanmak yerine, bir veri **kümesiyle**eşitlenen bir **XmlDataDocument** üzerinde bir XPath sorgusu gerçekleştirebilirsiniz <xref:System.Xml.XmlNodeList> . **XmlNodeList**içindeki düğümler, düğüm olarak atama <xref:System.Xml.XmlElement> , daha sonra eşitlenmiş veri kümesindeki tablonun satırlarına eşleşen başvuruları döndürmek Için **XmlDataDocument**'in **GetRowFromElement** metoduna geçirilebilir <xref:System.Data.DataRow> . **DataSet**  
  
 Örneğin, aşağıdaki kod örneği bir "ılchild" XPath sorgusu gerçekleştirir. **Veri kümesi** üç tabloyla doldurulmuştur: **müşteriler**, **siparişler**ve **OrderDetails**. Örnekte, ilk olarak **müşteriler** ve **siparişler** tabloları arasında ve **siparişler** ve **OrderDetails** tabloları arasında bir üst-alt ilişkisi oluşturulur. Daha sonra bir XPath sorgusu, bir alt öğe **OrderDetails** düğümünün 43 değeriyle bir **ProductID** düğümü olduğu **müşteriler** düğümlerinin bir **XmlNodeList** 'i döndürmek için gerçekleştirilir. Temelde, örnek 43 **ProductID** 'sini içeren ürünü hangi müşterilerin sipariş etti belirleyen XPath sorgusunu kullanmaktır.  
  
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
