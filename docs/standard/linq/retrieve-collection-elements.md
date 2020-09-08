---
title: Öğe koleksiyonunu alma-LINQ to XML
description: Bir öğenin alt öğelerinin koleksiyonunu almak için XContainer. Elements yönteminin nasıl kullanılacağını öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: e73f608cff13f75f769f77372dc1c09949e00b0e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552961"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml"></a>Öğe koleksiyonunu alma (LINQ to XML)

Bu makalede <xref:System.Xml.Linq.XContainer.Elements%2A> , bir öğenin alt öğelerinin koleksiyonunu alan yöntemi gösterilmektedir.

## <a name="example-iterate-through-the-child-elements-of-an-element"></a>Örnek: bir öğenin alt öğeleri boyunca yineleme

Bu örnek, öğesinin alt öğeleri boyunca yinelenir `purchaseOrder` . XML belgesi [örnek xml dosyası kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> childElements =
    from el in po.Elements()
    select el;
foreach (XElement el in childElements)
    Console.WriteLine("Name: " + el.Name);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim childElements As IEnumerable(Of XElement)
childElements = _
    From el In po.Elements() _
    Select el
For Each el As XElement In childElements
    Console.WriteLine("Name: " & el.Name.ToString())
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Name: Address
Name: Address
Name: DeliveryNotes
Name: Items
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
