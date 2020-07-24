---
title: Kök öğeyi bulma (XPath-LINQ to XML) (C#)
description: Bu C# örneği, örnek bir XML belgesi için kök öğe alma için XPath 'i LINQ to XML karşılaştırır.
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 220899823210c5cd6e9834541ca87e4d8394b4ff
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105185"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Kök öğeyi bulma (XPath-LINQ to XML) (C#)
Bu konu, XPath ve ile kök öğesinin nasıl alınacağını gösterir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 XPath ifadesi:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Örnek  
 Bu örnek, kök öğesini bulur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
```output  
Results are identical  
PurchaseOrders  
```  
