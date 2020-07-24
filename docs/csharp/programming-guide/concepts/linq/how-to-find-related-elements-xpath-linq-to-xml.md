---
title: İlgili öğeleri bulma (XPath-LINQ to XML) (C#)
description: Bu C# örneği, başka bir öğenin değeri tarafından başvurulan bir öznitelik üzerinde seçim yapmak için XPath 'i LINQ to XML karşılaştırır.
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: 4423e7d719d39e71bcbcc9e88d052c6aff4ffb05
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105249"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="4c9e6-103">İlgili öğeleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4c9e6-103">How to find related elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="4c9e6-104">Bu konu başlığı altında, başka bir öğenin değeri tarafından başvurulan bir özniteliği seçme öğesinin nasıl alınacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c9e6-104">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="4c9e6-105">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="4c9e6-105">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="4c9e6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c9e6-106">Example</span></span>  
 <span data-ttu-id="4c9e6-107">Bu örnek 12 `Order` . öğesini bulur ve ardından o sipariş için müşteriyi bulur.</span><span class="sxs-lookup"><span data-stu-id="4c9e6-107">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="4c9e6-108">.NET 'teki bir listede dizin oluşturmanın ' sıfır ' tabanlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4c9e6-108">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="4c9e6-109">XPath koşulunda bir düğümler koleksiyonuna dizin oluşturma işlemi ' One ' tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c9e6-109">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="4c9e6-110">Bu örnek, bu farkı yansıtır.</span><span class="sxs-lookup"><span data-stu-id="4c9e6-110">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="4c9e6-111">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="4c9e6-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="4c9e6-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4c9e6-112">This example produces the following output:</span></span>  
  
```output  
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
