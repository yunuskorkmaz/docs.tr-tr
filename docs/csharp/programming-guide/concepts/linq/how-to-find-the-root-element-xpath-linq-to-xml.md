---
title: 'Nasıl yapılır: kök öğe (XPath-LINQ-XML) Bul (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: a7c15c8eb688f70b2d1633fc5c094b02cc97031c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Nasıl yapılır: kök öğe (XPath-LINQ-XML) Bul (C#)
Bu konu XPath Kök öğeyle alma gösterir ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 XPath ifadesi şöyledir:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Örnek  
 Bu örnekte, kök öğe bulur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML XPath kullanıcıların (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
