---
title: Bağlam LINQ to XML göre öğeleri bulan bir sorgu yazma
description: Bağlam temelinde öğeleri seçen bir sorgu yazın; Örneğin, sonuçları önceki veya sonraki eşdüzey öğelere göre filtreleyin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 2c51a790a2a8adef565f186992a6a3faa5f102ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550462"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-linq-to-xml"></a><span data-ttu-id="5ddd4-103">Bağlam temelinde öğeleri bulan bir sorgu yazma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5ddd4-103">How to write a query that finds elements based on context (LINQ to XML)</span></span>

<span data-ttu-id="5ddd4-104">Bazen, bağlamlarına göre öğeleri seçen bir sorgu yazmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5ddd4-104">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="5ddd4-105">Örneğin, önceki veya sonraki eşdüzey öğelere ya da alt veya üst öğe öğelerine göre filtrelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ddd4-105">For example, you might want to filter based on preceding or following sibling elements, or on child or ancestor elements.</span></span>

<span data-ttu-id="5ddd4-106">Bunu, bir sorgu yazarak ve yan tümcesindeki sorgunun sonuçlarını kullanarak yapabilirsiniz `where` .</span><span class="sxs-lookup"><span data-stu-id="5ddd4-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="5ddd4-107">İlk olarak null ile test etmeniz ve sonra değeri test etmeniz gerekiyorsa, sorguyu bir yan tümce içinde yapmak daha kolay olur `let` ve sonra sonuçları `where` yan tümce içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="5ddd4-107">If you have to first test against null, and then test the value, it's more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>

## <a name="example-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a><span data-ttu-id="5ddd4-108">Örnek: `p` hemen arkasından bir öğe gelen öğeleri seçin `ul`</span><span class="sxs-lookup"><span data-stu-id="5ddd4-108">Example: Select `p` elements that are immediately followed by a `ul` element</span></span>

<span data-ttu-id="5ddd4-109">Aşağıdaki örnek, `p` hemen arkasından bir öğesi olan tüm öğeleri seçer `ul` .</span><span class="sxs-lookup"><span data-stu-id="5ddd4-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>

```csharp
XElement doc = XElement.Parse(@"<Root>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

IEnumerable<XElement> items =
    from e in doc.Descendants("p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name.LocalName == "ul"
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Dim doc As XElement = _
    <Root>
        <p id='1'/>
        <ul>abc</ul>
        <Child>
            <p id='2'/>
            <notul/>
            <p id='3'/>
            <ul>def</ul>
            <p id='4'/>
        </Child>
        <Child>
            <p id='5'/>
            <notul/>
            <p id='6'/>
            <ul>abc</ul>
            <p id='7'/>
        </Child>
    </Root>

Dim items As IEnumerable(Of XElement) = _
    From e In doc...<p> _
    Let z = e.ElementsAfterSelf().FirstOrDefault() _
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _
    Select e

For Each e As XElement In items
    Console.WriteLine("id = {0}", e.@<id>)
Next
```

<span data-ttu-id="5ddd4-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5ddd4-110">This example produces the following output:</span></span>

```output
id = 1
id = 3
id = 6
```

## <a name="example-in-a-namespace-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a><span data-ttu-id="5ddd4-111">Örnek: bir ad alanında `p` hemen arkasından bir öğe gelen öğeleri seçin `ul`</span><span class="sxs-lookup"><span data-stu-id="5ddd4-111">Example: In a namespace select `p` elements that are immediately followed by a `ul` element</span></span>

<span data-ttu-id="5ddd4-112">Aşağıdaki örnek, yukarıdaki gibi, ancak bir ad alanında olan XML için de aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ddd4-112">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="5ddd4-113">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5ddd4-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

XNamespace ad = "http://www.adatum.com";

IEnumerable<XElement> items =
    from e in doc.Descendants(ad + "p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name == ad.GetName("ul")
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim doc As XElement = _
            <Root>
                <p id='1'/>
                <ul>abc</ul>
                <Child>
                    <p id='2'/>
                    <notul/>
                    <p id='3'/>
                    <ul>def</ul>
                    <p id='4'/>
                </Child>
                <Child>
                    <p id='5'/>
                    <notul/>
                    <p id='6'/>
                    <ul>abc</ul>
                    <p id='7'/>
                </Child>
            </Root>

        Dim items As IEnumerable(Of XElement) = _
            From e In doc...<p> _
            Let z = e.ElementsAfterSelf().FirstOrDefault() _
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _
            Select e

        For Each e As XElement In items
            Console.WriteLine("id = {0}", e.@<id>)
        Next
    End Sub
End Module
```

<span data-ttu-id="5ddd4-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5ddd4-114">This example produces the following output:</span></span>

```output
id = 1
id = 3
id = 6
```

## <a name="see-also"></a><span data-ttu-id="5ddd4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ddd4-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="5ddd4-116">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ddd4-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
