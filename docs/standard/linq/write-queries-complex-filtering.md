---
title: Karmaşık filtreleme ile sorguları yazma-LINQ to XML
description: Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz. Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553928"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a>Karmaşık filtrelemeye sahip sorgular yazma (LINQ to XML)

Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz. Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir. Bu makalede, karmaşık filtrelemeye sahip bir sorgu yazma örneği verilmiştir.

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a>Örnek: yan tümcede iç içe bir sorgu ile bulma `Where`

Bu örnek, tüm öğelerin nasıl bulunacağını gösterir `PurchaseOrder` :

- `Address` `Type` Özniteliği "Shipping" değerine eşit olan bir alt öğe.
- `State`"NY" değerine eşit olan bir alt öğe.

Yan tümcesinde iç içe geçmiş bir sorgu kullanır `Where` ve `Any` koleksiyonda herhangi bir öğe varsa işleç döndürülür `true` . Örnek, XML belgesi [örnek xml dosyasını kullanır: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md).

İşleci hakkında daha fazla bilgi için `Any` bkz. [nicelik belirteci Işlemleri (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) ve [nicelik belirteci işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrders.xml")
Dim purchaseOrders As IEnumerable(Of XElement) = _
    From el In root.<PurchaseOrder> _
    Where _
        (From add In el.<Address> _
        Where _
             add.@Type = "Shipping" And _
             add.<State>.Value = "NY" _
        Select add) _
    .Any() _
    Select el
For Each el As XElement In purchaseOrders
    Console.WriteLine(el.@PurchaseOrderNumber)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a>Örnek: bir ad alanında bulunan XML içinde bulma

Aşağıdaki örnek, yukarıdaki gibi, ancak bir ad alanında olan XML için de aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

Bu örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders-namespace.md).

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim purchaseOrders As IEnumerable(Of XElement) = _
            From el In root.<aw:PurchaseOrder> _
            Where _
                (From add In el.<aw:Address> _
                Where _
                     add.@aw:Type = "Shipping" And _
                     add.<aw:State>.Value = "NY" _
                Select add) _
            .Any() _
            Select el
        For Each el As XElement In purchaseOrders
            Console.WriteLine(el.@aw:PurchaseOrderNumber)
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
99505
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Projeksiyon Işlemleri (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [Nicelik belirteci Işlemleri (C#)](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [XML Alt Axis Özelliği (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML Özniteliği Axis Özelliği (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML Değeri Özelliği (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Projeksiyon Işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [Nicelik belirteci Işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
