---
title: 'Nasıl yapılır: Öğelerin koleksiyonunu al (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 0ca40b77a78f155292dfbb26471442450bf16b9b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592646"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Nasıl yapılır: Öğelerin koleksiyonunu al (LINQ to XML) (C#)
Bu konuda <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi gösterilmektedir. Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `purchaseOrder` öğesinin alt öğeleri boyunca yinelenir.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
