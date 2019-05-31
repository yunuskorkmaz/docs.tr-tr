---
title: Genel türler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423390"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="5c9b3-102">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5c9b3-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="5c9b3-103">Genel türler, C# dili ve ortak dil çalışma zamanı (CLR) 2.0 sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="5c9b3-104">Genel türler için .NET Framework tasarım sınıfları ve sınıf ya da yöntem bildirildi ve istemci kodu sayesinde örneği kadar bir veya daha fazla tür belirtimi erteleme yöntemlere mümkün hale tür parametrelerinin kavramı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="5c9b3-105">Örneğin, bir genel tür parametre T kullanarak diğer istemci kodu çalışma zamanı atamaları veya kutulama işlemleri riskini ve maliyet olmaksızın burada gösterildiği gibi kullanabileceğiniz tek bir sınıf yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5c9b3-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

<span data-ttu-id="5c9b3-106">Genel sınıflar ve yöntemler çalışmalarında, tür güvenliği ve verimlilik genel olmayan karşılıkları edilemez bir şekilde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-106">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="5c9b3-107">Genel türler, koleksiyonlar ve bunlar üzerinde çalışan yöntemleri ile sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-107">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="5c9b3-108">.NET Framework sınıf kitaplığı 2.0 sürümünü sağlayan yeni bir ad alanı <xref:System.Collections.Generic>, birkaç yeni genel tabanlı koleksiyon sınıflarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-108">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="5c9b3-109">Tüm .NET Framework 2.0 ve daha sonra kullanmak yeni genel koleksiyon sınıfları yerine eski genel olmayan ortaklarınıza gibi hedefleyen uygulamalar, önerilen <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-109">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="5c9b3-110">Daha fazla bilgi için [.NET içindeki genel türler](../../../standard/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c9b3-110">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="5c9b3-111">Elbette, özel, genel türler de oluşturabilirsiniz ve kendi sağlamak için yöntemleri çözümleri ve tür açısından güvenli ve verimli tasarım desenleri genelleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-111">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="5c9b3-112">Aşağıdaki kod örneği, Tanıtım amaçlı basit bir genel bağlantılı liste sınıfı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-112">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="5c9b3-113">(Çoğu durumda, kullanmanız gereken <xref:System.Collections.Generic.List%601> sınıf kendi oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan.) Tür parametresi `T` çeşitli konumlarda burada somut bir türde normalde kullanılabilir listesinde depolanan öğenin türünü belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-113">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="5c9b3-114">Bu, aşağıdaki şekillerde kullanılır:</span><span class="sxs-lookup"><span data-stu-id="5c9b3-114">It is used in the following ways:</span></span>  
  
- <span data-ttu-id="5c9b3-115">Bir yöntemin parametre türü olarak `AddHead` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-115">As the type of a method parameter in the `AddHead` method.</span></span>  
  
- <span data-ttu-id="5c9b3-116">Dönüş türü olarak `Data` iç içe özellik `Node` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-116">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
- <span data-ttu-id="5c9b3-117">Özel üye türü olarak `data` içinde iç içe geçmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-117">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="5c9b3-118">T için iç içe geçmiş kullanılabilir olduğunu unutmayın `Node` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-118">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="5c9b3-119">Zaman `GenericList<T>` somut bir türde örneğin olarak Örneklendirilmiş bir `GenericList<int>`, her geçtiği `T` ile değiştirilecek `int`.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-119">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 <span data-ttu-id="5c9b3-120">Aşağıdaki kod örneği, istemci kodu Genel nasıl kullandığını gösterir `GenericList<T>` tamsayı listesi oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-120">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="5c9b3-121">Basit tür bağımsız değişkeni değiştirerek aşağıdaki kodu kolayca dizeler veya başka herhangi bir özel tür listesini oluşturmak için değiştirilmesi:</span><span class="sxs-lookup"><span data-stu-id="5c9b3-121">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a><span data-ttu-id="5c9b3-122">Genel türlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="5c9b3-122">Generics Overview</span></span>  
  
- <span data-ttu-id="5c9b3-123">Genel türler, kod yeniden kullanımını, tür güvenliği ve performansı en üst düzeye çıkarmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-123">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
- <span data-ttu-id="5c9b3-124">Genel türlerin yararları en yaygın kullanımı, koleksiyon sınıfları oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-124">The most common use of generics is to create collection classes.</span></span>  
  
- <span data-ttu-id="5c9b3-125">.NET Framework sınıf kitaplığı çeşitli yeni genel koleksiyon sınıflarını içeren <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-125">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="5c9b3-126">Olası yerine gibi sınıfların her durumda bu kullanılmalıdır <xref:System.Collections.ArrayList> içinde <xref:System.Collections> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-126">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
- <span data-ttu-id="5c9b3-127">Kendi genel arabirimler, sınıflar, yöntemler, olaylar ve temsilciler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-127">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
- <span data-ttu-id="5c9b3-128">Genel sınıflar, yöntemler belirli veri türlerinde erişimi etkinleştirmek için kısıtlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-128">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
- <span data-ttu-id="5c9b3-129">Genel veri türü kullanılan türleri hakkında bilgi çalışma zamanında yansıma kullanarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-129">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5c9b3-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5c9b3-130">Related Sections</span></span>  
 <span data-ttu-id="5c9b3-131">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="5c9b3-131">For more information:</span></span>  
  
- [<span data-ttu-id="5c9b3-132">Genel Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="5c9b3-132">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [<span data-ttu-id="5c9b3-133">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="5c9b3-133">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [<span data-ttu-id="5c9b3-134">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="5c9b3-134">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [<span data-ttu-id="5c9b3-135">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="5c9b3-135">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [<span data-ttu-id="5c9b3-136">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c9b3-136">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [<span data-ttu-id="5c9b3-137">Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="5c9b3-137">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [<span data-ttu-id="5c9b3-138">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="5c9b3-138">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [<span data-ttu-id="5c9b3-139">Genel Türler ve Yansıma</span><span class="sxs-lookup"><span data-stu-id="5c9b3-139">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [<span data-ttu-id="5c9b3-140">Çalışma Zamanındaki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="5c9b3-140">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5c9b3-141">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5c9b3-141">C# Language Specification</span></span>  
 <span data-ttu-id="5c9b3-142">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="5c9b3-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9b3-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c9b3-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="5c9b3-144">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5c9b3-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5c9b3-145">Türler</span><span class="sxs-lookup"><span data-stu-id="5c9b3-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="5c9b3-146">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="5c9b3-146">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [<span data-ttu-id="5c9b3-147">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="5c9b3-147">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [<span data-ttu-id="5c9b3-148">.NET içindeki genel türler</span><span class="sxs-lookup"><span data-stu-id="5c9b3-148">Generics in .NET</span></span>](../../../standard/generics/index.md)
