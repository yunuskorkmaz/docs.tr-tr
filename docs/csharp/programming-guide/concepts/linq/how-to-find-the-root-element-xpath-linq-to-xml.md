---
title: Kök öğesi (XPath-LINQ - XML) (C#) nasıl bulabilirim?
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1c5526f436b5b9d88ca359ef7e0fc04c5c3cf43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345957"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>Kök öğesi (XPath-LINQ - XML) (C#) nasıl bulabilirim?
Bu konu, XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 XPath ifadesi:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Örnek  
 Bu örnek, kök öğeyi bulur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Birden Çok SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Results are identical  
PurchaseOrders  
```  
