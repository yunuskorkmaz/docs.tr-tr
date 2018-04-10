---
title: Genel Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0804ca0fcefcc53e06352accf9a2db19edb31037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="f81bc-102">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f81bc-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="f81bc-103">Genel türler 2.0 C# dili ve ortak dil çalışma zamanı (CLR) sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f81bc-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="f81bc-104">Genel türler için .NET Framework tasarım sınıflar ve sınıf veya yöntemin bildirilen ve istemci kodu tarafından örneği kadar bir veya daha fazla türü belirtimini erteleneceği yöntemler için olası kolaylaştırır tür parametreleri kavramı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f81bc-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="f81bc-105">Örneğin, bir genel tür parametresi T kullanarak kullanabileceğiniz diğer istemci kodu maliyet ya da çalışma zamanı atamaları veya kutulama işlemleri riskini yansıtılmasını olmadan aşağıda gösterildiği gibi tek bir sınıf yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f81bc-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="f81bc-106">Genel türler genel bakış</span><span class="sxs-lookup"><span data-stu-id="f81bc-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="f81bc-107">Kodu yeniden kullanma, tür güvenliği ve performansı en üst düzeye çıkarmak için genel türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="f81bc-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="f81bc-108">En yaygın genel türler koleksiyon sınıfları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f81bc-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="f81bc-109">.NET Framework sınıf kitaplığı birkaç yeni genel koleksiyon sınıflarda içeren <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f81bc-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="f81bc-110">Olası yerine gibi sınıflar her durumda bunları kullanılmalıdır <xref:System.Collections.ArrayList> içinde <xref:System.Collections> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f81bc-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="f81bc-111">Sınıfları, yöntemleri, olaylar ve temsilciler kendi genel arabirimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f81bc-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="f81bc-112">Genel sınıflar, belirli veri türlerini yöntemlere erişimi etkinleştirmek için kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="f81bc-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="f81bc-113">Yansıma kullanarak çalışma zamanında bir genel veri türünde kullanılan türleri hakkında bilgi alınabilir.</span><span class="sxs-lookup"><span data-stu-id="f81bc-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f81bc-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f81bc-114">Related Sections</span></span>  
 <span data-ttu-id="f81bc-115">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="f81bc-115">For more information:</span></span>  
  
-   [<span data-ttu-id="f81bc-116">Genel türlere giriş</span><span class="sxs-lookup"><span data-stu-id="f81bc-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="f81bc-117">Genel türlerin yararları</span><span class="sxs-lookup"><span data-stu-id="f81bc-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="f81bc-118">Genel tür parametreleri</span><span class="sxs-lookup"><span data-stu-id="f81bc-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="f81bc-119">Tür parametrelerindeki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="f81bc-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="f81bc-120">Genel sınıflar</span><span class="sxs-lookup"><span data-stu-id="f81bc-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="f81bc-121">Genel arabirimler</span><span class="sxs-lookup"><span data-stu-id="f81bc-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="f81bc-122">Genel yöntemler</span><span class="sxs-lookup"><span data-stu-id="f81bc-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="f81bc-123">Genel temsilciler</span><span class="sxs-lookup"><span data-stu-id="f81bc-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="f81bc-124">C++ şablonları ve C# genel türleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="f81bc-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="f81bc-125">Genel türler ve yansıma</span><span class="sxs-lookup"><span data-stu-id="f81bc-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="f81bc-126">Çalışma zamanındaki genel türler</span><span class="sxs-lookup"><span data-stu-id="f81bc-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [<span data-ttu-id="f81bc-127">.NET Framework Sınıf Kitaplığı'nda genel türler</span><span class="sxs-lookup"><span data-stu-id="f81bc-127">Generics in the .NET Framework Class Library</span></span>](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f81bc-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f81bc-128">C# Language Specification</span></span>  
 <span data-ttu-id="f81bc-129">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f81bc-129">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81bc-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f81bc-130">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="f81bc-131">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f81bc-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f81bc-132">Türler</span><span class="sxs-lookup"><span data-stu-id="f81bc-132">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="f81bc-133">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="f81bc-133">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [<span data-ttu-id="f81bc-134">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="f81bc-134">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
