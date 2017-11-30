---
title: "Bir veri kümesine XPath sorgusunu gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e8a993c75f33dd3c98da5534658d02b4eeeda51a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="da7cb-102">Bir veri kümesine XPath sorgusunu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="da7cb-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="da7cb-103">Bir eşitlenmiş arasındaki ilişkiyi <xref:System.Data.DataSet> ve <xref:System.Xml.XmlDataDocument> XML'sini kullanmak yapmanızı sağlar erişen gibi hizmetleri XML Path dili (XPath) sorgusu **XmlDataDocument** ve bazı işlevleri gerçekleştirebilir erişme değerinden daha rahat **DataSet** doğrudan.</span><span class="sxs-lookup"><span data-stu-id="da7cb-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="da7cb-104">Örneğin, kullanarak yerine **seçin** yöntemi bir <xref:System.Data.DataTable> diğer tablolarla ilişkileri gitmek için bir **veri kümesi**, bir XPath sorgusu gerçekleştirebileceğiniz bir **XmlDataDocument**  ile eşitlenen **DataSet**biçiminde XML öğeleri listesini almak için bir <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="da7cb-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="da7cb-105">Düğümlerin **XmlNodeList**, noktaya yayın olarak <xref:System.Xml.XmlElement> düğümleri, ardından geçirilebilir için **GetRowFromElement** yöntemi **XmlDataDocument**, eşleşen döndürmek için <xref:System.Data.DataRow> Eşitlenmiş Tablo satırlara yapılan başvurular **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="da7cb-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="da7cb-106">Örneğin, aşağıdaki kod örneği, bir "en alt" XPath sorgusu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="da7cb-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="da7cb-107">**DataSet** üç tablolarla girilir: **müşteriler**, **siparişleri**, ve **sipariş ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="da7cb-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="da7cb-108">Örnekte, bir üst-alt ilişkisi ilk arasında oluşturulur **müşteriler** ve **siparişleri** tablolar arasındaki **siparişleri** ve **SiparişAyrıntıları** tablo.</span><span class="sxs-lookup"><span data-stu-id="da7cb-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="da7cb-109">Bir XPath sorgusu sonra dönmek için gerçekleştirilen bir **XmlNodeList** , **müşteriler** düğümleri bir en alt burada **sipariş ayrıntıları** düğüm bir **ProductID**düğüm 43 değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="da7cb-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="da7cb-110">Esas olarak, örnek XPath sorgusu hangi müşterilerin sahip ürün sipariş belirlemek için kullandığı **ProductID** / 43.</span><span class="sxs-lookup"><span data-stu-id="da7cb-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da7cb-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da7cb-111">See Also</span></span>  
 [<span data-ttu-id="da7cb-112">Veri kümesi ve XmlDataDocument eşitleme</span><span class="sxs-lookup"><span data-stu-id="da7cb-112">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [<span data-ttu-id="da7cb-113">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="da7cb-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
