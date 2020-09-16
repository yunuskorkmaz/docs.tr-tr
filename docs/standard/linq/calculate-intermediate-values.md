---
title: Ara değerleri hesaplama-LINQ to XML
description: Sıralama, filtreleme ve seçme sırasında kullanılmak üzere ara değerleri hesaplayın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: c37926b93e0dc11255fd27c312679f6286fa7e5d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558120"
---
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a>Ara değerleri hesaplama (LINQ to XML)

Bu makalede, C# ve Visual Basic sıralamada, filtrelemede ve seçiminde kullanılmak üzere ara değerlerin nasıl hesaplanacağı gösterilmektedir.

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a>Örnek: `let` öğe verilerine göre hesaplamak için yan tümcesini kullanın

Aşağıdaki örnek, `let` öğelerinden sayısal değerlerin ürünlerini hesaplamak için yan tümcesini kullanır. XML belgesi [örnek xml dosyası kullanır: sayısal veri](sample-xml-file-numerical-data.md).

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> extensions =
    from el in root.Elements("Data")
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim extensions As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
    Where extension > 25 _
    Order By extension _
    Select extension
For Each ex As Decimal In extensions
    Console.WriteLine(ex)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a>Örnek: bir ad alanında olan XML 'den hesaplama

Aşağıdaki örnek, daha önce olduğu gibi, bir ad alanında olan XML için de aynı sorguyu gösterir. XML belgesi [Sample XML dosyasını kullanır: bir ad alanında sayısal veri](sample-xml-file-numerical-data-namespace.md).

Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<decimal> extensions =
    from el in root.Elements(ad + "Data")
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Imports <xmlns="http://www.adatum.com">

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim extensions As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
            Where extension > 25 _
            Order By extension _
            Select extension
        For Each ex As Decimal In extensions
            Console.WriteLine(ex)
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a>Ayrıca bkz.

- [Temel sorgular (LINQ to XML) (Visual Basic)](./find-element-specific-attribute.md)
