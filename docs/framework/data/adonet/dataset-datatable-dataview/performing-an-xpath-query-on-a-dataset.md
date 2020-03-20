---
title: DataSet Üzerinde XPath Sorgusu Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 5e9a00ab78a57c3c1686d7c87ed8b45d9b2649af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150837"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>DataSet Üzerinde XPath Sorgusu Gerçekleştirme
Senkronize <xref:System.Data.DataSet> edilmiş <xref:System.Xml.XmlDataDocument> ve XML Yol Dili (XPath) sorgusu **gibi, XmlDataDocument'a** erişen ve belirli işlevleri doğrudan **DataSet'e** erişmekten daha rahat gerçekleştirebilen XML hizmetlerinden yararlanmanızı sağlar. Örneğin, **Bir DataSet'teki**diğer <xref:System.Data.DataTable> tablolarla ilişkileri yönlendirmek için bir ilişkinin **Seç** yöntemini kullanmak yerine, Bir ' şeklinde XML öğelerinin listesini almak **için, DataSet** <xref:System.Xml.XmlNodeList>ile senkronize edilmiş bir **XmlDataDocument'da** XPath sorgusu gerçekleştirebilirsiniz. **XmlNodeList**düğümleri <xref:System.Xml.XmlElement> , düğümolarak döküm, daha sonra **XmlDataDocument** **GetRowFromElement** yöntemine geçirilebilir , <xref:System.Data.DataRow> senkronize **DataSet**tablonun satırlarına eşleşen başvurular dönmek için .  
  
 Örneğin, aşağıdaki kod örneği bir "torun" XPath sorgusu gerçekleştirir. **DataSet** üç tabloyla doldurulur: **Müşteriler,** **Siparişler**ve **Sipariş Ayrıntıları.** Örnekte, önce **Müşteriler** ve **Siparişler** tabloları arasında ve **Siparişler** ve Sipariş **Ayrıntıları** tabloları arasında bir üst-alt ilişkisi oluşturulur. XPath sorgusu daha sonra, torun **Sipariş Ayrıntıları** düğümünde 43 değeriolan bir **ProductID** düğümüolan Bir **XmlNodeList** **of Customers** düğümlerini döndürmek için gerçekleştirilir. Özünde, örnek, **43'ün ProductID'sine** sahip ürünü hangi müşterilerin sipariş ettiğini belirlemek için XPath sorgusunu kullanır.  
  
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
