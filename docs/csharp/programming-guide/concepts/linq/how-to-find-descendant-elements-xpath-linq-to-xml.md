---
title: 'Nasıl yapılır: alt öğeleri bulma (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: df1b151948b7b11757f2f8f312fa1f0bba00673a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099049"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="08185-102">Nasıl yapılır: alt öğeleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="08185-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="08185-103">Bu konuda, belirli bir ada sahip alt öğeleri almak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08185-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="08185-104">XPath ifadesi `//Name`.</span><span class="sxs-lookup"><span data-stu-id="08185-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08185-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="08185-105">Example</span></span>  
 <span data-ttu-id="08185-106">Bu örnek adlı tüm alt öğeleri bulan `Name`.</span><span class="sxs-lookup"><span data-stu-id="08185-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="08185-107">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: birden fazla satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="08185-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="08185-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="08185-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08185-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08185-109">See Also</span></span>

- [<span data-ttu-id="08185-110">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="08185-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
