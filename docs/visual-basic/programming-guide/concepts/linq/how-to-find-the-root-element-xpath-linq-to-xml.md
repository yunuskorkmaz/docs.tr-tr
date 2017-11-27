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
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: kök öğe (XPath-LINQ-XML) bulunamadı (Visual Basic)
Bu konu XPath Kök öğeyle alma gösterir ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 XPath ifadesi şöyledir:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Örnek  
 Bu örnekte, kök öğe bulur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML XPath kullanıcıların (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
