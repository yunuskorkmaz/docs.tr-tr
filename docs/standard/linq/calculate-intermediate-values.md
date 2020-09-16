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
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a><span data-ttu-id="48abf-103">Ara değerleri hesaplama (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="48abf-103">How to calculate intermediate values (LINQ to XML)</span></span>

<span data-ttu-id="48abf-104">Bu makalede, C# ve Visual Basic sıralamada, filtrelemede ve seçiminde kullanılmak üzere ara değerlerin nasıl hesaplanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48abf-104">This article shows how to calculate intermediate values for use in sorting, filtering, and selecting in C# and Visual Basic.</span></span>

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a><span data-ttu-id="48abf-105">Örnek: `let` öğe verilerine göre hesaplamak için yan tümcesini kullanın</span><span class="sxs-lookup"><span data-stu-id="48abf-105">Example: Use the `let` clause to calculate based on element data</span></span>

<span data-ttu-id="48abf-106">Aşağıdaki örnek, `let` öğelerinden sayısal değerlerin ürünlerini hesaplamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="48abf-106">The following example uses the `let` clause to calculate products of numerical values from elements.</span></span> <span data-ttu-id="48abf-107">XML belgesi [örnek xml dosyası kullanır: sayısal veri](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="48abf-107">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

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

<span data-ttu-id="48abf-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="48abf-108">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a><span data-ttu-id="48abf-109">Örnek: bir ad alanında olan XML 'den hesaplama</span><span class="sxs-lookup"><span data-stu-id="48abf-109">Example: Calculate from XML that's in a namespace</span></span>

<span data-ttu-id="48abf-110">Aşağıdaki örnek, daha önce olduğu gibi, bir ad alanında olan XML için de aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="48abf-110">The following example shows the same query as before, but for XML that's in a namespace.</span></span> <span data-ttu-id="48abf-111">XML belgesi [Sample XML dosyasını kullanır: bir ad alanında sayısal veri](sample-xml-file-numerical-data-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="48abf-111">It uses the XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="48abf-112">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="48abf-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

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

<span data-ttu-id="48abf-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="48abf-113">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a><span data-ttu-id="48abf-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48abf-114">See also</span></span>

- [<span data-ttu-id="48abf-115">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48abf-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
