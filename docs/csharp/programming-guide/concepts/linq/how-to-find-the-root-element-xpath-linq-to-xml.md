---
title: 'Nasıl yapılır: Kök öğeyi bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1fea4cc630dd708a86a0f0595ac727f8b8fa40af
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593381"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Nasıl yapılır: Kök öğeyi bul (XPath-LINQ to XML) (C#)
Bu konu, XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile kök öğesinin nasıl alınacağını gösterir.  
  
 XPath ifadesi:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Örnek  
 Bu örnek, kök öğesini bulur.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birden çok satın alma siparişi (](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)LINQ to XML).  
  
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
