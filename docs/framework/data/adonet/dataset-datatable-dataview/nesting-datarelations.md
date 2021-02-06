---
description: 'Daha fazla bilgi edinin: Iç Içe DataRelation'
title: DataRelations’ı İç İçe Yerleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: d998802a11fbb2bf414aa28b4beee95cac70a819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651762"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="a81f0-103">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="a81f0-103">Nesting DataRelations</span></span>

<span data-ttu-id="a81f0-104">Verilerin ilişkisel bir gösteriminde, tek tek tablolar bir sütun veya sütun kümesi kullanılarak birbirleriyle ilişkili satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-104">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="a81f0-105">ADO.NET <xref:System.Data.DataSet> , tablolar arasındaki ilişki bir kullanılarak uygulanır <xref:System.Data.DataRelation> .</span><span class="sxs-lookup"><span data-stu-id="a81f0-105">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="a81f0-106">Bir **DataRelation** oluşturduğunuzda, sütunların üst-alt ilişkileri yalnızca ilişki üzerinden yönetilir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-106">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="a81f0-107">Tablolar ve sütunlar ayrı varlıklardır.</span><span class="sxs-lookup"><span data-stu-id="a81f0-107">The tables and columns are separate entities.</span></span> <span data-ttu-id="a81f0-108">XML 'in sağladığı verilerin hiyerarşik gösteriminde, üst-alt ilişkileri iç içe geçmiş alt öğeler içeren üst öğeler tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-108">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="a81f0-109">Bir **veri kümesi** , WRITEXML kullanılarak XML verileriyle eşitlendiğinde veya yazılmış olduğunda alt nesnelerin iç içe koyulmasını kolaylaştırmak için <xref:System.Xml.XmlDataDocument> , bir **iç içe geçmiş** özelliği gösterir. </span><span class="sxs-lookup"><span data-stu-id="a81f0-109">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="a81f0-110">Bir **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlamak, ilişkinin alt satırlarının XML verisi olarak yazıldığında veya bir **XmlDataDocument** ile eşitlendiğinde üst sütun içinde iç içe olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a81f0-110">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="a81f0-111">**DataRelation** 'ın **Nested** özelliği varsayılan olarak **false 'tur**.</span><span class="sxs-lookup"><span data-stu-id="a81f0-111">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="a81f0-112">Örneğin, aşağıdaki **veri kümesini** göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a81f0-112">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="a81f0-113">Bu **veri** kümesi için **DataRelation** nesnesinin **Nested** özelliği **true** olarak ayarlanmadığından, bu **veri kümesi** XML verisi olarak temsil edildiğinde alt nesneler üst öğeler içinde iç içe değildir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-113">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="a81f0-114">İç içe olmayan veri ilişkileri ile ilgili **veri kümesini** Içeren bir **veri kümesinin** XML gösterimini dönüştürmek, performansın düşmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-114">Transforming the XML representation of a **DataSet** that contains related **DataSet** s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="a81f0-115">Veri ilişkilerini iç içe etmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="a81f0-115">We recommend that you nest the data relations.</span></span> <span data-ttu-id="a81f0-116">Bunu yapmak için, **Iç Içe geçmiş** özelliği **true** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a81f0-116">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="a81f0-117">Ardından, verileri bulmak ve dönüştürmek için yukarıdan aşağı hiyerarşik XPath sorgu ifadelerini kullanan XSLT stil sayfasına kod yazın.</span><span class="sxs-lookup"><span data-stu-id="a81f0-117">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="a81f0-118">Aşağıdaki kod örneği, **veri kümesinde** **WriteXml** çağırmanın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-118">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="a81f0-119">**Customers** öğesi ve **Orders** öğelerinin eşdüzey öğeler olarak gösterildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a81f0-119">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="a81f0-120">**Orders** öğelerinin kendi üst öğelerinin alt öğeleri olarak gösterilmesini Istiyorsanız, **DataRelation** 'ın **Nested** özelliği **true** olarak ayarlanmalıdır ve aşağıdakileri eklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="a81f0-120">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="a81f0-121">Aşağıdaki kod, elde edilen çıktının nasıl görüneceğine, ilgili üst öğelerinin içine yerleştirilmiş **Orders** öğeleriyle gösterir.</span><span class="sxs-lookup"><span data-stu-id="a81f0-121">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a81f0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a81f0-122">See also</span></span>

- [<span data-ttu-id="a81f0-123">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="a81f0-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="a81f0-124">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="a81f0-124">Adding DataRelations</span></span>](adding-datarelations.md)
- [<span data-ttu-id="a81f0-125">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="a81f0-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a81f0-126">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a81f0-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
