---
title: Visual Basic LINQ to XML genel ad alanları ile çalışma
description: Ad alanının varsayılan bir ad alanı veya öneki olup olmadığı, Imports ifadesiyle Visual Basic bir ad alanı bildirirsiniz. Bu makalede Içeri aktarma deyimleri ve ad alanları ile çalışmanın diğer yönleri açıklanmaktadır.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553932"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="d1268-104">Visual Basic genel ad alanları ile çalışma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d1268-104">Work with global namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="d1268-105">Visual Basic XML sabit değerlerinin temel özelliklerinden biri, ifadesini kullanarak XML ad alanları bildirme yeteneğidir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="d1268-105">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="d1268-106">Bu özelliği kullanarak, ön ek kullanan bir XML ad alanı bildirebilir veya varsayılan bir XML ad alanı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1268-106">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>

<span data-ttu-id="d1268-107">Bu özellik iki durumda faydalıdır:</span><span class="sxs-lookup"><span data-stu-id="d1268-107">This capability is useful in two situations:</span></span>

- <span data-ttu-id="d1268-108">XML değişmez değerlerinde belirtilen ad alanları, gömülü ifadeler içine taşımaz.</span><span class="sxs-lookup"><span data-stu-id="d1268-108">Namespaces declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="d1268-109">Genel ad alanlarını bildirmek, katıştırılmış ifadeleri ad alanlarıyla birlikte kullanmak için gereken çalışma miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="d1268-109">Declaring global namespaces reduces the amount of work needed to use embedded expressions with namespaces.</span></span>
- <span data-ttu-id="d1268-110">XML özellikleriyle ad alanlarını kullanabilmeniz için genel ad alanlarını bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1268-110">You must declare global namespaces in order to use namespaces with XML properties.</span></span>

<span data-ttu-id="d1268-111">Genel ad alanlarını proje düzeyinde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1268-111">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="d1268-112">Genel ad alanlarını modül düzeyinde bildirebilirsiniz ve bu da proje düzeyi genel ad alanlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d1268-112">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="d1268-113">Son olarak, bir XML sabit değerinde genel ad alanlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1268-113">Finally, you can override global namespaces in an XML literal.</span></span>

<span data-ttu-id="d1268-114">Genel olarak tanımlanan ad alanları içindeki XML değişmez değerlerini veya xml özelliklerini kullanırken, Visual Studio 'da üzerine giderek, XML değişmez değerlerinin veya özelliklerinin genişletilmiş adını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1268-114">When using XML literals or XML properties that are in globally declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="d1268-115">Genişletilmiş adı bir araç ipucunda görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d1268-115">You will see the expanded name in a tooltip.</span></span>

<span data-ttu-id="d1268-116"><xref:System.Xml.Linq.XNamespace>Yöntemini kullanarak genel bir ad alanına karşılık gelen bir nesnesi alabilirsiniz `GetXmlNamespace` .</span><span class="sxs-lookup"><span data-stu-id="d1268-116">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>

## <a name="example-use-imports-to-declare-a-global-namespace"></a><span data-ttu-id="d1268-117">Örnek: `Imports` genel bir ad alanı bildirmek Için kullanın</span><span class="sxs-lookup"><span data-stu-id="d1268-117">Example: Use `Imports` to declare a global namespace</span></span>

<span data-ttu-id="d1268-118">Aşağıdaki örnek, ifadesiyle bir varsayılan genel ad alanı bildirir `Imports` ve ardından <xref:System.Xml.Linq.XElement> Bu ad alanındaki bir NESNEYI bir XML değişmez değeri ile başlatır:</span><span class="sxs-lookup"><span data-stu-id="d1268-118">The following example declares a default global namespace with the `Imports` statement, and then initializes an <xref:System.Xml.Linq.XElement> object in that namespace with an XML literal:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="d1268-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d1268-119">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a><span data-ttu-id="d1268-120">Örnek: ön eki olan genel bir ad alanı bildirin</span><span class="sxs-lookup"><span data-stu-id="d1268-120">Example: Declare a global namespace that has a prefix</span></span>

<span data-ttu-id="d1268-121">Sonraki örnek, öneki olan bir genel ad alanı bildirir ve bir XML değişmez değeri olan bir öğe başlatır:</span><span class="sxs-lookup"><span data-stu-id="d1268-121">The next example declares a global namespace with a prefix, and initializes an element with an XML literal:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="d1268-122">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d1268-122">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a><span data-ttu-id="d1268-123">Örnek: varsayılan bir ad alanı bildirin ve öğe için gömülü bir ifade kullanın `Child`</span><span class="sxs-lookup"><span data-stu-id="d1268-123">Example: Declare a default namespace and use an embedded expression for the `Child` element</span></span>

<span data-ttu-id="d1268-124">XML değişmez değerlerinde belirtilen ad alanları, gömülü ifadeler içine taşımaz.</span><span class="sxs-lookup"><span data-stu-id="d1268-124">Namespaces that are declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="d1268-125">Aşağıdaki örnek bir varsayılan ad alanı bildirir ve ardından öğesi için gömülü bir ifade kullanır `Child` .</span><span class="sxs-lookup"><span data-stu-id="d1268-125">The following example declares a default namespace, and then uses an embedded expression for the `Child` element.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="d1268-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d1268-126">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

<span data-ttu-id="d1268-127">Elde edilen XML, bir varsayılan ad alanı bildirimi içerir, böylece `Child` öğe ad alanında yer alır.</span><span class="sxs-lookup"><span data-stu-id="d1268-127">The resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>

<span data-ttu-id="d1268-128">Katıştırılmış ifadede aşağıdaki gibi farklı bir ad alanı bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d1268-128">You could declare a different namespace in the embedded expression, as follows:</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="d1268-129">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d1268-129">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

<span data-ttu-id="d1268-130">Ancak, genel varsayılan ad alanı ile, ad alanlarını bildirmeden XML değişmez değerlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1268-130">However, with the global default namespace you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="d1268-131">Elde edilen XML, bu örnekte olduğu gibi, genel olarak belirtilen varsayılan ad alanında olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1268-131">The resulting XML will be in the globally-declared default namespace, as in this example:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="d1268-132">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d1268-132">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a><span data-ttu-id="d1268-133">Örnek: XML özellikleriyle ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="d1268-133">Example: Use namespaces with XML properties</span></span>

<span data-ttu-id="d1268-134">Bir ad alanında olan bir XML ağacıyla çalışıyorsanız ve XML özelliklerini kullanıyorsanız, XML özelliklerinin de doğru ad alanında olması için genel bir ad alanı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1268-134">If you're working with an XML tree that's in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="d1268-135">Aşağıdaki örnek, bir ad alanında bir XML ağacını bildirir ve sonra öğe sayısını yazdırır `Child` .</span><span class="sxs-lookup"><span data-stu-id="d1268-135">The following example declares an XML tree in a namespace, and then prints the count of `Child` elements.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

<span data-ttu-id="d1268-136">Bu örnek, hiçbir öğe olmadığını gösterir `Child` .</span><span class="sxs-lookup"><span data-stu-id="d1268-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="d1268-137">Bu çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d1268-137">It produces this output:</span></span>

```output
0
```

<span data-ttu-id="d1268-138">Ancak, varsayılan bir genel ad alanı bildirirseniz, hem XML değişmez değeri hem de XML özelliği varsayılan genel ad alanında bulunur:</span><span class="sxs-lookup"><span data-stu-id="d1268-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

<span data-ttu-id="d1268-139">Bu örnek, bir öğe olduğunu gösterir `Child` .</span><span class="sxs-lookup"><span data-stu-id="d1268-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="d1268-140">Bu çıktıyı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d1268-140">It produces this output:</span></span>

```output
1
```

<span data-ttu-id="d1268-141">Ön eki olan genel bir ad alanı bildirirseniz, öneki hem XML değişmez değerleri hem de XML özellikleri için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d1268-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a><span data-ttu-id="d1268-142">Örnek: şunu `GetXmlNamespace` almak Için kullanın `XNamespace`</span><span class="sxs-lookup"><span data-stu-id="d1268-142">Example: Use `GetXmlNamespace` to get an `XNamespace`</span></span>

<span data-ttu-id="d1268-143"><xref:System.Xml.Linq.XNamespace>Yöntemini kullanarak bir nesnesi elde edebilirsiniz `GetXmlNamespace` :</span><span class="sxs-lookup"><span data-stu-id="d1268-143">You can obtain an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

<span data-ttu-id="d1268-144">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d1268-144">This example produces the following output:</span></span>

```output
http://www.adventure-works.com
```

## <a name="see-also"></a><span data-ttu-id="d1268-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1268-145">See also</span></span>

- [<span data-ttu-id="d1268-146">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="d1268-146">Namespaces overview</span></span>](namespaces-overview.md)
