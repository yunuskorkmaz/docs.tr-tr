---
title: Öğeleri sıralama-LINQ to XML
description: Sonuçlarını sıralayan bir sorgu yazmayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 0e93add12e39c71c7312036917d42dd53450b712
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550071"
---
# <a name="how-to-sort-elements-linq-to-xml"></a><span data-ttu-id="bf954-103">Öğeleri sıralama (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bf954-103">How to sort elements (LINQ to XML)</span></span>

<span data-ttu-id="bf954-104">XML 'yi sorguladığınızda sonuçlarınızı sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf954-104">You can sort your results when you query XML.</span></span> <span data-ttu-id="bf954-105">Bu makalede iki örnek sunulmaktadır: ilki, bir ad alanında *olmayan* XML için sonuçları sıralar, *ikincisi ise bir ad alanında olan XML* için de aynı sıralamayı yapar.</span><span class="sxs-lookup"><span data-stu-id="bf954-105">This article provides two examples: the first sorts results for XML that *isn't* in a namespace, and the second does the same sort, but for XML that *is* in a namespace.</span></span>

## <a name="example-write-a-query-that-sorts-its-results"></a><span data-ttu-id="bf954-106">Örnek: sonuçlarını sıralayan bir sorgu yazın</span><span class="sxs-lookup"><span data-stu-id="bf954-106">Example: Write a query that sorts its results</span></span>

<span data-ttu-id="bf954-107">Bu örnek, sonuçlarını sıralayan bir sorgunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf954-107">This example shows how to write a query that sorts its results.</span></span> <span data-ttu-id="bf954-108">XML belgesi [örnek xml dosyası kullanır: sayısal veri](sample-xml-file-numerical-data.md).</span><span class="sxs-lookup"><span data-stu-id="bf954-108">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> prices =
    from el in root.Elements("Data")
    let price = (decimal)el.Element("Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim prices As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let price = Convert.ToDecimal(el.<Price>.Value) _
    Order By (price) _
    Select price
For Each el As Decimal In prices
    Console.WriteLine(el)
Next
```

<span data-ttu-id="bf954-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bf954-109">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a><span data-ttu-id="bf954-110">Örnek: bir ad alanına sonuçlarını sıralayan bir sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="bf954-110">Example: Write a query in a namespace that sorts its results</span></span>

<span data-ttu-id="bf954-111">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf954-111">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="bf954-112">XML belgesi [örnek xml dosyası kullanır: bir ad alanında sayısal veri](sample-xml-file-numerical-data-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="bf954-112">It uses XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="bf954-113">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bf954-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace aw = "http://www.adatum.com";
IEnumerable<decimal> prices =
    from el in root.Elements(aw + "Data")
    let price = (decimal)el.Element(aw + "Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim prices As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let price = Convert.ToDecimal(el.<Price>.Value) _
            Order By (price) _
            Select price
        For Each el As Decimal In prices
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

<span data-ttu-id="bf954-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bf954-114">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a><span data-ttu-id="bf954-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf954-115">See also</span></span>

- [<span data-ttu-id="bf954-116">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="bf954-116">Sorting Data (C#)</span></span>](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="bf954-117">Verileri sıralama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf954-117">Sorting Data (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="bf954-118">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf954-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
