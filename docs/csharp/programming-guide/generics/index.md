---
title: Genel türler-C# Programlama Kılavuzu
description: Genel türler hakkında bilgi edinin. Genel türler kod yeniden kullanımını, tür güvenliğini ve performansı en üst düzeye çıkarır ve genellikle koleksiyon sınıfları oluşturmak için kullanılır.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: beef9c20e3ac62505bc7a4584b404637935de1dc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299402"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="71e44-104">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="71e44-104">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="71e44-105">Genel türler, sınıf veya yöntem istemci kodu tarafından bildirilene ve örneklendirilene kadar bir veya daha fazla türün belirtimini erteleme sınıfları ve yöntemleri tasarlamayı sağlayan .NET 'e parametre türü kavramını getirir.</span><span class="sxs-lookup"><span data-stu-id="71e44-105">Generics introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="71e44-106">Örneğin, genel bir tür parametresi kullanarak `T` , burada gösterildiği gibi, diğer istemci kodunun, çalışma zamanı yayınları veya paketleme işlemlerinin maliyetini veya riskini ortadan kaldırarak kullanabileceği tek bir sınıf yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="71e44-106">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="71e44-107">Genel sınıflar ve Yöntemler, yeniden kullanılabilirlik, tür güvenliği ve verimliliği genel olmayan karşılıklarının bir şekilde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="71e44-107">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="71e44-108">Genel türler, koleksiyonlarla ve bunlarla çalışan yöntemlerle en sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71e44-108">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="71e44-109"><xref:System.Collections.Generic>Ad alanı, birkaç genel tabanlı koleksiyon sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="71e44-109">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="71e44-110">Genel olmayan koleksiyonlar, gibi <xref:System.Collections.ArrayList> önerilmez ve uyumluluk amacıyla korunur.</span><span class="sxs-lookup"><span data-stu-id="71e44-110">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="71e44-111">Daha fazla bilgi için bkz. [.net 'Teki genel türler](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="71e44-111">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="71e44-112">Kuşkusuz, özel genel türler ve Yöntemler oluşturarak tür açısından güvenli ve verimli bir şekilde kendi Genelleştirilmiş çözümlerinizi ve tasarım düzenlerini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e44-112">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="71e44-113">Aşağıdaki kod örneğinde, tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71e44-113">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="71e44-114">(Çoğu durumda, <xref:System.Collections.Generic.List%601> kendinizinkini oluşturmak yerine .NET tarafından sunulan sınıfı kullanmanız gerekir.) Tür parametresi, `T` somut bir türün listede depolanan öğenin türünü belirtmek için normalde kullanıldığı çeşitli konumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71e44-114">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by .NET instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="71e44-115">Aşağıdaki yollarla kullanılır:</span><span class="sxs-lookup"><span data-stu-id="71e44-115">It is used in the following ways:</span></span>

- <span data-ttu-id="71e44-116">Yöntem içindeki yöntem parametresinin türü olarak `AddHead` .</span><span class="sxs-lookup"><span data-stu-id="71e44-116">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="71e44-117">`Data`İç içe yerleştirilmiş sınıftaki özelliğinin dönüş türü olarak `Node` .</span><span class="sxs-lookup"><span data-stu-id="71e44-117">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="71e44-118">`data`İç içe yerleştirilmiş sınıftaki özel üyenin türü olarak.</span><span class="sxs-lookup"><span data-stu-id="71e44-118">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="71e44-119">`T`İç içe yerleştirilmiş sınıf için kullanılabilir olduğunu unutmayın `Node` .</span><span class="sxs-lookup"><span data-stu-id="71e44-119">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="71e44-120">, `GenericList<T>` Örneğin, bir somut tür ile örneği oluşturulduğunda, `GenericList<int>` öğesinin her oluşumu `T` ile yerine kullanılır `int` .</span><span class="sxs-lookup"><span data-stu-id="71e44-120">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="71e44-121">Aşağıdaki kod örneği, istemci kodunun `GenericList<T>` tamsayılar listesini oluşturmak için genel sınıfı nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="71e44-121">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="71e44-122">Yalnızca tür bağımsız değişkenini değiştirerek aşağıdaki kod, dizelerin veya diğer özel türün listesini oluşturmak için kolayca değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="71e44-122">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="71e44-123">Genel bakışa genel bakış</span><span class="sxs-lookup"><span data-stu-id="71e44-123">Generics overview</span></span>

- <span data-ttu-id="71e44-124">Kod yeniden kullanımını en üst düzeye çıkarmak için genel türleri kullanın, güvenlik ve performans yazın.</span><span class="sxs-lookup"><span data-stu-id="71e44-124">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="71e44-125">Genel türlerin en yaygın kullanımı koleksiyon sınıfları oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="71e44-125">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="71e44-126">.NET sınıf kitaplığı, ad alanındaki çeşitli genel koleksiyon sınıflarını içerir <xref:System.Collections.Generic> .</span><span class="sxs-lookup"><span data-stu-id="71e44-126">The .NET class library contains several generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="71e44-127">Bunlar <xref:System.Collections.ArrayList> , ad alanı gibi sınıflar yerine mümkün olduğunda kullanılmalıdır <xref:System.Collections> .</span><span class="sxs-lookup"><span data-stu-id="71e44-127">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="71e44-128">Kendi genel arabirimlerinizi, sınıflarınızı, yöntemlerinizi, olaylarınızı ve temsilcilerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71e44-128">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="71e44-129">Genel sınıflar, belirli veri türlerindeki yöntemlere erişimi etkinleştirmek için kısıtlanabilir.</span><span class="sxs-lookup"><span data-stu-id="71e44-129">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="71e44-130">Genel veri türünde kullanılan türlerle ilgili bilgiler, yansıma kullanılarak çalışma zamanında elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="71e44-130">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="71e44-131">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="71e44-131">Related sections</span></span>

- [<span data-ttu-id="71e44-132">Genel Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="71e44-132">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="71e44-133">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="71e44-133">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="71e44-134">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="71e44-134">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="71e44-135">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="71e44-135">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="71e44-136">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71e44-136">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="71e44-137">Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="71e44-137">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="71e44-138">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="71e44-138">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="71e44-139">Genel Türler ve Yansıma</span><span class="sxs-lookup"><span data-stu-id="71e44-139">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="71e44-140">Çalışma Zamanındaki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="71e44-140">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="71e44-141">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="71e44-141">C# language specification</span></span>

<span data-ttu-id="71e44-142">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="71e44-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="71e44-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71e44-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="71e44-144">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="71e44-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="71e44-145">Türler</span><span class="sxs-lookup"><span data-stu-id="71e44-145">Types</span></span>](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="71e44-146">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="71e44-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
