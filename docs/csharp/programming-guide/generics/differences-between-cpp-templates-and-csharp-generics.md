---
title: C++ şablonları arasındaki farklar ve C# genel türler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 13ecd6c0d613199210610c1c094ae1bdabaa71a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608476"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="f9c78-102">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f9c78-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="f9c78-103">C# genel türleri ve C++ şablonları parametreli türler için destek sağlayan her iki dil özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="f9c78-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="f9c78-104">Ancak, ikisi arasındaki pek çok fark vardır.</span><span class="sxs-lookup"><span data-stu-id="f9c78-104">However, there are many differences between the two.</span></span> <span data-ttu-id="f9c78-105">Sözdizimi, C# genel türleri için C++ şablonlarının karmaşıklığı olmadan parametreli türler basit bir yaklaşım düzeyindedir.</span><span class="sxs-lookup"><span data-stu-id="f9c78-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="f9c78-106">Ayrıca, C# tüm C++ şablonları sağlayan işlevselliği sağlamak denemez.</span><span class="sxs-lookup"><span data-stu-id="f9c78-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="f9c78-107">Uygulama düzeyinde birincil çalışma zamanında C# genel tür değişimler gerçekleştirilir ve genel tür bilgileri, böylece örneklenen nesneleri korunur farktır.</span><span class="sxs-lookup"><span data-stu-id="f9c78-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="f9c78-108">Daha fazla bilgi için [çalışma zamanı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="f9c78-108">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="f9c78-109">C++ şablonları ile C# genel türleri arasındaki temel farklılıklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f9c78-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="f9c78-110">C# genel türleri aynı miktarda C++ şablonları olarak esneklik sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f9c78-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="f9c78-111">Kullanıcı tanımlı işleçler çağrılabilir olsa gibi bir C# genel sınıfta, aritmetik işleçler çağırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="f9c78-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="f9c78-112">C# izin vermiyor tür olmayan şablon parametreleri gibi `template C<int i> {}`.</span><span class="sxs-lookup"><span data-stu-id="f9c78-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="f9c78-113">C# açık özelleştirme desteklemez; diğer bir deyişle, özel uygulanışı belirli bir tür için bir şablon.</span><span class="sxs-lookup"><span data-stu-id="f9c78-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="f9c78-114">C# kısmi özelleştirmede desteklemiyor: özel bir uygulama için bir alt tür bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="f9c78-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="f9c78-115">C# genel tür için temel sınıf olarak kullanılacak tür parametresi izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f9c78-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="f9c78-116">C# varsayılan türler tür parametreleri izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f9c78-116">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="f9c78-117">Genel türler oluşturulan türler kullanılabilir olsa da C# ' ta genel tür parametresi kendisi bir genel olamaz.</span><span class="sxs-lookup"><span data-stu-id="f9c78-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="f9c78-118">C++ şablon parametreleri izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f9c78-118">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="f9c78-119">C++ tür parametresi kullanılan belirli bir tür için denetlenir şablondaki tüm tür parametreleri için geçerli olmayabilir kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9c78-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="f9c78-120">C# kısıtlamalar karşılayan herhangi bir türde çalışır şekilde yazılacak bir sınıftaki kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f9c78-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="f9c78-121">Örneğin, c++'ta aritmetik işleçler kullanan bir işlev yazmak mümkündür `+` ve `-` tür parametresinin nesneler üzerinde hangi ilişkilendiren bir hata şablonu bir örneğinin bu desteği olmayan bir tür ile anında işleçler.</span><span class="sxs-lookup"><span data-stu-id="f9c78-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="f9c78-122">C# bu izin vermiyor; izin verilen tek dil yapıları kısıtlamalardan çıkarılabildiği olanlardır.</span><span class="sxs-lookup"><span data-stu-id="f9c78-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c78-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9c78-123">See also</span></span>

- [<span data-ttu-id="f9c78-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f9c78-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f9c78-125">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="f9c78-125">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [<span data-ttu-id="f9c78-126">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="f9c78-126">Templates</span></span>](/cpp/cpp/templates-cpp)
