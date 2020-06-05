---
title: 'Nasıl yapılır: İki Koleksiyonu Birleştirme (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: dc3cfd19d990fa81e00f4781cb15bf07eb9a80ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398057"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="c5364-102">Nasıl yapılır: Iki koleksiyonu birleştirin (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5364-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c5364-103">XML belgesindeki bir öğe veya öznitelik, bazen başka bir öğe veya özniteliğe başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="c5364-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="c5364-104">Örneğin, [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) XML belgesi, müşterilerin ve siparişlerin listesinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="c5364-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="c5364-105">Her `Customer` öğe bir `CustomerID` özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="c5364-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="c5364-106">Her `Order` öğe bir `CustomerID` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="c5364-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="c5364-107">`CustomerID`Her siparişte bulunan öğe, `CustomerID` bir müşterinin özniteliği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5364-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="c5364-108">[Örnek xsd dosyası: müşteriler ve siparişler](sample-xsd-file-customers-and-orders.md) , bu belgeyi doğrulamak için KULLANıLABILECEK bir xsd içerir.</span><span class="sxs-lookup"><span data-stu-id="c5364-108">The topic [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="c5364-109">`xs:key`Özniteliğin ve özelliklerini kullanarak `xs:keyref` `CustomerID` `Customer` öğe özniteliğinin bir anahtar olduğunu ve her bir öğe `CustomerID` içindeki öğe ile her bir öğedeki özniteliği arasında bir ilişki kurmayı kullanır `Order` `CustomerID` `Customer` .</span><span class="sxs-lookup"><span data-stu-id="c5364-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="c5364-110">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , yan tümcesini kullanarak bu ilişkiyi kullanabilirsiniz `Join` .</span><span class="sxs-lookup"><span data-stu-id="c5364-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="c5364-111">Kullanılabilir dizin olmadığından, bu tür bir birleştirme çalışma zamanı performansına sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c5364-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="c5364-112">Hakkında daha ayrıntılı bilgi için `Join` bkz. [JOIN işlemleri (Visual Basic)](join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c5364-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5364-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5364-113">Example</span></span>  
 <span data-ttu-id="c5364-114">Aşağıdaki örnek öğeleri öğelerine birleştirir `Customer` `Order` ve siparişlerdeki öğesini içeren yenı bir XML belgesi oluşturur `CompanyName` .</span><span class="sxs-lookup"><span data-stu-id="c5364-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="c5364-115">Sorguyu yürütmeden önce örnek, belgenin örnek XSD dosyasındaki şemayla uyumlu olduğunu doğrular [: müşteriler ve siparişler](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="c5364-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="c5364-116">Bu, JOIN yan tümcesinin her zaman çalışmasına de sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5364-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="c5364-117">Bu sorgu önce tüm `Customer` öğeleri alır ve ardından bunları `Order` öğelerine birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c5364-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="c5364-118">Yalnızca "K" dan büyük müşterilere ait siparişleri seçer `CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="c5364-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="c5364-119">Ardından `Order` , her bir sırada müşteri bilgilerini içeren yeni bir öğesi projeler.</span><span class="sxs-lookup"><span data-stu-id="c5364-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="c5364-120">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c5364-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c5364-121">Bu örnek şu XSD şemasını kullanır: [örnek xsd dosyası: müşteriler ve siparişler](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="c5364-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="c5364-122">Bu biçimde birleştirme işlemi çok iyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="c5364-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="c5364-123">Birleşimler, doğrusal bir arama yoluyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="c5364-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="c5364-124">Performansla ilgili yardım için hiçbir karma tablo veya dizin yok.</span><span class="sxs-lookup"><span data-stu-id="c5364-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="c5364-125">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c5364-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5364-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5364-126">See also</span></span>

- [<span data-ttu-id="c5364-127">Gelişmiş sorgu teknikleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5364-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
