---
title: İki koleksiyon nasıl katılır (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345855"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="d3746-102">İki koleksiyon nasıl katılır (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d3746-102">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="d3746-103">XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="d3746-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="d3746-104">Örneğin, [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d3746-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="d3746-105">Her `Customer` öğesi bir `CustomerID` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="d3746-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="d3746-106">Her `Order` öğesi bir `CustomerID` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="d3746-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="d3746-107">Her sırada `CustomerID` öğesi bir müşterinin `CustomerID` özniteliğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="d3746-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="d3746-108">[Örnek xsd dosyası: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md) , bu belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir.</span><span class="sxs-lookup"><span data-stu-id="d3746-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="d3746-109">`Customer` öğesinin `CustomerID` özniteliğinin bir anahtar olduğunu ve her `CustomerID` öğesindeki `Order` öğesi ile her `CustomerID` öğesi arasında bir ilişki kurmayı oluşturmak için XSD 'nin `xs:key` ve `xs:keyref` özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3746-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="d3746-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], `join` yan tümcesini kullanarak bu ilişkinin avantajlarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3746-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="d3746-111">Kullanılabilir dizin olmadığından, bu tür bir katılım düşük çalışma zamanı performansına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d3746-111">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="d3746-112">`join`hakkında daha ayrıntılı bilgi için bkz. [JOIN Operations (C#)](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d3746-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="d3746-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3746-113">Example</span></span>

<span data-ttu-id="d3746-114">Aşağıdaki örnek `Customer` öğelerini `Order` öğelerine birleştirir ve siparişlerde `CompanyName` öğesini içeren yeni bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3746-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="d3746-115">Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="d3746-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="d3746-116">Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3746-116">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="d3746-117">Bu sorgu ilk olarak tüm `Customer` öğelerini alır ve sonra bunları `Order` öğelerine birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d3746-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="d3746-118">Yalnızca, "K" dan büyük `CustomerID` olan müşterilere ait siparişleri seçer.</span><span class="sxs-lookup"><span data-stu-id="d3746-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="d3746-119">Ardından, her bir sırada müşteri bilgilerini içeren yeni bir `Order` öğesini projeler.</span><span class="sxs-lookup"><span data-stu-id="d3746-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="d3746-120">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="d3746-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="d3746-121">Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="d3746-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="d3746-122">Bu şekilde katılabilmek iyi bir işlem yapmaz.</span><span class="sxs-lookup"><span data-stu-id="d3746-122">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="d3746-123">Birleşimler, doğrusal bir arama yoluyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="d3746-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="d3746-124">Performansla ilgili yardım için hiçbir karma tablo veya dizin yok.</span><span class="sxs-lookup"><span data-stu-id="d3746-124">There are no hash tables or indexes to help with performance.</span></span>

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

<span data-ttu-id="d3746-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d3746-125">This code produces the following output:</span></span>

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
