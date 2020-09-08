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
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="da343-103">Belirli bir özniteliğe sahip bir öğe bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="da343-103">How to find an element with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="da343-104">Bu makalede, özniteliği belirli bir değere sahip olan bir öğenin nasıl bulunacağını gösteren örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da343-104">This article provides examples of how to find an element whose attribute has a specific value.</span></span>

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a><span data-ttu-id="da343-105">Örnek: özniteliği belirli bir değere sahip olan bir öğe bul</span><span class="sxs-lookup"><span data-stu-id="da343-105">Example: Find an element whose attribute has a specific value</span></span>

<span data-ttu-id="da343-106">Aşağıdaki örnek, `Address` `Type` "Faturalandırma" değerine sahip bir özniteliğe sahip olan öğenin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da343-106">The following example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span> <span data-ttu-id="da343-107">Örnek, XML belgesi [örnek xml dosyasını kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="da343-107">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

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

<span data-ttu-id="da343-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="da343-108">This example produces the following output:</span></span>

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

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a><span data-ttu-id="da343-109">Örnek: bir ad alanında bulunan XML içinde bir öğe bulun</span><span class="sxs-lookup"><span data-stu-id="da343-109">Example: Find an element in XML that's in a namespace</span></span>

<span data-ttu-id="da343-110">Aşağıdaki örnek, bir ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="da343-110">The following example shows the same query, but for XML that's in a namespace.</span></span> <span data-ttu-id="da343-111">XML belgesi [örnek xml dosyası kullanır: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="da343-111">It uses XML document [Sample XML file: typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

<span data-ttu-id="da343-112">Ad alanları hakkında daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da343-112">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

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

<span data-ttu-id="da343-113">Bu örnek aşağıdaki çıktıyı üretir::</span><span class="sxs-lookup"><span data-stu-id="da343-113">This example produces the following output::</span></span>

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

## <a name="see-also"></a><span data-ttu-id="da343-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da343-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="da343-115">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="da343-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="da343-116">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="da343-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="da343-117">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da343-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="da343-118">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da343-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="da343-119">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da343-119">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
