---
title: C++ Şablonları ile C# Generics Arasındaki Farklar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: e44f67353410c58c406620109270972df17f9f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703539"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="c408d-102">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c408d-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="c408d-103">C# Generics ve C++ şablonları, parametreli türleri destekleyen her iki dil özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="c408d-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="c408d-104">Ancak, ikisi arasında birçok fark vardır.</span><span class="sxs-lookup"><span data-stu-id="c408d-104">However, there are many differences between the two.</span></span> <span data-ttu-id="c408d-105">Sözdizimi düzeyinde, C# jeneronları C++ şablonlarının karmaşıklığı olmadan parametrelendirilmiş türlere daha basit bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="c408d-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="c408d-106">Ayrıca, C# C++ şablonlarının sağladığı tüm işlevleri sağlamaya çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="c408d-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="c408d-107">Uygulama düzeyinde, birincil fark C# genel tür değiştirmelerinin çalışma zamanında gerçekleştirilmesi ve genel tür bilgilerinin anlık nesneler için korunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c408d-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="c408d-108">Daha fazla bilgi için [Çalışma Süresi'ndeki Genel Bilgiler'e](./generics-in-the-run-time.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c408d-108">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="c408d-109">C# Generics ve C++ şablonları arasındaki temel farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c408d-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="c408d-110">C# jenerikleri, C++ şablonları ile aynı düzeyde esneklik sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c408d-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="c408d-111">Örneğin, kullanıcı tanımlı işleçleri çağırmak mümkün olsa da, C# genel sınıfında aritmetik işleçleri aramak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c408d-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="c408d-112">C# gibi `template C<int i> {}`tür olmayan şablon parametrelerine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c408d-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="c408d-113">C# açık uzmanlık desteklemez; diğer bir şekilde, belirli bir tür için şablonun özel bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c408d-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="c408d-114">C# kısmi uzmanlaşmayı desteklemez: tür bağımsız değişkenlerinin bir alt kümesi için özel bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="c408d-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="c408d-115">C# türü parametresinin genel tür için taban sınıf olarak kullanılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c408d-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="c408d-116">C# tür parametrelerinin varsayılan türlere sahip olmasını sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c408d-116">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="c408d-117">C#'da, genel bir tür parametresi genel olarak kullanılamaz, ancak yapılandırılan türler genel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c408d-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="c408d-118">C++ şablon parametrelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c408d-118">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="c408d-119">C++, şablondaki tüm tür parametreleri için geçerli olmayan koda izin verir ve bu kod, daha sonra tür parametresi olarak kullanılan belirli bir tür için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="c408d-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="c408d-120">C# bir sınıftaki kodun kısıtlamaları karşılayan herhangi bir türle çalışacak şekilde yazılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c408d-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="c408d-121">Örneğin, C++'da aritmetik işleçleri `+` kullanan ve tür `-` parametresinin nesneleri üzerinde bu işleçleri desteklemeyen bir türle şablonun anında bir hata üretecek bir işlev yazmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c408d-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="c408d-122">C# bunu disallows; izin verilen tek dil yapıları kısıtlamalardan çıkarılabilenlerdir.</span><span class="sxs-lookup"><span data-stu-id="c408d-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c408d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c408d-123">See also</span></span>

- [<span data-ttu-id="c408d-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c408d-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c408d-125">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="c408d-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="c408d-126">Şablon</span><span class="sxs-lookup"><span data-stu-id="c408d-126">Templates</span></span>](/cpp/cpp/templates-cpp)
