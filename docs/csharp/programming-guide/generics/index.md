---
title: Genel türler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 7d212aeaa7d7a8c3f152f8610a7ef3fe5de0fe23
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589597"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="6ea81-102">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6ea81-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="6ea81-103">C# Dil sürüm 2,0 ve ortak dil çalışma zamanı (CLR) için genel türler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ea81-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="6ea81-104">Genel türler, sınıf veya yöntem istemci kodu tarafından bildirilene ve örneklendirilene kadar bir veya daha fazla türün belirtimini erteleme sınıfları ve yöntemleri tasarlamayı sağlayan tür parametrelerinin kavramının .NET Framework sunar.</span><span class="sxs-lookup"><span data-stu-id="6ea81-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="6ea81-105">Örneğin, bir genel tür parametresi kullanarak, diğer istemci kodunun, çalışma zamanı yayınları veya paketleme işlemlerinin maliyetini veya riskini aşmadan kullanabileceği tek bir sınıf yazabilirsiniz, burada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="6ea81-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="6ea81-106">Genel sınıflar ve Yöntemler, yeniden kullanılabilirliği birleştirir, güvenlik ve verimliliği genel olmayan karşılıklarına göre bir şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="6ea81-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="6ea81-107">Genel türler, koleksiyonlarla ve bunlarla çalışan yöntemlerle en sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6ea81-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="6ea81-108">.NET Framework sınıf kitaplığının 2,0 sürümü, birkaç yeni genel tabanlı koleksiyon sınıfı <xref:System.Collections.Generic>içeren yeni bir ad alanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ea81-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="6ea81-109">.NET Framework 2,0 ve üstünü hedefleyen tüm uygulamaların, gibi eski genel olmayan karşılıkları <xref:System.Collections.ArrayList>yerine yeni genel koleksiyon sınıflarını kullanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="6ea81-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="6ea81-110">Daha fazla bilgi için bkz. [.net 'Teki genel türler](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="6ea81-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="6ea81-111">Kuşkusuz, özel genel türler ve Yöntemler oluşturarak tür açısından güvenli ve verimli bir şekilde kendi Genelleştirilmiş çözümlerinizi ve tasarım düzenlerini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ea81-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="6ea81-112">Aşağıdaki kod örneğinde, tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ea81-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="6ea81-113">(Çoğu durumda, kendi örneğini oluşturmak yerine .NET Framework <xref:System.Collections.Generic.List%601> sınıf kitaplığı tarafından sunulan sınıfı kullanmanız gerekir.) Tür parametresi `T` , somut bir türün listede depolanan öğenin türünü belirtmek için normalde kullanıldığı çeşitli konumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6ea81-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="6ea81-114">Aşağıdaki yollarla kullanılır:</span><span class="sxs-lookup"><span data-stu-id="6ea81-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="6ea81-115">`AddHead` Yöntem içindeki yöntem parametresinin türü olarak.</span><span class="sxs-lookup"><span data-stu-id="6ea81-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="6ea81-116">İç içe yerleştirilmiş `Data` `Node` sınıftaki özelliğinin dönüş türü olarak.</span><span class="sxs-lookup"><span data-stu-id="6ea81-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="6ea81-117">İç içe yerleştirilmiş sınıftaki özel üyenin `data` türü olarak.</span><span class="sxs-lookup"><span data-stu-id="6ea81-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="6ea81-118">Bu T 'in iç içe yerleştirilmiş `Node` sınıf için kullanılabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6ea81-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="6ea81-119">, Örneğin, bir `GenericList<int>`somut tür ile örneği oluşturulduğunda, öğesinin `T` her oluşumu ile `int`yerine kullanılır. `GenericList<T>`</span><span class="sxs-lookup"><span data-stu-id="6ea81-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="6ea81-120">Aşağıdaki kod örneği, istemci kodunun tamsayılar listesini oluşturmak için genel `GenericList<T>` sınıfı nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ea81-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="6ea81-121">Yalnızca tür bağımsız değişkenini değiştirerek aşağıdaki kod, dizelerin veya diğer özel türün listesini oluşturmak için kolayca değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="6ea81-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="6ea81-122">Genel bakışa genel bakış</span><span class="sxs-lookup"><span data-stu-id="6ea81-122">Generics Overview</span></span>  
  
- <span data-ttu-id="6ea81-123">Kod yeniden kullanımını en üst düzeye çıkarmak için genel türleri kullanın, güvenlik ve performans yazın.</span><span class="sxs-lookup"><span data-stu-id="6ea81-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="6ea81-124">Genel türlerin en yaygın kullanımı koleksiyon sınıfları oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6ea81-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="6ea81-125">.NET Framework sınıf kitaplığı, <xref:System.Collections.Generic> ad alanında birkaç yeni genel koleksiyon sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="6ea81-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="6ea81-126">Bunlar, <xref:System.Collections.ArrayList> <xref:System.Collections> ad alanı gibi sınıflar yerine mümkün olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ea81-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="6ea81-127">Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, olayları ve temsilcilerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ea81-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="6ea81-128">Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6ea81-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="6ea81-129">Genel veri türünde kullanılan türlerle ilgili bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="6ea81-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6ea81-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6ea81-130">Related Sections</span></span>  
 <span data-ttu-id="6ea81-131">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="6ea81-131">For more information:</span></span>  
  
- [<span data-ttu-id="6ea81-132">Genel Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="6ea81-132">Generic Type Parameters</span></span>](./generic-type-parameters.md)  
  
- [<span data-ttu-id="6ea81-133">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="6ea81-133">Constraints on Type Parameters</span></span>](./constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="6ea81-134">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="6ea81-134">Generic Classes</span></span>](./generic-classes.md)  
  
- [<span data-ttu-id="6ea81-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="6ea81-135">Generic Interfaces</span></span>](./generic-interfaces.md)  
  
- [<span data-ttu-id="6ea81-136">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6ea81-136">Generic Methods</span></span>](./generic-methods.md)  
  
- [<span data-ttu-id="6ea81-137">Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="6ea81-137">Generic Delegates</span></span>](./generic-delegates.md)  
  
- [<span data-ttu-id="6ea81-138">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="6ea81-138">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="6ea81-139">Genel Türler ve Yansıma</span><span class="sxs-lookup"><span data-stu-id="6ea81-139">Generics and Reflection</span></span>](./generics-and-reflection.md)  
  
- [<span data-ttu-id="6ea81-140">Çalışma Zamanındaki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="6ea81-140">Generics in the Run Time</span></span>](./generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6ea81-141">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6ea81-141">C# Language Specification</span></span>  
 <span data-ttu-id="6ea81-142">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="6ea81-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea81-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ea81-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="6ea81-144">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6ea81-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6ea81-145">Türler</span><span class="sxs-lookup"><span data-stu-id="6ea81-145">Types</span></span>](../types/index.md)
- [<span data-ttu-id="6ea81-146">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="6ea81-146">\<typeparam></span></span>](../xmldoc/typeparam.md)
- [<span data-ttu-id="6ea81-147">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="6ea81-147">\<typeparamref></span></span>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="6ea81-148">.NET 'teki genel türler</span><span class="sxs-lookup"><span data-stu-id="6ea81-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
