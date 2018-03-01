---
title: "C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aea1b51c26a8f3de56ea66b9cf89e75bfeb59d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="d1104-102">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d1104-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="d1104-103">C# genel türleri ve C++ şablonları parametreli türleri için destek sağlayan iki dil özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="d1104-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="d1104-104">Bununla birlikte, ikisi arasındaki birçok farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="d1104-104">However, there are many differences between the two.</span></span> <span data-ttu-id="d1104-105">Sözdizimi, C# genel türleri C++ şablonlarının KARMAŞASIZ parametreli türler için basit bir yaklaşım düzeyindedir.</span><span class="sxs-lookup"><span data-stu-id="d1104-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="d1104-106">Ayrıca, C# tüm C++ şablonları sağlar işlevselliği sağlamak denemez.</span><span class="sxs-lookup"><span data-stu-id="d1104-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="d1104-107">Uygulama düzeyinde birincil çalışma zamanında C# genel tür kısaltmaları gerçekleştirilir ve genel tür bilgileri için örnek nesneleri böylece korunur farktır.</span><span class="sxs-lookup"><span data-stu-id="d1104-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="d1104-108">Daha fazla bilgi için bkz: [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="d1104-108">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="d1104-109">C++ şablonları ile C# genel türleri arasındaki temel farklılıklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d1104-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
-   <span data-ttu-id="d1104-110">C# genel türleri esneklik C++ şablon olarak aynı miktarda sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d1104-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="d1104-111">Kullanıcı tanımlı işleçler çağırmak mümkün olsa Örneğin, bunu bir C# genel sınıfta aritmetik işleçler çağırmak mümkün değil.</span><span class="sxs-lookup"><span data-stu-id="d1104-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
-   <span data-ttu-id="d1104-112">C# izin vermiyor tür olmayan şablon parametreleri gibi `template C<int i> {}`.</span><span class="sxs-lookup"><span data-stu-id="d1104-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
-   <span data-ttu-id="d1104-113">C# açık uzmanlık desteklemiyor; belirli bir tür için bir şablon başka bir deyişle, özel bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d1104-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
-   <span data-ttu-id="d1104-114">C# kısmi uzmanlığı desteklemiyor: tür bağımsız değişkenleri bir alt kümesi için özel bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d1104-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
-   <span data-ttu-id="d1104-115">C# genel tür için temel sınıf olarak kullanılacak tür parametresi izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="d1104-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
-   <span data-ttu-id="d1104-116">C# varsayılan türleri tür parametreleri izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="d1104-116">C# does not allow type parameters to have default types.</span></span>  
  
-   <span data-ttu-id="d1104-117">Genel türler oluşturulan türler kullanılabilse de C# ' ta bir genel tür parametresi kendisini bir genel olamaz.</span><span class="sxs-lookup"><span data-stu-id="d1104-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="d1104-118">C++ şablon parametreleri izin vermez.</span><span class="sxs-lookup"><span data-stu-id="d1104-118">C++ does allow template parameters.</span></span>  
  
-   <span data-ttu-id="d1104-119">C++ tür parametresi kullanılan belirli türünün sonra kullanıma şablondaki tüm tür parametreleri için geçerli olmayabilir kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1104-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="d1104-120">C# kod kısıtlamaları karşılayan herhangi bir türü ile çalışacağını şekilde yazılması için bir sınıf gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d1104-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="d1104-121">Örneğin, c++'ta aritmetik işleçler kullanan bir işlev yazmak mümkündür `+` ve `-` tür parametresi nesnelerde hangi oluşturacak bir hata şablonu örneklemesi bu desteklemeyen türüne sahip zaman işleçler.</span><span class="sxs-lookup"><span data-stu-id="d1104-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="d1104-122">C# bu izin vermez; izin verilen tek dil yapıları kısıtlamaları anlaşılan izinlerdir.</span><span class="sxs-lookup"><span data-stu-id="d1104-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1104-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1104-123">See Also</span></span>  
 [<span data-ttu-id="d1104-124">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d1104-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d1104-125">Genel türlere giriş</span><span class="sxs-lookup"><span data-stu-id="d1104-125">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="d1104-126">Şablonları</span><span class="sxs-lookup"><span data-stu-id="d1104-126">Templates</span></span>](/cpp/cpp/templates-cpp)
