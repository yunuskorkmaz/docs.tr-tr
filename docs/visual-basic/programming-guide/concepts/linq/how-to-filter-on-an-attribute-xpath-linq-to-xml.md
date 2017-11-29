---
title: "Nasıl yapılır: bir öznitelik (XPath-LINQ-XML) üzerinde filtre (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffefb9d6-45ec-4677-a396-dd9c2b36298f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4bd1482b535035c9cae329c774e952e54d8c681
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="03d20-102">Nasıl yapılır: bir öznitelik (XPath-LINQ-XML) üzerinde filtre (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03d20-102">How to: Filter on an Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="03d20-103">Bu konu, alt öğelerini belirtilen ada sahip ve belirtilen değerli özniteliği ile alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="03d20-103">This topic shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="03d20-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="03d20-104">The XPath expression is:</span></span>  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a><span data-ttu-id="03d20-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="03d20-105">Example</span></span>  
 <span data-ttu-id="03d20-106">Bu örnekte tüm alt öğeleri adıyla bulur `Address`ile bir `Type` özniteliği "Gönderme" değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="03d20-106">This example finds all descendants elements with the name of `Address`, and with a `Type` attribute with a value of "Shipping".</span></span>  
  
 <span data-ttu-id="03d20-107">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="03d20-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In po...<Address> _  
    Where el.@Type = "Shipping" _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    po.XPathSelectElements(".//Address[@Type='Shipping']")  
  
If (list1.Count = list2.Count And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="03d20-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="03d20-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Address Type="Shipping">  
  <Name>Ellen Adams</Name>  
  <Street>123 Maple Street</Street>  
  <City>Mill Valley</City>  
  <State>CA</State>  
  <Zip>10999</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Cristian Osorio</Name>  
  <Street>456 Main Street</Street>  
  <City>Buffalo</City>  
  <State>NY</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Jessica Arnold</Name>  
  <Street>4055 Madison Ave</Street>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03d20-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03d20-109">See Also</span></span>  
 [<span data-ttu-id="03d20-110">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03d20-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
