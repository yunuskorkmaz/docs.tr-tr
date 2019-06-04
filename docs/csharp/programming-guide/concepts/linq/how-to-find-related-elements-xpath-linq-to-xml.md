---
title: 'Nasıl yapılır: (XPath-LINQ to XML) ilgili öğeleri bulma (C#)'
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: a4260012899527662638a037fa4616a7a0d6f875
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486745"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="fa392-102">Nasıl yapılır: (XPath-LINQ to XML) ilgili öğeleri bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="fa392-102">How to: Find Related Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="fa392-103">Bu konu, başka bir öğenin değeri tarafından başvurulan öznitelik seçerek bir öğenin nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa392-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="fa392-104">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="fa392-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="fa392-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa392-105">Example</span></span>  
 <span data-ttu-id="fa392-106">Bu örnek 12 bulur `Order` öğesini ve sonra müşteri sipariş bulur.</span><span class="sxs-lookup"><span data-stu-id="fa392-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="fa392-107">. NET'te listeye dizin 'zero' bağlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa392-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="fa392-108">Bir XPath kuralının koşulu düğümler koleksiyonuna dizin '' temel biridir.</span><span class="sxs-lookup"><span data-stu-id="fa392-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="fa392-109">Bu örnekte, bu fark yansıtır.</span><span class="sxs-lookup"><span data-stu-id="fa392-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="fa392-110">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="fa392-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XDocument co = XDocument.Load("CustomersOrders.xml");  
  
// LINQ to XML query  
XElement customer1 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .ToList()[11]  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// An alternate way to write the query that avoids creation  
// of a System.Collections.Generic.List:  
XElement customer2 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .Skip(11).First()  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// XPath expression  
XElement customer3 = co.XPathSelectElement(  
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");  
  
if (customer1 == customer2 && customer1 == customer3)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(customer1);  
```  
  
 <span data-ttu-id="fa392-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fa392-111">This example produces the following output:</span></span>  
  
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
 