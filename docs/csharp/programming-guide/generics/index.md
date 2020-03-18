---
title: Jenerikler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167499"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="b1e64-102">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b1e64-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="b1e64-103">Jenerikler, bir veya daha fazla türünün belirtimini, sınıf veya yöntem istemci kodu tarafından bildirilene ve anında yapılana kadar erteleyen sınıflar ve yöntemler tasarlamayı mümkün kılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1e64-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="b1e64-104">Örneğin, genel bir tür parametresi `T`kullanarak, burada gösterildiği gibi, diğer istemci kodunun çalışma zamanı dökümleri veya kutulama işlemleri maliyetini veya riskine maruz kalmadan kullanabileceği tek bir sınıf yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b1e64-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="b1e64-105">Genel sınıflar ve yöntemler yeniden kullanılabilirliği, tür güvenliğini ve verimliliği, genel olmayan karşılıklarının yapamayacağı şekilde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b1e64-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="b1e64-106">Jenerikler en sık koleksiyonlar ve bunlar üzerinde çalışan yöntemlerle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1e64-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="b1e64-107">Ad <xref:System.Collections.Generic> alanı birkaç genel tabanlı koleksiyon sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="b1e64-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="b1e64-108">Genel olmayan koleksiyonlar, örneğin <xref:System.Collections.ArrayList> önerilmez ve uyumluluk amacıyla korunur.</span><span class="sxs-lookup"><span data-stu-id="b1e64-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="b1e64-109">Daha fazla bilgi için [.NET'teki Jenerik'e](../../../standard/generics/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b1e64-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="b1e64-110">Tabii ki, aynı zamanda kendi genelleştirilmiş çözümler ve tür güvenli ve verimli tasarım desenleri sağlamak için özel genel türleri ve yöntemleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1e64-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="b1e64-111">Aşağıdaki kod örneği, gösteri amacıyla basit bir genel bağlantılı liste sınıfını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1e64-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="b1e64-112">(Çoğu durumda, kendi kitabınızı oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan <xref:System.Collections.Generic.List%601> sınıfı kullanmanız gerekir.) Tür parametresi, `T` listede depolanan maddenin türünü belirtmek için normalde somut bir türün kullanılacağı çeşitli konumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1e64-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="b1e64-113">Aşağıdaki şekillerde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b1e64-113">It is used in the following ways:</span></span>

- <span data-ttu-id="b1e64-114">`AddHead` Yöntemde yöntem parametresi türü olarak.</span><span class="sxs-lookup"><span data-stu-id="b1e64-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="b1e64-115">İç içe sınıftaki `Data` `Node` özelliğin dönüş türü olarak.</span><span class="sxs-lookup"><span data-stu-id="b1e64-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="b1e64-116">İç içe sınıftaki `data` özel üyenin türü olarak.</span><span class="sxs-lookup"><span data-stu-id="b1e64-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="b1e64-117">İç `T` içe sınıf `Node` için kullanılabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b1e64-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="b1e64-118">Bir `GenericList<T>` beton türü ile instantiated olduğunda, `GenericList<int>`örneğin bir `T` , her `int`olay ile değiştirilecektir .</span><span class="sxs-lookup"><span data-stu-id="b1e64-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="b1e64-119">Aşağıdaki kod örneği, istemci kodunun `GenericList<T>` tamsayılar listesi oluşturmak için genel sınıfı nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1e64-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="b1e64-120">Yalnızca tür bağımsız değişkenini değiştirerek, aşağıdaki kod dizeleri veya başka bir özel tür listeleri oluşturmak için kolayca değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="b1e64-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="b1e64-121">Genel genel bakış</span><span class="sxs-lookup"><span data-stu-id="b1e64-121">Generics overview</span></span>

- <span data-ttu-id="b1e64-122">Kodun yeniden kullanımını, tür güvenliğini ve performansı en üst düzeye çıkarmak için genel türleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1e64-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="b1e64-123">Generics en yaygın kullanımı toplama sınıfları oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="b1e64-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="b1e64-124">.NET Framework sınıf kitaplığı <xref:System.Collections.Generic> ad alanında birkaç yeni genel koleksiyon sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="b1e64-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="b1e64-125">Bunlar, ad alanı gibi <xref:System.Collections.ArrayList> sınıflar yerine mümkün olduğunda kullanılmalıdır. <xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="b1e64-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="b1e64-126">Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, etkinliklerinizi ve temsilcilerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1e64-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="b1e64-127">Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b1e64-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="b1e64-128">Genel bir veri türünde kullanılan türler hakkındaki bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b1e64-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b1e64-129">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="b1e64-129">Related sections</span></span>

- [<span data-ttu-id="b1e64-130">Genel Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="b1e64-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="b1e64-131">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="b1e64-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="b1e64-132">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="b1e64-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="b1e64-133">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="b1e64-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="b1e64-134">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b1e64-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="b1e64-135">Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="b1e64-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="b1e64-136">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="b1e64-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="b1e64-137">Genel Türler ve Yansıma</span><span class="sxs-lookup"><span data-stu-id="b1e64-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="b1e64-138">Çalışma Zamanındaki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b1e64-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="b1e64-139">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b1e64-139">C# language specification</span></span>

<span data-ttu-id="b1e64-140">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="b1e64-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1e64-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1e64-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b1e64-142">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b1e64-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b1e64-143">Türler</span><span class="sxs-lookup"><span data-stu-id="b1e64-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="b1e64-144">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="b1e64-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="b1e64-145">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="b1e64-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="b1e64-146">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="b1e64-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
