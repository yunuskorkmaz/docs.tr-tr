---
title: Tek bir alt öğe alma-LINQ to XML
description: Belirtilen ada sahip ilk alt öğeyi alın. C# ' de XContainer. element ' i ve dizi dizin oluşturucu gösterimini Visual Basic ' de kullanabilirsiniz.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553876"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a>Tek bir alt öğeyi alma (LINQ to XML)

Bu makalede, belirli bir ada sahip ilk alt öğe olan tek bir alt öğenin nasıl alınacağını açıklanmaktadır. C# ' de bunu <xref:System.Xml.Linq.XContainer.Element%2A> yöntemiyle yapabilirsiniz. Visual Basic, dizi Dizin Oluşturucu gösterimi ile bunu yapabilirsiniz.

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a>Örnek: belirtilen ada sahip olan ilk öğeyi alma

Aşağıdaki örnek `DeliveryNotes` örnek XML DOSYASıNDAKI XML belgesinden ilk öğeyi alır [: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a>Örnek: bir ad alanında bulunan XML 'den alma

Aşağıdaki örnek, yukarıdaki ile aynı şeyi yapar, ancak bir ad alanında bulunan XML için. XML belgesi [örnek xml dosyasını kullanır: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-namespace.md). Ad alanları hakkında daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim e As XElement = po.<aw:DeliveryNotes>(0)
        Console.WriteLine(e)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
