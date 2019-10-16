---
title: 'Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: cb39895ec5916eb417fb2a161e7c1307087c09c5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320571"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="960f8-102">Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="960f8-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="960f8-103">XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="960f8-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="960f8-104">Örneğin, [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="960f8-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="960f8-105">Her `Customer` öğesi bir `CustomerID` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="960f8-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="960f8-106">Her `Order` öğesi bir `CustomerID` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="960f8-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="960f8-107">Her bir siparişte `CustomerID` öğesi, bir müşterinin `CustomerID` özniteliğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="960f8-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="960f8-108">[Örnek xsd dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) , bu belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir.</span><span class="sxs-lookup"><span data-stu-id="960f8-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="960f8-109">@No__t-3 öğesinin `CustomerID` özniteliğinin bir anahtar olduğunu ve her `Order` öğesinde `CustomerID` öğesi ile her `Customer` öğesindeki `CustomerID` özniteliğinde bir ilişki kurmayı belirlemek için, XSD 'nin `xs:key` ve `xs:keyref` özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="960f8-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="960f8-110">@No__t-0 ile, `Join` yan tümcesini kullanarak bu ilişkiyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="960f8-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="960f8-111">Kullanılabilir dizin olmadığından, bu tür bir birleştirme çalışma zamanı performansına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="960f8-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="960f8-112">@No__t-0 hakkında daha ayrıntılı bilgi için bkz. [JOIN Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="960f8-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="960f8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="960f8-113">Example</span></span>  
 <span data-ttu-id="960f8-114">Aşağıdaki örnek, `Customer` öğelerini `Order` öğelerine birleştirir ve siparişlerdeki `CompanyName` öğesini içeren yeni bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="960f8-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="960f8-115">Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="960f8-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="960f8-116">Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.</span><span class="sxs-lookup"><span data-stu-id="960f8-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="960f8-117">Bu sorgu ilk olarak tüm `Customer` öğelerini alır ve sonra bunları `Order` öğelerine birleştirir.</span><span class="sxs-lookup"><span data-stu-id="960f8-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="960f8-118">Yalnızca, "K" dan büyük `CustomerID` ' a sahip müşterilere ait siparişleri seçer.</span><span class="sxs-lookup"><span data-stu-id="960f8-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="960f8-119">Ardından, her bir sırada müşteri bilgilerini içeren yeni bir `Order` öğesi projeler olur.</span><span class="sxs-lookup"><span data-stu-id="960f8-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="960f8-120">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="960f8-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="960f8-121">Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="960f8-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="960f8-122">Bu biçimde birleştirme işlemi çok iyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="960f8-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="960f8-123">Birleşimler, doğrusal bir arama yoluyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="960f8-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="960f8-124">Performansla ilgili yardım için hiçbir karma tablo veya dizin yok.</span><span class="sxs-lookup"><span data-stu-id="960f8-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="960f8-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="960f8-125">This code produces the following output:</span></span>  
  
```console
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
  
## <a name="see-also"></a><span data-ttu-id="960f8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="960f8-126">See also</span></span>

- [<span data-ttu-id="960f8-127">Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="960f8-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
