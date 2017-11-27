---
title: "Nasıl yapılır: kök öğe (XPath-LINQ-XML) bulunamadı (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 78bedc9b3f6143b1574d9063ea7ee0f08550681e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="f9a7b-102">Nasıl yapılır: kök öğe (XPath-LINQ-XML) bulunamadı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9a7b-102">How to: Find the Root Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f9a7b-103">Bu konu XPath Kök öğeyle alma gösterir ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9a7b-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="f9a7b-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="f9a7b-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="f9a7b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9a7b-105">Example</span></span>  
 <span data-ttu-id="f9a7b-106">Bu örnekte, kök öğe bulur.</span><span class="sxs-lookup"><span data-stu-id="f9a7b-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="f9a7b-107">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f9a7b-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 <span data-ttu-id="f9a7b-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="f9a7b-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9a7b-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9a7b-109">See Also</span></span>  
 [<span data-ttu-id="f9a7b-110">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9a7b-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
