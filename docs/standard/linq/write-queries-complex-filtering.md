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
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a><span data-ttu-id="26f19-104">Karmaşık filtrelemeye sahip sorgular yazma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="26f19-104">How to write queries with complex filtering (LINQ to XML)</span></span>

<span data-ttu-id="26f19-105">Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26f19-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="26f19-106">Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="26f19-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="26f19-107">Bu makalede, karmaşık filtrelemeye sahip bir sorgu yazma örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="26f19-107">This article gives an example of writing a query with complex filtering.</span></span>

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a><span data-ttu-id="26f19-108">Örnek: yan tümcede iç içe bir sorgu ile bulma `Where`</span><span class="sxs-lookup"><span data-stu-id="26f19-108">Example: Find with a nested query in the `Where` clause</span></span>

<span data-ttu-id="26f19-109">Bu örnek, tüm öğelerin nasıl bulunacağını gösterir `PurchaseOrder` :</span><span class="sxs-lookup"><span data-stu-id="26f19-109">This example shows how to find all `PurchaseOrder` elements that have:</span></span>

- <span data-ttu-id="26f19-110">`Address` `Type` Özniteliği "Shipping" değerine eşit olan bir alt öğe.</span><span class="sxs-lookup"><span data-stu-id="26f19-110">A child `Address` element whose `Type` attribute equals "Shipping".</span></span>
- <span data-ttu-id="26f19-111">`State`"NY" değerine eşit olan bir alt öğe.</span><span class="sxs-lookup"><span data-stu-id="26f19-111">A child `State` element that equals "NY".</span></span>

<span data-ttu-id="26f19-112">Yan tümcesinde iç içe geçmiş bir sorgu kullanır `Where` ve `Any` koleksiyonda herhangi bir öğe varsa işleç döndürülür `true` .</span><span class="sxs-lookup"><span data-stu-id="26f19-112">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="26f19-113">Örnek, XML belgesi [örnek xml dosyasını kullanır: birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders.md).</span><span class="sxs-lookup"><span data-stu-id="26f19-113">The example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="26f19-114">İşleci hakkında daha fazla bilgi için `Any` bkz. [nicelik belirteci Işlemleri (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) ve [nicelik belirteci işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="26f19-114">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) and [Quantifier Operations (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>

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

<span data-ttu-id="26f19-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="26f19-115">This example produces the following output:</span></span>

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a><span data-ttu-id="26f19-116">Örnek: bir ad alanında bulunan XML içinde bulma</span><span class="sxs-lookup"><span data-stu-id="26f19-116">Example: Find in XML that's in a namespace</span></span>

<span data-ttu-id="26f19-117">Aşağıdaki örnek, yukarıdaki gibi, ancak bir ad alanında olan XML için de aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="26f19-117">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="26f19-118">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="26f19-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="26f19-119">Bu örnek, XML belgesi [örnek xml dosyası kullanır: bir ad alanında birden fazla satın alma siparişi](sample-xml-file-multiple-purchase-orders-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="26f19-119">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

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

<span data-ttu-id="26f19-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="26f19-120">This example produces the following output:</span></span>

```output
99505
```

## <a name="see-also"></a><span data-ttu-id="26f19-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26f19-121">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="26f19-122">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="26f19-122">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="26f19-123">Nicelik belirteci Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="26f19-123">Quantifier Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [<span data-ttu-id="26f19-124">XML Alt Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f19-124">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="26f19-125">XML Özniteliği Axis Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f19-125">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="26f19-126">XML Değeri Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f19-126">XML Value Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="26f19-127">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f19-127">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="26f19-128">Nicelik belirteci Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f19-128">Quantifier Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
