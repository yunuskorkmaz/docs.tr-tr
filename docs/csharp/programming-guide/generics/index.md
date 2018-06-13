---
title: Genel Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 8f412366072c81b8aaca94829e0aa214f356200d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333820"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="226e7-102">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="226e7-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="226e7-103">Genel türler 2.0 C# dili ve ortak dil çalışma zamanı (CLR) sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="226e7-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="226e7-104">Genel türler için .NET Framework tasarım sınıflar ve sınıf veya yöntemin bildirilen ve istemci kodu tarafından örneği kadar bir veya daha fazla türü belirtimini erteleneceği yöntemler için olası kolaylaştırır tür parametreleri kavramı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="226e7-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="226e7-105">Örneğin, bir genel tür parametresi T kullanarak kullanabileceğiniz diğer istemci kodu maliyet ya da çalışma zamanı atamaları veya kutulama işlemleri riskini yansıtılmasını olmadan aşağıda gösterildiği gibi tek bir sınıf yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="226e7-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="226e7-106">Genel türler genel bakış</span><span class="sxs-lookup"><span data-stu-id="226e7-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="226e7-107">Kodu yeniden kullanma, tür güvenliği ve performansı en üst düzeye çıkarmak için genel türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="226e7-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="226e7-108">En yaygın genel türler koleksiyon sınıfları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="226e7-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="226e7-109">.NET Framework sınıf kitaplığı birkaç yeni genel koleksiyon sınıflarda içeren <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="226e7-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="226e7-110">Olası yerine gibi sınıflar her durumda bunları kullanılmalıdır <xref:System.Collections.ArrayList> içinde <xref:System.Collections> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="226e7-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="226e7-111">Sınıfları, yöntemleri, olaylar ve temsilciler kendi genel arabirimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="226e7-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="226e7-112">Genel sınıflar, belirli veri türlerini yöntemlere erişimi etkinleştirmek için kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="226e7-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="226e7-113">Yansıma kullanarak çalışma zamanında bir genel veri türünde kullanılan türleri hakkında bilgi alınabilir.</span><span class="sxs-lookup"><span data-stu-id="226e7-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="226e7-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="226e7-114">Related Sections</span></span>  
 <span data-ttu-id="226e7-115">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="226e7-115">For more information:</span></span>  
  
-   [<span data-ttu-id="226e7-116">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="226e7-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="226e7-117">Genel Türlerin Yararları</span><span class="sxs-lookup"><span data-stu-id="226e7-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="226e7-118">Genel Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="226e7-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="226e7-119">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="226e7-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="226e7-120">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="226e7-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="226e7-121">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="226e7-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="226e7-122">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="226e7-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="226e7-123">Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="226e7-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="226e7-124">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="226e7-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="226e7-125">Genel Türler ve Yansıma</span><span class="sxs-lookup"><span data-stu-id="226e7-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="226e7-126">Çalışma Zamanındaki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="226e7-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="226e7-127">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="226e7-127">C# Language Specification</span></span>  
 <span data-ttu-id="226e7-128">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="226e7-128">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226e7-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="226e7-129">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="226e7-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="226e7-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="226e7-131">Türler</span><span class="sxs-lookup"><span data-stu-id="226e7-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="226e7-132">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="226e7-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [<span data-ttu-id="226e7-133">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="226e7-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
 [<span data-ttu-id="226e7-134">.NET'nda genel türler</span><span class="sxs-lookup"><span data-stu-id="226e7-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  