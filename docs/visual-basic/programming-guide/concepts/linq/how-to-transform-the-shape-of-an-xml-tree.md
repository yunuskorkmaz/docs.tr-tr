---
title: 'Nasıl yapılır: XML Ağacının Şeklini Dönüştürme'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 90fa23df09972eb76154dc47ce0a025e85a12ea3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397667"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="bb1e1-102">Nasıl yapılır: bir XML ağacının şeklini dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb1e1-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="bb1e1-103">Bir XML belgesinin *şekli* öğe adlarına, öznitelik adlarına ve hiyerarşisinin özelliklerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="bb1e1-104">Bazen bir XML belgesinin şeklini değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="bb1e1-105">Örneğin, var olan bir XML belgesini farklı öğe ve öznitelik adları gerektiren başka bir sisteme göndermeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="bb1e1-106">Belgeyi, gereken şekilde silip yeniden adlandırarak, ancak işlevsel oluşturmayı kullanmak daha okunabilir ve sürdürülebilir kod ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="bb1e1-107">İşlevsel oluşturma hakkında daha fazla bilgi için bkz. [Işlevsel oluşturma (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bb1e1-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="bb1e1-108">İlk örnek, XML belgesi organizasyonunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="bb1e1-109">Karmaşık öğeleri ağaçtaki bir konumdan diğerine taşımıştır.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="bb1e1-110">Bu konudaki ikinci örnek, kaynak belgeden farklı bir şekle sahip bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="bb1e1-111">Öğe adlarının büyük küçük harflerini değiştirir, bazı öğeleri yeniden adlandırır ve dışarı dönüştürülen ağacın bazı öğelerini kaynak ağacından bırakır.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb1e1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb1e1-112">Example</span></span>  
 <span data-ttu-id="bb1e1-113">Aşağıdaki kod, ekli sorgu ifadeleri kullanarak bir XML dosyasının şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="bb1e1-114">Bu örnekteki kaynak XML belgesi `Customers` , `Root` tüm müşterileri içeren öğesi altında bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="bb1e1-115">Ayrıca `Orders` , `Root` tüm siparişleri içeren öğesi altında bir öğesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="bb1e1-116">Bu örnek, her müşteriye ait siparişlerin öğesi içindeki bir öğede bulunduğu yeni bir XML ağacı oluşturur `Orders` `Customer` .</span><span class="sxs-lookup"><span data-stu-id="bb1e1-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="bb1e1-117">Özgün belge ayrıca `CustomerID` öğesi içindeki bir öğesi de içerir `Order` ; Bu öğe, yeniden şekillendirilmiş belgeden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="bb1e1-118">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bb1e1-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bb1e1-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bb1e1-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bb1e1-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb1e1-120">Example</span></span>  
 <span data-ttu-id="bb1e1-121">Bu örnek bazı öğeleri yeniden adlandırır ve bazı öznitelikleri öğelere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="bb1e1-122">`ConvertAddress`Bir nesne listesi döndüren kod çağırır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="bb1e1-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bb1e1-123">Yöntemin bağımsız değişkeni, `Address` özniteliğinin değeri olan karmaşık öğeyi belirleyen bir sorgudur `Type` `"Shipping"` .</span><span class="sxs-lookup"><span data-stu-id="bb1e1-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="bb1e1-124">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bb1e1-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bb1e1-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bb1e1-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb1e1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb1e1-126">See also</span></span>

- [<span data-ttu-id="bb1e1-127">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb1e1-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
