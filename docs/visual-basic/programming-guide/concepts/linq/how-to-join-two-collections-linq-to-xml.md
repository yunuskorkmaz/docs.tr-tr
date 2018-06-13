---
title: 'Nasıl yapılır: iki koleksiyonları (LINQ-XML) birleştirme (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 3ceb9cf7dfdd1d18a07e93d15624fd8fac045d07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643698"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="2e8f6-102">Nasıl yapılır: iki koleksiyonları (LINQ-XML) birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e8f6-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="2e8f6-103">Bazen bir öğe veya öznitelik bir XML belgesi başka bir öğe veya öznitelik başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="2e8f6-104">Örneğin, [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML belgesi, müşterilerin listesini ve siparişleri listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="2e8f6-105">Her `Customer` öğesi içeren bir `CustomerID` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="2e8f6-106">Her `Order` öğesi içeren bir `CustomerID` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="2e8f6-107">`CustomerID` Her sipariş öğesinde başvurduğu `CustomerID` bir müşteri özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="2e8f6-108">Konu [örnek XSD dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) bu belgeyi doğrulamak için kullanılan bir XSD içerir.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="2e8f6-109">Kullandığı `xs:key` ve `xs:keyref` , kurmak için XSD özelliklerini `CustomerID` özniteliği `Customer` öğesidir bir anahtarı ve arasında bir ilişki oluşturmak için `CustomerID` her öğesinde `Order` öğesi ve `CustomerID` her özniteliği `Customer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="2e8f6-110">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bu ilişkinin kullanarak yararlanabilirsiniz `Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="2e8f6-111">Kullanılabilir herhangi bir dizin olduğundan zayıf çalışma zamanı performans böyle birleştirme'nin elde edersiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="2e8f6-112">Hakkında ayrıntılı bilgi için `Join`, bkz: [birleştirme işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2e8f6-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e8f6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e8f6-113">Example</span></span>  
 <span data-ttu-id="2e8f6-114">Aşağıdaki örnek birleştirmeler `Customer` öğelerine `Order` öğeleri ve içeren yeni bir XML belgesi oluşturur `CompanyName` siparişleri öğesinde.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="2e8f6-115">Sorguyu çalıştırmadan önce örnek belge şeması ile uyumlu doğrular [örnek XSD dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="2e8f6-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="2e8f6-116">Bu birleştirme yan tümcesi her zaman çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="2e8f6-117">Bu sorgu önce tüm alır `Customer` öğeleri ve bunları birleştirir `Order` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="2e8f6-118">Yalnızca siparişleri sahip müşteriler için seçtiği bir `CustomerID` "K" büyüktür.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="2e8f6-119">Ardından yeni bir proje `Order` her sipariş içinde müşteri bilgilerini içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="2e8f6-120">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2e8f6-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2e8f6-121">Bu örnekte aşağıdaki XSD şema kullanır: [örnek XSD dosyası: müşteriler ve siparişler](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="2e8f6-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="2e8f6-122">Bu şekilde birleştirme çok iyi gerçekleştirmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="2e8f6-123">Birleştirmeler doğrusal arama gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="2e8f6-124">Karma tabloları veya performansla yardımcı olması için dizin yok.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="2e8f6-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2e8f6-125">This code produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="2e8f6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e8f6-126">See Also</span></span>  
 [<span data-ttu-id="2e8f6-127">Gelişmiş sorgu teknikler (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e8f6-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
