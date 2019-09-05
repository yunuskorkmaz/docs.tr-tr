---
title: 'Nasıl yapılır: Alt öğeleri bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: 602e04eaf5dff9f95a495daea9606afb8c162bb2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253718"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="1c0bd-102">Nasıl yapılır: Alt öğeleri bul (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1c0bd-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="1c0bd-103">Bu konu, belirli bir ada sahip alt öğelerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c0bd-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="1c0bd-104">XPath ifadesi `//Name`.</span><span class="sxs-lookup"><span data-stu-id="1c0bd-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c0bd-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c0bd-105">Example</span></span>  
 <span data-ttu-id="1c0bd-106">Bu örnek adlı `Name`tüm alt öğeleri bulur.</span><span class="sxs-lookup"><span data-stu-id="1c0bd-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="1c0bd-107">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birden çok satın alma siparişi (](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="1c0bd-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="1c0bd-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1c0bd-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
