---
title: Varsayılan ad alanları kapsamı-LINQ to XML
description: XML ağacında temsil edilen varsayılan ad alanları sorgular kapsamında değildir. Bu, doğru ve hatalı şekilde sorgulamada yanlış yollar sunar.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553934"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a><span data-ttu-id="923fa-104">Varsayılan ad alanlarının kapsamı (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="923fa-104">Scope of default namespaces (LINQ to XML)</span></span>

<span data-ttu-id="923fa-105">XML ağacında temsil edilen varsayılan ad alanları sorgular kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="923fa-105">Default namespaces as represented in the XML tree aren't in scope for queries.</span></span> <span data-ttu-id="923fa-106">Varsayılan bir ad alanında olan XML varsa, sorguda kullanılacak nitelikli bir ad oluşturmak için ad alanını yerel adla birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="923fa-106">If you have XML that's in a default namespace, you must combine a namespace with the local name to make a qualified name to be used in the query.</span></span>

<span data-ttu-id="923fa-107">Varsayılan ad alanı olan bir XML ağacını sorgularken yaygın bir hata, XML 'nin bir ad alanında olmadığı gibi sorguyu yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="923fa-107">A common mistake in querying an XML tree that has a default namespace is to write the query as if the XML weren't in a namespace.</span></span> <span data-ttu-id="923fa-108">İlk örnekte, varsayılan bir ad alanının tipik hatalı bir sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="923fa-108">The first example shows a typical improper query of a default namespace.</span></span> <span data-ttu-id="923fa-109">İkincisi, doğru bir sorgu gösterir.</span><span class="sxs-lookup"><span data-stu-id="923fa-109">The second shows a proper query.</span></span>

## <a name="example-improper-query-of-xml-in-a-namespace"></a><span data-ttu-id="923fa-110">Örnek: bir ad alanında hatalı XML sorgusu</span><span class="sxs-lookup"><span data-stu-id="923fa-110">Example: Improper query of XML in a namespace</span></span>

<span data-ttu-id="923fa-111">Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren yanlış bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="923fa-111">This example shows the creation of XML in a namespace, and an improper query that returns an empty result set.</span></span>

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

<span data-ttu-id="923fa-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="923fa-112">This example produces the following output:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a><span data-ttu-id="923fa-113">Örnek: bir ad alanında XML 'nin doğru sorgusu</span><span class="sxs-lookup"><span data-stu-id="923fa-113">Example:  Proper query of XML in a namespace</span></span>

<span data-ttu-id="923fa-114">Bu örnekte, bir ad alanında XML oluşturulması ve uygun bir sorgu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="923fa-114">This example shows the creation of XML in a namespace, and a proper query.</span></span>

<span data-ttu-id="923fa-115">C# ' de, doğru yaklaşım bir nesneyi bildirmek ve başlatmak <xref:System.Xml.Linq.XNamespace> ve nesneleri belirtirken kullanmak <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="923fa-115">In C#, the correct approach is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="923fa-116">Bu durumda, yöntemin bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> bir <xref:System.Xml.Linq.XName> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="923fa-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="923fa-117">Visual Basic kullanırken doğru yaklaşım, genel bir varsayılan ad alanını bildirmek ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="923fa-117">The correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="923fa-118">Bu, tüm XML özelliklerini varsayılan ad alanına koyar.</span><span class="sxs-lookup"><span data-stu-id="923fa-118">This places all XML properties in the default namespace.</span></span>

<span data-ttu-id="923fa-119">Kod aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="923fa-119">Here is the code:</span></span>

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
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="923fa-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="923fa-120">This example produces the following output:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="923fa-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="923fa-121">See also</span></span>

- [<span data-ttu-id="923fa-122">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="923fa-122">Namespaces overview</span></span>](namespaces-overview.md)
