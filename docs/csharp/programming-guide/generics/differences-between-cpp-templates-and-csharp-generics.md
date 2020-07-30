---
title: C++ şablonları ve C# genel türleri arasındaki farklar-C# Programlama Kılavuzu
description: C++ şablonları ve C# genel türleri arasındaki farklar hakkında bilgi edinin. Her ikisi de parametreli türler için destek sağlayan dil özelliklerdir.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: f405e2d4bef730317703b3b8470edef5b89f0bed
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301937"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="d6f35-104">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d6f35-104">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="d6f35-105">C# Generics ve C++ şablonları, parametreli türler için destek sağlayan dil özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="d6f35-105">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="d6f35-106">Ancak, ikisi arasında birçok farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="d6f35-106">However, there are many differences between the two.</span></span> <span data-ttu-id="d6f35-107">Sözdizimi düzeyinde C# genel türleri, C++ şablonlarının karmaşıklığı olmadan parametreli türlere daha basit bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="d6f35-107">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="d6f35-108">Ayrıca C#, C++ şablonlarının sağladığı tüm işlevleri sağlamaya çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d6f35-108">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="d6f35-109">Uygulama düzeyinde, birincil fark, C# genel tür değişimlerin çalışma zamanında ve genel tür bilgilerinin bu nedenle oluşturulan nesneler için korunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d6f35-109">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="d6f35-110">Daha fazla bilgi için bkz. [çalışma zamanındaki genel türler](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="d6f35-110">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="d6f35-111">C# genel türleri ve C++ şablonları arasındaki temel farklılıklar aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d6f35-111">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="d6f35-112">C# genel türleri, C++ şablonlarıyla aynı esneklik miktarını sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d6f35-112">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="d6f35-113">Örneğin, Kullanıcı tanımlı işleçleri çağırmak mümkün olsa da, bir C# genel sınıfında aritmetik işleçleri çağırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d6f35-113">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="d6f35-114">C#, gibi tür olmayan şablon parametrelerine izin vermez `template C<int i> {}` .</span><span class="sxs-lookup"><span data-stu-id="d6f35-114">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="d6f35-115">C# açık özelleştirmeyi desteklemez; diğer bir deyişle, belirli bir tür için bir şablonun özel bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d6f35-115">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="d6f35-116">C# Kısmi özelleştirmeyi desteklemez: tür bağımsız değişkenlerinin bir alt kümesi için özel bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="d6f35-116">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="d6f35-117">C#, tür parametresinin genel tür için temel sınıf olarak kullanılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="d6f35-117">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="d6f35-118">C#, tür parametrelerinin varsayılan türleri olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6f35-118">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="d6f35-119">C# dilinde, bir genel tür parametresi genel olamaz, ancak oluşturulan türler genel türler olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6f35-119">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="d6f35-120">C++, şablon parametrelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d6f35-120">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="d6f35-121">C++, şablondaki tüm tür parametreleri için geçerli olmayan koda izin verir, daha sonra tür parametresi olarak kullanılan belirli tür için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="d6f35-121">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="d6f35-122">C#, bir sınıftaki kodun, kısıtlamaları karşılayan herhangi bir türle çalışacak şekilde yazılmasına gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="d6f35-122">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="d6f35-123">Örneğin, C++ ' da aritmetik işleçleri ve tür parametresinin nesnelerini kullanan bir işlev yazmak mümkündür `+` `-` , bu da bu işleçleri desteklemeyen bir tür ile şablon örneği oluşturma sırasında bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6f35-123">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="d6f35-124">C# buna izin vermez; izin verilen tek dil yapıları, kısıtlamalardan çıkarsanolabilecek olanlardır.</span><span class="sxs-lookup"><span data-stu-id="d6f35-124">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f35-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6f35-125">See also</span></span>

- [<span data-ttu-id="d6f35-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d6f35-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d6f35-127">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="d6f35-127">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="d6f35-128">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="d6f35-128">Templates</span></span>](/cpp/cpp/templates-cpp)
