---
title: 'Nasıl yapılır: Bulma (XPath-LINQ to XML) kök öğe (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: a74556e4b05bc3ae02998eeb6dd3190a3bade36a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668022"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Nasıl yapılır: Bulma (XPath-LINQ to XML) kök öğe (C#)
Bu konu XPath kök öğesiyle almak nasıl gösterir ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 XPath ifadesidir:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Örnek  
 Bu örnekte, kök öğesi bulur.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Birden fazla satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML için XPath kullanıcıları (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
