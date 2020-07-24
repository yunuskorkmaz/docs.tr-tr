---
title: Öğelerin koleksiyonunu alma (LINQ to XML) (C#)
description: C# içindeki Elements yöntemi bir öğenin alt öğelerinin bir koleksiyonunu alır. Bu LINQ to XML örnek, bir öğenin alt öğeleri üzerinden yinelenir.
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103352"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Öğelerin koleksiyonunu alma (LINQ to XML) (C#)
Bu konuda yöntemi gösterilmektedir <xref:System.Xml.Linq.XContainer.Elements%2A> . Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, öğesinin alt öğeleri boyunca yinelenir `purchaseOrder` .  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir.  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
