---
title: Elementler topluluğu (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 89799b17115fb56a93bda5fbc144b21b334a6974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345013"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Elementler topluluğu (LINQ - XML) (C#) nasıl alınır?
Bu konu <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi gösterir. Bu yöntem, bir öğenin alt öğelerinin bir koleksiyon alır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `purchaseOrder` öğenin alt öğeleri ile yineler.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir.  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](./linq-to-xml-axes-overview.md)
