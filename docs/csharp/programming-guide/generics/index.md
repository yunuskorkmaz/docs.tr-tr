---
title: Genel Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 9aa57fd31b8d969bbbbf4329a028007f42d3e097
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50042317"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="2ac5c-102">Genel Türler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2ac5c-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="2ac5c-103">Genel türler, C# dili ve ortak dil çalışma zamanı (CLR) 2.0 sürümüne eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="2ac5c-104">Genel türler için .NET Framework tasarım sınıfları ve sınıf ya da yöntem bildirildi ve istemci kodu sayesinde örneği kadar bir veya daha fazla tür belirtimi erteleme yöntemlere mümkün hale tür parametrelerinin kavramı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="2ac5c-105">Örneğin, bir genel tür parametre T kullanarak diğer istemci kodu çalışma zamanı atamaları veya kutulama işlemleri riskini ve maliyet olmaksızın burada gösterildiği gibi kullanabileceğiniz tek bir sınıf yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2ac5c-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="2ac5c-106">Genel türlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="2ac5c-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="2ac5c-107">Genel türler, kod yeniden kullanımını, tür güvenliği ve performansı en üst düzeye çıkarmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="2ac5c-108">Genel türlerin yararları en yaygın kullanımı, koleksiyon sınıfları oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="2ac5c-109">.NET Framework sınıf kitaplığı çeşitli yeni genel koleksiyon sınıflarını içeren <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="2ac5c-110">Olası yerine gibi sınıfların her durumda bu kullanılmalıdır <xref:System.Collections.ArrayList> içinde <xref:System.Collections> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="2ac5c-111">Kendi genel arabirimler, sınıflar, yöntemler, olaylar ve temsilciler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="2ac5c-112">Genel sınıflar, yöntemler belirli veri türlerinde erişimi etkinleştirmek için kısıtlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="2ac5c-113">Genel veri türü kullanılan türleri hakkında bilgi çalışma zamanında yansıma kullanarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2ac5c-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2ac5c-114">Related Sections</span></span>  
 <span data-ttu-id="2ac5c-115">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="2ac5c-115">For more information:</span></span>  
  
-   [<span data-ttu-id="2ac5c-116">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="2ac5c-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="2ac5c-117">Genel Türlerin Yararları</span><span class="sxs-lookup"><span data-stu-id="2ac5c-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="2ac5c-118">Genel Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="2ac5c-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="2ac5c-119">Tür Parametrelerindeki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="2ac5c-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="2ac5c-120">Genel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="2ac5c-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="2ac5c-121">Genel Arabirimler</span><span class="sxs-lookup"><span data-stu-id="2ac5c-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="2ac5c-122">Genel Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2ac5c-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="2ac5c-123">Genel Temsilciler</span><span class="sxs-lookup"><span data-stu-id="2ac5c-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="2ac5c-124">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="2ac5c-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="2ac5c-125">Genel Türler ve Yansıma</span><span class="sxs-lookup"><span data-stu-id="2ac5c-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="2ac5c-126">Çalışma Zamanındaki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="2ac5c-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2ac5c-127">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2ac5c-127">C# Language Specification</span></span>  
 <span data-ttu-id="2ac5c-128">Daha fazla bilgi edinmek için, bkz. [C# Dil Belirtimi](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="2ac5c-128">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac5c-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ac5c-129">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="2ac5c-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2ac5c-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2ac5c-131">Türler</span><span class="sxs-lookup"><span data-stu-id="2ac5c-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="2ac5c-132">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="2ac5c-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
- [<span data-ttu-id="2ac5c-133">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="2ac5c-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
- [<span data-ttu-id="2ac5c-134">.NET içindeki genel türler</span><span class="sxs-lookup"><span data-stu-id="2ac5c-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  