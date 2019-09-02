---
title: DataRelations’ı İç İçe Yerleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 08149de9222c34928078c0ca9d88096f7a4a88d1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203263"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="d9afc-102">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="d9afc-102">Nesting DataRelations</span></span>
<span data-ttu-id="d9afc-103">Verilerin ilişkisel bir gösteriminde, tek tek tablolar bir sütun veya sütun kümesi kullanılarak birbirleriyle ilişkili satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="d9afc-104">ADO.net <xref:System.Data.DataSet>, tablolar arasındaki ilişki bir <xref:System.Data.DataRelation>kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d9afc-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="d9afc-105">Bir **DataRelation**oluşturduğunuzda, sütunların üst-alt ilişkileri yalnızca ilişki üzerinden yönetilir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="d9afc-106">Tablolar ve sütunlar ayrı varlıklardır.</span><span class="sxs-lookup"><span data-stu-id="d9afc-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="d9afc-107">XML 'in sağladığı verilerin hiyerarşik gösteriminde, üst-alt ilişkileri iç içe geçmiş alt öğeler içeren üst öğeler tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="d9afc-108">Bir **veri kümesi** , **WriteXml**kullanılarak XML verileriyle eşitlendiğinde <xref:System.Xml.XmlDataDocument> veya yazılmış olduğunda alt nesnelerin iç içe koyulmasını kolaylaştırmak için, bir **iç içe geçmiş** özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="d9afc-109">Bir **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlamak, ilişkinin alt satırlarının XML verisi olarak yazıldığında veya bir **XmlDataDocument**ile eşitlendiğinde üst sütun içinde iç içe olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="d9afc-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="d9afc-110">**DataRelation** 'ın **Nested** özelliği varsayılan olarak **false 'tur**.</span><span class="sxs-lookup"><span data-stu-id="d9afc-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="d9afc-111">Örneğin, aşağıdaki **veri kümesini**göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d9afc-111">For example, consider the following **DataSet**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 <span data-ttu-id="d9afc-112">Bu **veri**kümesi için **DataRelation** nesnesinin **Nested** özelliği **true** olarak ayarlanmadığından, bu **veri kümesi** XML verisi olarak temsil edildiğinde alt nesneler üst öğeler içinde iç içe değildir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="d9afc-113">İç içe olmayan veri ilişkileri ile ilgili **veri kümesini**Içeren bir **veri kümesinin** XML gösterimini dönüştürmek, performansın düşmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="d9afc-114">Veri ilişkilerini iç içe etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="d9afc-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="d9afc-115">Bunu yapmak için, **Iç Içe geçmiş** özelliği **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d9afc-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="d9afc-116">Ardından, verileri bulmak ve dönüştürmek için yukarıdan aşağı hiyerarşik XPath sorgu ifadelerini kullanan XSLT stil sayfasına kod yazın.</span><span class="sxs-lookup"><span data-stu-id="d9afc-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="d9afc-117">Aşağıdaki kod örneği, **veri kümesinde** **WriteXml** çağırmanın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 <span data-ttu-id="d9afc-118">**Customers** öğesi ve **Orders** öğelerinin eşdüzey öğeler olarak gösterildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d9afc-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="d9afc-119">**Orders** öğelerinin kendi üst öğelerinin alt öğeleri olarak gösterilmesini Istiyorsanız, **DataRelation** 'ın **Nested** özelliği **true** olarak ayarlanmalıdır ve aşağıdakileri eklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="d9afc-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="d9afc-120">Aşağıdaki kod, elde edilen çıktının nasıl görüneceğine, ilgili üst öğelerinin içine yerleştirilmiş **Orders** öğeleriyle gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9afc-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9afc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9afc-121">See also</span></span>

- [<span data-ttu-id="d9afc-122">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="d9afc-122">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="d9afc-123">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="d9afc-123">Adding DataRelations</span></span>](adding-datarelations.md)
- [<span data-ttu-id="d9afc-124">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="d9afc-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d9afc-125">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d9afc-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
