---
title: Bir veri kümesine XPath sorgusunu gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: c785cc69289440918f45974c711ae0b112130c5d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Bir veri kümesine XPath sorgusunu gerçekleştirme
Bir eşitlenmiş arasındaki ilişkiyi <xref:System.Data.DataSet> ve <xref:System.Xml.XmlDataDocument> XML'sini kullanmak yapmanızı sağlar erişen gibi hizmetleri XML Path dili (XPath) sorgusu **XmlDataDocument** ve bazı işlevleri gerçekleştirebilir erişme değerinden daha rahat **DataSet** doğrudan. Örneğin, kullanarak yerine **seçin** yöntemi bir <xref:System.Data.DataTable> diğer tablolarla ilişkileri gitmek için bir **veri kümesi**, bir XPath sorgusu gerçekleştirebileceğiniz bir **XmlDataDocument**  ile eşitlenen **DataSet**biçiminde XML öğeleri listesini almak için bir <xref:System.Xml.XmlNodeList>. Düğümlerin **XmlNodeList**, noktaya yayın olarak <xref:System.Xml.XmlElement> düğümleri, ardından geçirilebilir için **GetRowFromElement** yöntemi **XmlDataDocument**, eşleşen döndürmek için <xref:System.Data.DataRow> Eşitlenmiş Tablo satırlara yapılan başvurular **DataSet**.  
  
 Örneğin, aşağıdaki kod örneği, bir "en alt" XPath sorgusu gerçekleştirir. **DataSet** üç tablolarla girilir: **müşteriler**, **siparişleri**, ve **sipariş ayrıntıları**. Örnekte, bir üst-alt ilişkisi ilk arasında oluşturulur **müşteriler** ve **siparişleri** tablolar arasındaki **siparişleri** ve **SiparişAyrıntıları** tablo. Bir XPath sorgusu sonra dönmek için gerçekleştirilen bir **XmlNodeList** , **müşteriler** düğümleri bir en alt burada **sipariş ayrıntıları** düğüm bir **ProductID**düğüm 43 değerine sahip. Esas olarak, örnek XPath sorgusu hangi müşterilerin sahip ürün sipariş belirlemek için kullandığı **ProductID** / 43.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
