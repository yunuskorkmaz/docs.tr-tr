---
title: Boş sorgu sonuçları kümelerinde hata ayıklama-LINQ to XML
description: Varsayılan bir ad alanında bir XML ağacını sorguladığınızda, XML 'nin bir ad alanında olmamasına rağmen, yaygın olarak sorgulanmasını önleyin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 3320763fffe77ddd6ca4c78e77629ec0805e4290
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553486"
---
# <a name="how-to-debug-empty-query-results-sets-linq-to-xml"></a><span data-ttu-id="d9664-103">Boş sorgu sonuçları kümelerinde hata ayıklama (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d9664-103">How to debug empty query results sets (LINQ to XML)</span></span>

<span data-ttu-id="d9664-104">XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.</span><span class="sxs-lookup"><span data-stu-id="d9664-104">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="d9664-105">Bu makaledeki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği ve daha sonra yanlış sorgulandığı tipik bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9664-105">The first set of examples in this article shows a typical way that XML in a default namespace is loaded, and then queried improperly.</span></span>

<span data-ttu-id="d9664-106">İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9664-106">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="d9664-107">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d9664-107">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

## <a name="example-an-improper-query-on-xml-in-a-namespace"></a><span data-ttu-id="d9664-108">Örnek: bir ad alanında XML üzerinde hatalı sorgu</span><span class="sxs-lookup"><span data-stu-id="d9664-108">Example: An improper query on XML in a namespace</span></span>

<span data-ttu-id="d9664-109">Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9664-109">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="d9664-110">Örnek bu sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="d9664-110">The example produces this result:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example-a-proper-query-on-xml-in-a-namespace"></a><span data-ttu-id="d9664-111">Örnek: bir ad alanında XML üzerinde doğru bir sorgu</span><span class="sxs-lookup"><span data-stu-id="d9664-111">Example: A proper query on XML in a namespace</span></span>

<span data-ttu-id="d9664-112">Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9664-112">This example shows creation of XML in a namespace, and a query that's  coded properly.</span></span>

<span data-ttu-id="d9664-113">Çözüm, bir nesneyi bildirmek ve başlatmak <xref:System.Xml.Linq.XNamespace> ve nesneleri belirtirken kullanmak <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="d9664-113">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="d9664-114">Bu durumda, yöntemin bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> bir <xref:System.Xml.Linq.XName> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="d9664-114">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="d9664-115">Örnek bu sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="d9664-115">The example produces this result:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="d9664-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9664-116">See also</span></span>

- [<span data-ttu-id="d9664-117">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9664-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
