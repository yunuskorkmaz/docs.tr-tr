---
title: 'Nasıl yapılır: ilgili öğeleri (XPath-LINQ-XML) bulma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
ms.openlocfilehash: 24a8f252d0c703cc7883ae1408120b8cae018331
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643186"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="df95d-102">Nasıl yapılır: ilgili öğeleri (XPath-LINQ-XML) bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df95d-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="df95d-103">Bu konu, bir öğe başka bir öğe değeri tarafından başvurulan bir öznitelik seçme alma gösterir.</span><span class="sxs-lookup"><span data-stu-id="df95d-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="df95d-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="df95d-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="df95d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="df95d-105">Example</span></span>  
 <span data-ttu-id="df95d-106">Bu örnek 12 bulur `Order` öğesini ve ardından bu sipariş için müşteri bulur.</span><span class="sxs-lookup"><span data-stu-id="df95d-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="df95d-107">.Net listesinde içine dizin 'zero' bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="df95d-107">Note that indexing into a list in .Net is 'zero' based.</span></span> <span data-ttu-id="df95d-108">Bir XPath kuralının koşulu düğümler koleksiyonuna dizin '' dayalı biridir.</span><span class="sxs-lookup"><span data-stu-id="df95d-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="df95d-109">Bu örnekte bu farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="df95d-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="df95d-110">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: müşteriler ve siparişler (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="df95d-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")  
  
' LINQ to XML query  
Dim customer1 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        ToList()(11).<CustomerID>(0).Value _  
    Select el).First()  
  
' An alternate way to write the query that avoids creation  
' of a System.Collections.Generic.List:  
Dim customer2 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        Skip(11).First().<CustomerID>(0).Value _  
    Select el).First()  
  
' XPath expression  
Dim customer3 As XElement = co.XPathSelectElement _  
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")  
  
If customer1 Is customer2 And customer1 Is customer3 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(customer1)  
```  
  
 <span data-ttu-id="df95d-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="df95d-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
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
</Customer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df95d-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df95d-112">See Also</span></span>  
 [<span data-ttu-id="df95d-113">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df95d-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
