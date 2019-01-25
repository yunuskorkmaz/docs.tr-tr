---
title: 'Nasıl yapılır: (Visual Basic) XML ağacının şeklini dönüştürme'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: c3fb1cd0995597be6c5108832750b6695d196b58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624192"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="6dff7-102">Nasıl yapılır: (Visual Basic) XML ağacının şeklini dönüştürme</span><span class="sxs-lookup"><span data-stu-id="6dff7-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="6dff7-103">*Şekli* alt öğe adları, öznitelik adları ve özellikleri, hiyerarşinin bir XML'sini belge başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="6dff7-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="6dff7-104">Bazen, bir XML belgesi şeklini değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="6dff7-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="6dff7-105">Örneğin, var olan bir XML belgesi farklı öğe ve öznitelik adları gerektiren başka bir sisteme gönderme gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="6dff7-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="6dff7-106">Belgede, silme ve gerekli, ancak kullanarak işlevsel oluşturma sonuçları daha okunabilir ve sürdürülebilir kod öğeleri yeniden adlandırma gidilemedi.</span><span class="sxs-lookup"><span data-stu-id="6dff7-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="6dff7-107">İşlevsel oluşturma hakkında daha fazla bilgi için bkz: [işlevsel oluşturma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6dff7-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="6dff7-108">İlk örnek, XML belgesi kuruluş değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6dff7-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="6dff7-109">Bu karmaşık öğe ağacında bir konumdan diğerine taşır.</span><span class="sxs-lookup"><span data-stu-id="6dff7-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="6dff7-110">Bu konudaki ikinci örnek, kaynak belgedeki daha farklı bir şekilde bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6dff7-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="6dff7-111">Öğe adları büyük küçük harfleri değiştirir, bazı öğelerin yeniden adlandırır ve bazı öğeleri kaynak ağaç dönüştürülmüş ağaç dışında bırakır.</span><span class="sxs-lookup"><span data-stu-id="6dff7-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dff7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6dff7-112">Example</span></span>  
 <span data-ttu-id="6dff7-113">Aşağıdaki kod, katıştırılmış sorgu ifadeleri kullanarak bir XML dosyası şeklini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6dff7-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="6dff7-114">Bu örnekte kaynak XML belgesinde içeren bir `Customers` öğesi altında `Root` tüm müşteriler içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="6dff7-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="6dff7-115">Ayrıca içerdiği bir `Orders` öğesi altında `Root` tüm siparişleri içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="6dff7-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="6dff7-116">Bu örnekte, her bir müşterinin siparişlerini içerdiği yeni bir XML ağacı oluşturur bir `Orders` öğesiyle `Customer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6dff7-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="6dff7-117">Özgün belgeyi de içeren bir `CustomerID` öğesinde `Order` öğesi; yeniden şekillendirilmiş belgeden kaldırılması bu öğe olacaktır.</span><span class="sxs-lookup"><span data-stu-id="6dff7-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="6dff7-118">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6dff7-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6dff7-119">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6dff7-119">This code produces the following output:</span></span>  
  
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
. . .  
```  
  
## <a name="example"></a><span data-ttu-id="6dff7-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="6dff7-120">Example</span></span>  
 <span data-ttu-id="6dff7-121">Bu örnek, bazı öğelerin yeniden adlandırır ve bazı öznitelikler öğesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6dff7-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="6dff7-122">Kod çağrıları `ConvertAddress`, listesini döndürür <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6dff7-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="6dff7-123">Yöntem bağımsız değişkeninin belirleyen bir sorgudur `Address` karmaşık bir öğe olduğu `Type` öznitelik değerine sahip `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="6dff7-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="6dff7-124">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6dff7-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6dff7-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6dff7-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6dff7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dff7-126">See also</span></span>
- [<span data-ttu-id="6dff7-127">Projeksiyonlar ve Dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6dff7-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
