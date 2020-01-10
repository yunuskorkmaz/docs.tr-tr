---
title: Genel türler C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 330aa74538ab15d1de19d80b0f57b3d0921c5c55
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712162"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="854de-102">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="854de-102">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="854de-103">Genel türler, sınıf veya yöntem istemci kodu tarafından bildirilene ve örneklendirilene kadar bir veya daha fazla türün belirtimini erteleme sınıfları ve yöntemleri tasarlamak için .NET Framework parametre türü kavramını ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="854de-103">Generics introduce the concept of type parameters to the .NET Framework, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="854de-104">Örneğin, bir genel tür parametresi kullanarak `T`, diğer istemci kodunun, çalışma zamanı yayınları veya paketleme işlemlerinin maliyetini ya da riskini göstermeden, burada gösterildiği gibi, kullanabileceği tek bir sınıf yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="854de-104">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="854de-105">Genel sınıflar ve Yöntemler, yeniden kullanılabilirlik, tür güvenliği ve verimliliği genel olmayan karşılıklarının bir şekilde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="854de-105">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="854de-106">Genel türler, koleksiyonlarla ve bunlarla çalışan yöntemlerle en sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="854de-106">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="854de-107"><xref:System.Collections.Generic> ad alanı, genel tabanlı birkaç koleksiyon sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="854de-107">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="854de-108"><xref:System.Collections.ArrayList> gibi genel olmayan koleksiyonlar önerilmez ve uyumluluk amacıyla korunur.</span><span class="sxs-lookup"><span data-stu-id="854de-108">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="854de-109">Daha fazla bilgi için bkz. [.net 'Teki genel türler](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="854de-109">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="854de-110">Kuşkusuz, özel genel türler ve Yöntemler oluşturarak tür açısından güvenli ve verimli bir şekilde kendi Genelleştirilmiş çözümlerinizi ve tasarım düzenlerini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="854de-110">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="854de-111">Aşağıdaki kod örneğinde, tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="854de-111">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="854de-112">(Çoğu durumda, kendinizinkini oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sunulan <xref:System.Collections.Generic.List%601> sınıfını kullanmanız gerekir.) Tür parametresi `T`, somut bir türün genellikle listede depolanan öğenin türünü belirtmek için kullanıldığı çeşitli konumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="854de-112">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="854de-113">Aşağıdaki yollarla kullanılır:</span><span class="sxs-lookup"><span data-stu-id="854de-113">It is used in the following ways:</span></span>

- <span data-ttu-id="854de-114">`AddHead` yönteminde bir yöntem parametresinin türü olarak.</span><span class="sxs-lookup"><span data-stu-id="854de-114">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="854de-115">İç içe `Node` sınıfındaki `Data` özelliğinin dönüş türü olarak.</span><span class="sxs-lookup"><span data-stu-id="854de-115">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="854de-116">Özel üyenin türü, iç içe yerleştirilmiş sınıfta `data`.</span><span class="sxs-lookup"><span data-stu-id="854de-116">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="854de-117">`T` iç içe `Node` sınıfı için kullanılabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="854de-117">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="854de-118">`GenericList<T>`, `GenericList<int>`gibi somut bir türle başlatıldığında `T` her oluşumu `int`ile yerine geçer.</span><span class="sxs-lookup"><span data-stu-id="854de-118">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)] 

<span data-ttu-id="854de-119">Aşağıdaki kod örneği, istemci kodunun tamsayılar listesini oluşturmak için genel `GenericList<T>` sınıfını nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="854de-119">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="854de-120">Yalnızca tür bağımsız değişkenini değiştirerek aşağıdaki kod, dizelerin veya diğer özel türün listesini oluşturmak için kolayca değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="854de-120">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="854de-121">Genel bakışa genel bakış</span><span class="sxs-lookup"><span data-stu-id="854de-121">Generics overview</span></span>

- <span data-ttu-id="854de-122">Kod yeniden kullanımını en üst düzeye çıkarmak için genel türleri kullanın, güvenlik ve performans yazın.</span><span class="sxs-lookup"><span data-stu-id="854de-122">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="854de-123">Genel türlerin en yaygın kullanımı koleksiyon sınıfları oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="854de-123">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="854de-124">.NET Framework sınıf kitaplığı, <xref:System.Collections.Generic> ad alanında birkaç yeni genel koleksiyon sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="854de-124">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="854de-125">Bunlar, <xref:System.Collections> ad alanındaki <xref:System.Collections.ArrayList> gibi sınıflar yerine mümkün olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="854de-125">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="854de-126">Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, olaylarınızı ve temsilcilerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="854de-126">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="854de-127">Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.</span><span class="sxs-lookup"><span data-stu-id="854de-127">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="854de-128">Genel veri türünde kullanılan türlerle ilgili bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="854de-128">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="854de-129">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="854de-129">Related sections</span></span>

- [<span data-ttu-id="854de-130">Genel Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="854de-130">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="854de-131">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="854de-131">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="854de-132">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="854de-132">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="854de-133">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="854de-133">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="854de-134">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="854de-134">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="854de-135">Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="854de-135">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="854de-136">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="854de-136">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="854de-137">Genel Türler ve Yansıma</span><span class="sxs-lookup"><span data-stu-id="854de-137">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="854de-138">Çalışma Zamanındaki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="854de-138">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="854de-139">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="854de-139">C# language specification</span></span>

<span data-ttu-id="854de-140">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="854de-140">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="854de-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="854de-141">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="854de-142">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="854de-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="854de-143">Türler</span><span class="sxs-lookup"><span data-stu-id="854de-143">Types</span></span>](../types/index.md)
- [<span data-ttu-id="854de-144">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="854de-144">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="854de-145">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="854de-145">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="854de-146">.NET 'teki genel türler</span><span class="sxs-lookup"><span data-stu-id="854de-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
