---
title: Şablonlar ve C++ C# genel türler arasındaki farklar C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: e44f67353410c58c406620109270972df17f9f86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75703539"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="895b1-102">C++ Şablonları ve C# Genel Türleri Arasındaki Farklar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="895b1-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="895b1-103">C#Genel türler C++ ve şablonlar, parametreli türler için destek sağlayan dil özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="895b1-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="895b1-104">Ancak, ikisi arasında birçok farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="895b1-104">However, there are many differences between the two.</span></span> <span data-ttu-id="895b1-105">Sözdizimi düzeyinde, C# genel türler C++ şablonların karmaşıklığı olmadan parametreli türlere daha basit bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="895b1-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="895b1-106">Ayrıca, C# C++ şablonların sağladığı tüm işlevleri sağlamayı denemez.</span><span class="sxs-lookup"><span data-stu-id="895b1-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="895b1-107">Uygulama düzeyinde, birincil farklılık, genel tür değişimlerin C# çalışma zamanında gerçekleştirildiği ve genel tür bilgilerinin, bu nedenle örneklenmiş nesneler için korunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="895b1-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="895b1-108">Daha fazla bilgi için bkz. [çalışma zamanındaki genel türler](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="895b1-108">For more information, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="895b1-109">Aşağıdakiler, genel türler ve C# C++ şablonlar arasındaki önemli farklardır:</span><span class="sxs-lookup"><span data-stu-id="895b1-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
- <span data-ttu-id="895b1-110">C#Genel türler, C++ şablonlarla aynı esneklik miktarını sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="895b1-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="895b1-111">Örneğin, Kullanıcı tanımlı işleçleri çağırmak mümkün olsa da, genel bir C# sınıfta aritmetik işleçleri çağırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="895b1-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
- <span data-ttu-id="895b1-112">C#`template C<int i> {}`gibi tür olmayan şablon parametrelerine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="895b1-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
- <span data-ttu-id="895b1-113">C#Açık özelleştirmeyi desteklemez; diğer bir deyişle, belirli bir tür için bir şablonun özel bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="895b1-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
- <span data-ttu-id="895b1-114">C#Kısmi özelleştirmeyi desteklemez: tür bağımsız değişkenlerinin bir alt kümesi için özel bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="895b1-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
- <span data-ttu-id="895b1-115">C#tür parametresinin genel tür için temel sınıf olarak kullanılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="895b1-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
- <span data-ttu-id="895b1-116">C#tür parametrelerinin varsayılan türleri olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="895b1-116">C# does not allow type parameters to have default types.</span></span>  
  
- <span data-ttu-id="895b1-117">İçinde C#, bir genel tür parametresi genel olamaz, ancak oluşturulan türler genel türler olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="895b1-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="895b1-118">C++Şablon parametrelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="895b1-118">C++ does allow template parameters.</span></span>  
  
- <span data-ttu-id="895b1-119">C++şablondaki tüm tür parametreleri için geçerli olmayan koda izin verir, daha sonra tür parametresi olarak kullanılan belirli tür için denetlenir.</span><span class="sxs-lookup"><span data-stu-id="895b1-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="895b1-120">C#, bir sınıftaki kodun, kısıtlamaları karşılayan herhangi bir türle çalışacak şekilde yazılmasına gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="895b1-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="895b1-121">Örneğin, içinde C++ aritmetik işleçleri kullanan bir işlev yazmak mümkündür `+` ve tür parametresinin nesneleri üzerinde `-`, bu işleçleri desteklemeyen bir tür ile şablon örneği oluşturma sırasında bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="895b1-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="895b1-122">C#Buna izin vermez; izin verilen tek dil yapıları, kısıtlamalardan çıkarsanolabilecek olanlardır.</span><span class="sxs-lookup"><span data-stu-id="895b1-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895b1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="895b1-123">See also</span></span>

- [<span data-ttu-id="895b1-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="895b1-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="895b1-125">Genel Türlere Giriş</span><span class="sxs-lookup"><span data-stu-id="895b1-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="895b1-126">Şablonlar</span><span class="sxs-lookup"><span data-stu-id="895b1-126">Templates</span></span>](/cpp/cpp/templates-cpp)
