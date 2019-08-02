---
title: Genel ad alanları (Visual Basic) ile çalışma (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 9aab6f7175c905fcb3e82829f131f52b3d9368ac
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710379"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="aa2a8-102">Genel ad alanları (Visual Basic) ile çalışma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="aa2a8-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="aa2a8-103">Visual Basic xml sabit değerlerinin temel özelliklerinden biri, `Imports` ifadesini kullanarak XML ad alanları bildirme yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="aa2a8-104">Bu özelliği kullanarak, ön ek kullanan bir XML ad alanı bildirebilir veya varsayılan bir XML ad alanı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="aa2a8-105">Bu özellik iki durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-105">This capability is useful in two situations.</span></span> <span data-ttu-id="aa2a8-106">İlk olarak, XML değişmez değerlerinde belirtilen ad alanları, katıştırılmış ifadeler içine taşımaz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="aa2a8-107">Genel ad alanlarını bildirmek, katıştırılmış ifadeleri ad alanlarıyla birlikte kullanmak için yapmanız gereken iş miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="aa2a8-108">İkincisi, XML özellikleriyle ad alanlarını kullanabilmeniz için genel ad alanlarını bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="aa2a8-109">Genel ad alanlarını proje düzeyinde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="aa2a8-110">Genel ad alanlarını modül düzeyinde bildirebilirsiniz ve bu da proje düzeyi genel ad alanlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="aa2a8-111">Son olarak, bir XML sabit değerinde genel ad alanlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="aa2a8-112">Genel olarak tanımlanmış ad alanlarında bulunan XML değişmez değerlerini veya xml özelliklerini kullanırken, Visual Studio 'da üzerine giderek, XML değişmez değerlerinin veya özelliklerinin genişletilmiş adını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="aa2a8-113">Genişletilmiş adı bir araç ipucunda görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="aa2a8-114">Yöntemini kullanarak genel bir <xref:System.Xml.Linq.XNamespace> ad alanına karşılık gelen bir nesnesi alabilirsiniz. `GetXmlNamespace`</span><span class="sxs-lookup"><span data-stu-id="aa2a8-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="aa2a8-115">Genel ad alanı örnekleri</span><span class="sxs-lookup"><span data-stu-id="aa2a8-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="aa2a8-116">Aşağıdaki örnek, bir varsayılan genel ad alanını `Imports` bildirimini kullanarak bildirir ve sonra bu ad alanındaki bir <xref:System.Xml.Linq.XElement> nesneyi başlatmak için bir XML değişmez değeri kullanır:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="aa2a8-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="aa2a8-118">Aşağıdaki örnek bir ön eki olan genel bir ad alanı bildirir ve sonra bir öğeyi başlatmak için bir XML değişmez değeri kullanır:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="aa2a8-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="aa2a8-120">Genel ad alanları ve katıştırılmış Ifadeler</span><span class="sxs-lookup"><span data-stu-id="aa2a8-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="aa2a8-121">XML değişmez değerlerinde belirtilen ad alanları, gömülü ifadeler içine taşımaz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="aa2a8-122">Aşağıdaki örnek bir varsayılan ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-122">The following example declares a default namespace.</span></span> <span data-ttu-id="aa2a8-123">Daha sonra `Child` öğesi için gömülü bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="aa2a8-124">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="aa2a8-125">Gördüğünüz gibi, elde edilen XML, bir varsayılan ad alanı bildirimi içerir, böylece `Child` öğe ad alanı içermez.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="aa2a8-126">Ad alanını katıştırılmış ifadede aşağıdaki gibi yeniden bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="aa2a8-127">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="aa2a8-128">Ancak bu, daha iyi bir yaklaşım olan genel varsayılan ad alanından kullanılmak üzere daha kısaberdır.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="aa2a8-129">Genel varsayılan ad alanı ile, XML değişmez değerlerini ad alanları bildirmeden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="aa2a8-130">Elde edilen XML, genel olarak belirtilen varsayılan ad alanında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="aa2a8-131">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="aa2a8-132">XML özellikleriyle ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="aa2a8-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="aa2a8-133">Bir ad alanında olan bir XML ağacıyla çalışıyorsanız ve XML özelliklerini kullanıyorsanız, XML özelliklerinin de doğru ad alanında olması için genel bir ad alanı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="aa2a8-134">Aşağıdaki örnek, bir ad alanında bir XML ağacını bildirir.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="aa2a8-135">Daha sonra `Child` öğe sayısını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="aa2a8-136">Bu örnek, hiçbir `Child` öğe olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="aa2a8-137">Aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="aa2a8-138">Ancak, varsayılan bir genel ad alanı bildirirseniz, hem XML değişmez değeri hem de XML özelliği varsayılan genel ad alanında bulunur:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="aa2a8-139">Bu örnek, bir `Child` öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="aa2a8-140">Aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="aa2a8-141">Ön eki olan genel bir ad alanı bildirirseniz, öneki hem XML değişmez değerleri hem de XML özellikleri için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="aa2a8-142">XNamespace ve Global ad alanları</span><span class="sxs-lookup"><span data-stu-id="aa2a8-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="aa2a8-143">Yöntemini kullanarak bir <xref:System.Xml.Linq.XNamespace> nesnesi edinebilirsiniz: `GetXmlNamespace`</span><span class="sxs-lookup"><span data-stu-id="aa2a8-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="aa2a8-144">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="aa2a8-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa2a8-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa2a8-145">See also</span></span>

- [<span data-ttu-id="aa2a8-146">Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa2a8-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
