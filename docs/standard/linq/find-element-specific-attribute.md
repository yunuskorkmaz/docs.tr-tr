---
title: Belirli bir özniteliğe sahip bir öğe bulma-LINQ to XML
description: Özniteliği belirli bir değere sahip olan bir öğeyi bulmayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 4c74de90a348d81ac87c98bf6ee27f3c78f34e83
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552871"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a>Belirli bir özniteliğe sahip bir öğe bulma (LINQ to XML)

Bu makalede, özniteliği belirli bir değere sahip olan bir öğenin nasıl bulunacağını gösteren örnekler verilmektedir.

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a>Örnek: özniteliği belirli bir değere sahip olan bir öğe bul

Aşağıdaki örnek, `Address` `Type` "Faturalandırma" değerine sahip bir özniteliğe sahip olan öğenin nasıl bulunacağını gösterir. Örnek, XML belgesi [örnek xml dosyasını kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).

```csharp
XElement root = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> address =
    from el in root.Elements("Address")
    where (string)el.Attribute("Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrder.xml")
Dim address As IEnumerable(Of XElement) = _
    From el In root.<Address> _
    Where el.@Type = "Billing" _
    Select el
For Each el As XElement In address
    Console.WriteLine(el)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Address Type="Billing">
  <Name>Tai Yee</Name>
  <Street>8 Oak Avenue</Street>
  <City>Old Town</City>
  <State>PA</State>
  <Zip>95819</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a>Örnek: bir ad alanında bulunan XML içinde bir öğe bulun

Aşağıdaki örnek, bir ad alanında olan XML için aynı sorguyu gösterir. XML belgesi [örnek xml dosyası kullanır: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-namespace.md).

Ad alanları hakkında daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

```csharp
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> address =
    from el in root.Elements(aw + "Address")
    where (string)el.Attribute(aw + "Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim address As IEnumerable(Of XElement) = _
            From el In root.<aw:Address> _
            Where el.@aw:Type = "Billing" _
            Select el
        For Each el As XElement In address
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir::

```xml
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">
  <aw:Name>Tai Yee</aw:Name>
  <aw:Street>8 Oak Avenue</aw:Street>
  <aw:City>Old Town</aw:City>
  <aw:State>PA</aw:State>
  <aw:Zip>95819</aw:Zip>
  <aw:Country>USA</aw:Country>
</aw:Address>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Standart sorgu Işleçlerine genel bakış (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Projeksiyon Işlemleri (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [Temel sorgular (LINQ to XML) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Projeksiyon Işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
