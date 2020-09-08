---
title: Ad alanlarında XML üzerinde sorgu yazma-LINQ to XML
description: Bir ad alanında bulunan XML üzerinde bir sorgu yazmak için, doğru ad alanına sahip XName nesnelerini kullanırsınız. Bunu C# ve Visual Basic ve sorgu oluşturma hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 7d2c765c30409b019bf4723b9161c577e2074c04
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553028"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-linq-to-xml"></a><span data-ttu-id="36ee2-104">Ad alanlarında XML üzerinde sorgu yazma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="36ee2-104">How to write queries on XML in namespaces (LINQ to XML)</span></span>

<span data-ttu-id="36ee2-105">Bir ad alanında bulunan XML üzerinde bir sorgu yazmak için, <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="36ee2-105">To write a query on XML that's in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>

<span data-ttu-id="36ee2-106">C# için en yaygın yaklaşım, <xref:System.Xml.Linq.XNamespace> URI 'yi içeren bir dize kullanarak başlatmak, ardından ad alanını yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="36ee2-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>

<span data-ttu-id="36ee2-107">Visual Basic için en yaygın yaklaşım genel bir ad alanı tanımlamaktır ve sonra genel ad alanını kullanan XML değişmez değerlerini ve XML özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36ee2-107">For Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="36ee2-108">Genel bir varsayılan ad alanı tanımlayabilirsiniz. Bu durumda, XML sabit değerlerinde bulunan öğeler varsayılan olarak ad alanında yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="36ee2-108">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="36ee2-109">Alternatif olarak, ön ek içeren bir genel ad alanı tanımlayabilir ve sonra öneki XML sabit değerlerinde ve XML özelliklerinde gereken şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36ee2-109">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals and in XML properties.</span></span> <span data-ttu-id="36ee2-110">Diğer XML formlarında olduğu gibi, özniteliklerin her zaman varsayılan olarak ad alanı yoktur.</span><span class="sxs-lookup"><span data-stu-id="36ee2-110">As with other forms of XML, attributes are always in no namespace by default.</span></span>

<span data-ttu-id="36ee2-111">Bu makaledeki ilk örnekte, varsayılan bir ad alanında bir XML ağacının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="36ee2-111">The first example in this article shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="36ee2-112">İkincisi, bir ad alanında öneki olan bir XML ağacının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="36ee2-112">The second shows how to create an XML tree in a namespace with a prefix.</span></span>

## <a name="example-create-a-tree-in-a-default-namespace-and-retrieve-elements"></a><span data-ttu-id="36ee2-113">Örnek: varsayılan bir ad alanında ağaç oluşturma ve öğeleri alma</span><span class="sxs-lookup"><span data-stu-id="36ee2-113">Example: Create a tree in a default namespace and retrieve elements</span></span>

<span data-ttu-id="36ee2-114">Aşağıdaki örnek, varsayılan bir ad alanında olan bir XML ağacı oluşturur ve ardından bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="36ee2-114">The following example creates an XML tree that's in a default namespace, and then retrieves a collection of elements.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
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
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
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
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="36ee2-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="36ee2-115">This example produces the following output:</span></span>

```output
1
2
3
```

## <a name="example-create-a-tree-in-a-namespace-with-a-prefix-and-retrieve-elements"></a><span data-ttu-id="36ee2-116">Örnek: bir ad alanında önek ve alma öğeleri içeren bir ağaç oluşturma</span><span class="sxs-lookup"><span data-stu-id="36ee2-116">Example: Create a tree in a namespace with a prefix and retrieve elements</span></span>

<span data-ttu-id="36ee2-117">C# ' ta, ön ek içeren bir ad alanı kullanan bir XML ağacına veya varsayılan bir ad alanı olan bir XML ağacına sorgu yazarken aynı şekilde sorgular yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="36ee2-117">In C#, you write queries in the same way regardless of whether you're writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>

<span data-ttu-id="36ee2-118">Aşağıdaki örnek, öneki olan bir ad alanında bulunan bir XML ağacı oluşturur ve ardından bir öğe koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="36ee2-118">The following example creates an XML tree that's in a namespace with a prefix, and then retrieves a collection of elements.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
    <aw:Child>1</aw:Child>
    <aw:Child>2</aw:Child>
    <aw:Child>3</aw:Child>
    <aw:AnotherChild>4</aw:AnotherChild>
    <aw:AnotherChild>5</aw:AnotherChild>
    <aw:AnotherChild>6</aw:AnotherChild>
</aw:Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>1</aw:Child>
                <aw:Child>2</aw:Child>
                <aw:Child>3</aw:Child>
                <aw:AnotherChild>4</aw:AnotherChild>
                <aw:AnotherChild>5</aw:AnotherChild>
                <aw:AnotherChild>6</aw:AnotherChild>
            </aw:Root>
        Dim c1 As IEnumerable(Of XElement) = _
            From el In root.<aw:Child> _
            Select el
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
    End Sub
End Module
```

<span data-ttu-id="36ee2-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="36ee2-119">This example produces the following output:</span></span>

```output
1
2
3
```

## <a name="see-also"></a><span data-ttu-id="36ee2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ee2-120">See also</span></span>

- [<span data-ttu-id="36ee2-121">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="36ee2-121">Namespaces overview</span></span>](namespaces-overview.md)
