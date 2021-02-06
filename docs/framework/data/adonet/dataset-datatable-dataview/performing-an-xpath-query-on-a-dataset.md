---
description: 'Hakkında daha fazla bilgi edinin: veri kümesinde XPath sorgusu gerçekleştirme'
title: DataSet Üzerinde XPath Sorgusu Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 9febcc545f86f048b2d693f8aa6558a1b7883a60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651723"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="a278c-103">DataSet Üzerinde XPath Sorgusu Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="a278c-103">Performing an XPath Query on a DataSet</span></span>

<span data-ttu-id="a278c-104">Eşitlenen ve arasındaki ilişki, <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> **XmlDataDocument** 'e erişen XML Path Language (XPath) sorgusu gibi XML hizmetlerinden yararlanabilirsiniz ve belirli işlevleri doğrudan **veri kümesine** erişmekten daha kolay gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="a278c-104">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="a278c-105">Örneğin, bir  <xref:System.Data.DataTable> **veri kümesindeki** diğer tablolarla ilişkilerde gezinmek için bir ' ın SELECT metodunu kullanmak yerine, bir veri **kümesiyle** eşitlenen bir **XmlDataDocument** üzerinde bir XPath sorgusu gerçekleştirebilirsiniz <xref:System.Xml.XmlNodeList> .</span><span class="sxs-lookup"><span data-stu-id="a278c-105">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="a278c-106">**XmlNodeList** içindeki düğümler, düğüm olarak atama <xref:System.Xml.XmlElement> , daha sonra eşitlenmiş veri kümesindeki tablonun satırlarına eşleşen başvuruları döndürmek Için **XmlDataDocument**'in **GetRowFromElement** metoduna geçirilebilir <xref:System.Data.DataRow> . </span><span class="sxs-lookup"><span data-stu-id="a278c-106">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="a278c-107">Örneğin, aşağıdaki kod örneği bir "ılchild" XPath sorgusu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a278c-107">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="a278c-108">**Veri kümesi** üç tabloyla doldurulmuştur: **müşteriler**, **siparişler** ve **OrderDetails**.</span><span class="sxs-lookup"><span data-stu-id="a278c-108">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="a278c-109">Örnekte, ilk olarak **müşteriler** ve **siparişler** tabloları arasında ve **siparişler** ve **OrderDetails** tabloları arasında bir üst-alt ilişkisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a278c-109">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="a278c-110">Daha sonra bir XPath sorgusu, bir alt öğe **OrderDetails** düğümünün 43 değeriyle bir **ProductID** düğümü olduğu **müşteriler** düğümlerinin bir **XmlNodeList** 'i döndürmek için gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a278c-110">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="a278c-111">Temelde, örnek 43 **ProductID** 'sini içeren ürünü hangi müşterilerin sipariş etti belirleyen XPath sorgusunu kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a278c-111">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a278c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a278c-112">See also</span></span>

- [<span data-ttu-id="a278c-113">DataSet ve XmlDataDocument Eşitlemesi</span><span class="sxs-lookup"><span data-stu-id="a278c-113">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="a278c-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a278c-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
