---
title: "Genel ad alanları (Visual Basic) (LINQ-XML) ile çalışma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 376a6d2dfbca22fb8efc6395f478839d716e14d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="62bfb-102">Genel ad alanları (Visual Basic) (LINQ-XML) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="62bfb-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="62bfb-103">Visual Basic'de XML değişmez değerleri önemli özelliklerinden biridir kullanarak XML ad alanlarını bildirme yeteneği `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="62bfb-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="62bfb-104">Bu özelliği kullanarak, bir önek kullanan bir XML ad alanı bildirimini veya varsayılan bir XML ad alanı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="62bfb-105">Bu özellik, iki durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="62bfb-105">This capability is useful in two situations.</span></span> <span data-ttu-id="62bfb-106">İlk olarak, XML değişmez değerlerine bildirilen ad alanları katıştırılmış ifadeler taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="62bfb-107">Genel ad alanlarını bildirme katıştırılmış ifadeler ad alanları ile kullanmak için yapmanız gereken iş miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="62bfb-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="62bfb-108">İkinci olarak, ad alanları ile XML özellikleri kullanmak için genel ad alanları bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="62bfb-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="62bfb-109">Proje düzeyinde genel ad alanları bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="62bfb-110">Proje düzeyi genel ad alanları geçersiz kılmaları modülü düzeyinde genel ad alanlarını da bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="62bfb-111">Son olarak, bir XML değişmez değer genel ad alanları geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="62bfb-112">XML değişmez değerleri veya genel olarak bildirilen ad alanlarında XML özellikleri kullandığınızda, Visual Studio'da üzerine gelerek genişletilmiş adı XML değişmez değerleri veya özellikler görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="62bfb-113">Genişletilmiş ad, bir araç ipucunda görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="62bfb-114">Alabileceğiniz bir <xref:System.Xml.Linq.XNamespace> kullanarak genel ad alanı için karşılık gelen nesne `GetXmlNamespace` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="62bfb-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="62bfb-115">Genel ad alanları örnekleri</span><span class="sxs-lookup"><span data-stu-id="62bfb-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="62bfb-116">Kullanarak aşağıdaki örnekte bir varsayılan genel ad alanı bildirir `Imports` deyimi ve başlatmak için bir XML değişmez değer kullanan bir <xref:System.Xml.Linq.XElement> ad nesnesinde:</span><span class="sxs-lookup"><span data-stu-id="62bfb-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="62bfb-117">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="62bfb-118">Aşağıdaki örnek, genel bir ad alanı öneki bildirir ve bir öğeyi başlatmak için bir XML değişmez değer kullanır:</span><span class="sxs-lookup"><span data-stu-id="62bfb-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="62bfb-119">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="62bfb-120">Genel ad alanları ve katıştırılmış ifadeler</span><span class="sxs-lookup"><span data-stu-id="62bfb-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="62bfb-121">XML değişmez değerlerine bildirilen ad alanları katıştırılmış ifadeler taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="62bfb-122">Aşağıdaki örnek, bir varsayılan ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="62bfb-122">The following example declares a default namespace.</span></span> <span data-ttu-id="62bfb-123">Katıştırılmış bir ifadenin ardından kullanan `Child` öğesi.</span><span class="sxs-lookup"><span data-stu-id="62bfb-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="62bfb-124">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="62bfb-125">Gördüğünüz gibi sonuç XML bir varsayılan ad alanı bildirimini içerir. böylece `Child` hiçbir ad alanında bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="62bfb-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="62bfb-126">Ad alanı katıştırılmış ifadede, aşağıdaki gibi yeniden bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="62bfb-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="62bfb-127">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="62bfb-128">Ancak, daha iyi bir yaklaşım genel varsayılan ad alanı kullanmak üzere daha kullanışsız budur.</span><span class="sxs-lookup"><span data-stu-id="62bfb-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="62bfb-129">Genel varsayılan ad alanı ile ad alanlarını bildirme olmadan XML değişmez değerleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="62bfb-130">Sonuçta elde edilen XML varsayılan genel olarak bildirilen ad alanında olacaktır.</span><span class="sxs-lookup"><span data-stu-id="62bfb-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
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
  
 <span data-ttu-id="62bfb-131">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="62bfb-132">XML özellikleri ile ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="62bfb-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="62bfb-133">XML özellikleri de doğru ad alanında olması bir ad alanı içinde bir XML ağacı çalıştığınız ve XML özellikleri kullanırsanız, genel ad alanı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62bfb-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="62bfb-134">Aşağıdaki örnek, bir XML ad alanı ağacında bildirir.</span><span class="sxs-lookup"><span data-stu-id="62bfb-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="62bfb-135">Ardından sayısını yazdırır `Child` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="62bfb-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="62bfb-136">Bu örnek olduğunu gösteren hiçbir `Child` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="62bfb-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="62bfb-137">Şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-137">It produces the following output:</span></span>  
  
```  
0  
```  
  
 <span data-ttu-id="62bfb-138">Ardından ancak, varsayılan genel ad alanı bildirirseniz değişmez değer XML ve XML özelliği varsayılan genel ad alanında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="62bfb-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
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
  
 <span data-ttu-id="62bfb-139">Bu örnek bir tane olduğunu gösteren `Child` öğesi.</span><span class="sxs-lookup"><span data-stu-id="62bfb-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="62bfb-140">Şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-140">It produces the following output:</span></span>  
  
```  
1  
```  
  
 <span data-ttu-id="62bfb-141">Bir ön ekine sahip genel bir ad alanı bildirirseniz XML değişmez değerleri ve XML özellikleri için önek kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="62bfb-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
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
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="62bfb-142">XNamespace ve genel ad alanları</span><span class="sxs-lookup"><span data-stu-id="62bfb-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="62bfb-143">Alabileceğiniz bir <xref:System.Xml.Linq.XNamespace> kullanarak nesne `GetXmlNamespace` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="62bfb-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
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
  
 <span data-ttu-id="62bfb-144">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62bfb-144">This example produces the following output:</span></span>  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="62bfb-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62bfb-145">See Also</span></span>  
 [<span data-ttu-id="62bfb-146">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="62bfb-146">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
