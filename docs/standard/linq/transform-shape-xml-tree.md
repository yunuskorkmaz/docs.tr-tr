---
title: Bir XML ağacının şeklini dönüştürme-LINQ to XML
description: Bir XML belgesinin şeklini değiştirmek için işlevsel oluşturma kullanabilirsiniz; diğer bir deyişle, verileri tutmak, ancak bu tür şeyleri öğe adı, öznitelik adları ve hiyerarşi olarak değiştirmek için.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 7f78cb2542357be674d771f93825b7f4a56abea0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554508"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-linq-to-xml"></a><span data-ttu-id="bcf71-103">XML ağacının şeklini dönüştürme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bcf71-103">How to transform the shape of an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="bcf71-104">Bir XML belgesinin *şekli* öğe adlarına, öznitelik adlarına ve hiyerarşisinin özelliklerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="bcf71-104">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>

<span data-ttu-id="bcf71-105">Bazen bir XML belgesinin şeklini değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bcf71-105">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="bcf71-106">Örneğin, var olan bir XML belgesini farklı öğe ve öznitelik adları gerektiren başka bir sisteme göndermeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bcf71-106">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="bcf71-107">Belgeyi, gereken şekilde silip yeniden adlandırarak, ancak işlevsel oluşturmayı kullanmak daha okunabilir ve sürdürülebilir kod ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="bcf71-107">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="bcf71-108">İşlevsel oluşturma hakkında daha fazla bilgi için bkz. [işlevsel oluşturma](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="bcf71-108">For more information about functional construction, see [Functional construction](functional-construction.md).</span></span>

<span data-ttu-id="bcf71-109">Bu makaledeki ilk örnekte bir XML belgesi organizasyonu değişir.</span><span class="sxs-lookup"><span data-stu-id="bcf71-109">The first example in this article changes the organization of an XML document.</span></span> <span data-ttu-id="bcf71-110">Karmaşık öğeleri ağaçtaki bir konumdan diğerine taşımıştır.</span><span class="sxs-lookup"><span data-stu-id="bcf71-110">It moves complex elements from one location in the tree to another.</span></span>

<span data-ttu-id="bcf71-111">İkinci örnek, şekli kaynak belgeden farklı olan bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bcf71-111">The second example creates an XML document whose shape differs from that of the source document.</span></span> <span data-ttu-id="bcf71-112">Bazı öğeleri atlar, diğerlerini yeniden adlandırır ve öğe adlarının büyük küçük harflerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bcf71-112">It omits some elements, renames others, and changes the casing of the element names.</span></span>

## <a name="example-use-embedded-query-expressions-to-change-the-shape-of-an-xml-tree"></a><span data-ttu-id="bcf71-113">Örnek: bir XML ağacının şeklini değiştirmek için katıştırılmış sorgu ifadeleri kullanın</span><span class="sxs-lookup"><span data-stu-id="bcf71-113">Example: Use embedded query expressions to change the shape of an XML tree</span></span>

<span data-ttu-id="bcf71-114">Aşağıdaki örnek, ekli sorgu ifadeleri kullanarak bir XML dosyasının şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bcf71-114">The following example changes the shape of an XML file using embedded query expressions.</span></span>

<span data-ttu-id="bcf71-115">Bu örnek için kaynak XML belgesi, [örnek xml dosyası: müşteriler ve siparişler](sample-xml-file-customers-orders.md), `Customers` `Root` tüm müşterileri içeren öğesi altında bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="bcf71-115">The source XML document for this example, [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="bcf71-116">Ayrıca `Orders` , `Root` tüm siparişleri içeren öğesi altında bir öğesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="bcf71-116">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="bcf71-117">Örnek, her müşteriye ait siparişlerin öğesi içindeki bir öğede bulunduğu yeni bir XML ağacı oluşturur `Orders` `Customer` .</span><span class="sxs-lookup"><span data-stu-id="bcf71-117">The example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="bcf71-118">Özgün belge `CustomerID` , öğesinde bir öğesi de içerir `Order` ; Bu öğe yeni ağaçtan atlanır.</span><span class="sxs-lookup"><span data-stu-id="bcf71-118">The original document also contains a `CustomerID` element in the `Order` element; this element is omitted from the new tree.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");
XElement newCustOrd =
    new XElement("Root",
        from cust in co.Element("Customers").Elements("Customer")
        select new XElement("Customer",
            cust.Attributes(),
            cust.Elements(),
            new XElement("Orders",
                from ord in co.Element("Orders").Elements("Order")
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")
                select new XElement("Order",
                    ord.Attributes(),
                    ord.Element("EmployeeID"),
                    ord.Element("OrderDate"),
                    ord.Element("RequiredDate"),
                    ord.Element("ShipInfo")
                )
            )
        )
    );
Console.WriteLine(newCustOrd);
```

 ```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim newCustOrd = _
    <Root>
        <%= From cust In co.<Customers>.<Customer> _
            Select _
            <Customer>
                <%= cust.Attributes() %>
                <%= cust.Elements() %>
                <Orders>
                    <%= From ord In co.<Orders>.<Order> _
                        Where ord.<CustomerID>.Value = cust.@CustomerID _
                        Select _
                        <Order>
                            <%= ord.Attributes() %>
                            <%= ord.<EmployeeID> %>
                            <%= ord.<OrderDate> %>
                            <%= ord.<RequiredDate> %>
                            <%= ord.<ShipInfo> %>
                        </Order> _
                    %>
                </Orders>
            </Customer> _
        %>
    </Root>
Console.WriteLine(newCustOrd)
```

<span data-ttu-id="bcf71-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bcf71-119">This example produces the following output:</span></span>

```xml
<Root>
  <Customer CustomerID="GREAL">
    <CompanyName>Great Lakes Food Market</CompanyName>
    <ContactName>Howard Snyder</ContactName>
    <ContactTitle>Marketing Manager</ContactTitle>
    <Phone>(503) 555-7555</Phone>
    <FullAddress>
      <Address>2732 Baker Blvd.</Address>
      <City>Eugene</City>
      <Region>OR</Region>
      <PostalCode>97403</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  <Customer CustomerID="HUNGC">
    <CompanyName>Hungry Coyote Import Store</CompanyName>
    <ContactName>Yoshi Latimer</ContactName>
    <ContactTitle>Sales Representative</ContactTitle>
    <Phone>(503) 555-6874</Phone>
    <Fax>(503) 555-2376</Fax>
    <FullAddress>
      <Address>City Center Plaza 516 Main St.</Address>
      <City>Elgin</City>
      <Region>OR</Region>
      <PostalCode>97827</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  ...
</Root>
```

## <a name="example-create-a-document-whose-shape-differs-from-that-of-the-source-document"></a><span data-ttu-id="bcf71-120">Örnek: şekli kaynak belgeden farklı olan bir belge oluştur</span><span class="sxs-lookup"><span data-stu-id="bcf71-120">Example: Create a document whose shape differs from that of the source document</span></span>

<span data-ttu-id="bcf71-121">Bu örnek bazı öğeleri yeniden adlandırır ve bazı öznitelikleri öğelere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bcf71-121">This example renames some elements and converts some attributes to elements.</span></span> <span data-ttu-id="bcf71-122">Bu `ConvertAddress` , bir nesne listesi döndüren çağırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="bcf71-122">It calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bcf71-123">Yöntemin bağımsız değişkeni, `Address` özniteliğinin değeri olan karmaşık öğeyi belirleyen bir sorgudur `Type` `"Shipping"` .</span><span class="sxs-lookup"><span data-stu-id="bcf71-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span> <span data-ttu-id="bcf71-124">Örnek, XML belgesi [örnek xml dosyasını kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="bcf71-124">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
static IEnumerable<XElement> ConvertAddress(XElement add)
{
    List<XElement> fragment = new List<XElement>() {
        new XElement("NAME", (string)add.Element("Name")),
        new XElement("STREET", (string)add.Element("Street")),
        new XElement("CITY", (string)add.Element("City")),
        new XElement("ST", (string)add.Element("State")),
        new XElement("POSTALCODE", (string)add.Element("Zip")),
        new XElement("COUNTRY", (string)add.Element("Country"))
    };
    return fragment;
}

static void Main(string[] args)
{
    XElement po = XElement.Load("PurchaseOrder.xml");
    XElement newPo = new XElement("PO",
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),
        ConvertAddress(
            (from el in po.Elements("Address")
            where (string)el.Attribute("Type") == "Shipping"
            select el)
            .First()
        )
    );
    Console.WriteLine(newPo);
}
```

```vb
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)
    Dim fragment = New List(Of XElement)
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)
    fragment.Add(<ST><%= add.<State>.Value %></ST>)
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)
    Return fragment
End Function

Sub Main()
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")
    Dim newPo As XElement = _
        <PO>
            <ID><%= po.@PurchaseOrderNumber %></ID>
            <DATE><%= CDate(po.@OrderDate) %></DATE>
            <%= _
                ConvertAddress( _
                (From el In po.<Address> _
                Where el.@Type = "Shipping" _
                Select el) _
                .First() _
                ) _
            %>
        </PO>
    Console.WriteLine(newPo)
End Sub
```

<span data-ttu-id="bcf71-125">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bcf71-125">This example produces the following output:</span></span>

```xml
<PO>
  <ID>99503</ID>
  <DATE>1999-10-20T00:00:00</DATE>
  <NAME>Ellen Adams</NAME>
  <STREET>123 Maple Street</STREET>
  <CITY>Mill Valley</CITY>
  <ST>CA</ST>
  <POSTALCODE>10999</POSTALCODE>
  <COUNTRY>USA</COUNTRY>
</PO>
```

## <a name="see-also"></a><span data-ttu-id="bcf71-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcf71-126">See also</span></span>

- [<span data-ttu-id="bcf71-127">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcf71-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](./work-dictionaries-linq-xml.md)
