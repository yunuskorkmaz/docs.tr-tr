---
title: Tür Tasarımı Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709029"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="48377-102">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="48377-102">Type Design Guidelines</span></span>
<span data-ttu-id="48377-103">CLR perspektifinden, türlerin yalnızca iki kategorisi vardır: başvuru türleri ve değer türleri, ancak çerçeve tasarımı hakkında bir tartışma amacıyla, türleri, her biri kendi belirli tasarım kurallarına sahip daha fazla mantıksal gruba böyoruz.</span><span class="sxs-lookup"><span data-stu-id="48377-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="48377-104">Sınıflar, başvuru türlerinin genel durumdur.</span><span class="sxs-lookup"><span data-stu-id="48377-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="48377-105">Bu kişiler, çerçevelerin çoğunluğunda türlerin toplu olarak kullanılabilmesini sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="48377-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="48377-106">Sınıflar, destekledikleri ve genel uygulanabilirliği olan zengin nesne yönelimli özellikler kümesi için popülerliğini borçlar.</span><span class="sxs-lookup"><span data-stu-id="48377-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="48377-107">Taban Sınıflar ve soyut sınıflar, genişletilebilirlik ile ilgili özel mantıksal gruplardır.</span><span class="sxs-lookup"><span data-stu-id="48377-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="48377-108">Arabirimler, başvuru türleri ve değer türleri tarafından uygulanabilen türlerdir.</span><span class="sxs-lookup"><span data-stu-id="48377-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="48377-109">Bunlar, bu nedenle, polimorfik, başvuru türleri ve değer türleri için kökler olarak işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="48377-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="48377-110">Ayrıca, arabirimler, CLR tarafından yerel olarak desteklenmeyen birden çok devralmanın benzetimini yapmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48377-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="48377-111">Yapılar, değer türlerinin genel durumdur ve dil temel elemanlarına benzer küçük, basit türler için ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48377-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="48377-112">Numaralandırmalar, haftanın günleri, konsol renkleri vb. gibi kısa değer kümelerini tanımlamak için kullanılan değer türlerinin özel bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="48377-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="48377-113">Statik sınıflar, statik üyeler için kapsayıcılar olması amaçlanan türlerdir.</span><span class="sxs-lookup"><span data-stu-id="48377-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="48377-114">Bunlar genellikle diğer işlemlere kısayollar sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48377-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="48377-115">Temsilciler, özel durumlar, öznitelikler, diziler ve koleksiyonlar, belirli kullanımlar için tasarlanan başvuru türlerinin tüm özel durumlarıyla ve tasarım ve kullanımlarıyla ilgili yönergelerin bu kitapta başka bir yerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="48377-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="48377-116">**✓ DO** her tür iyi tanımlanmış bir grup yalnızca rastgele koleksiyonunu ilgisiz işlevselliği ilgili üyesi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="48377-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48377-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="48377-117">In This Section</span></span>  
 [<span data-ttu-id="48377-118">Sınıf ile Yapı Arasında Seçim Yapma</span><span class="sxs-lookup"><span data-stu-id="48377-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="48377-119">Soyut Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="48377-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="48377-120">Statik Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="48377-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="48377-121">Arabirim Tasarımı</span><span class="sxs-lookup"><span data-stu-id="48377-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="48377-122">Yapı Tasarımı</span><span class="sxs-lookup"><span data-stu-id="48377-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="48377-123">Sabit Listesi Tasarımı</span><span class="sxs-lookup"><span data-stu-id="48377-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="48377-124">İç içe Geçmiş Türler</span><span class="sxs-lookup"><span data-stu-id="48377-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="48377-125">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="48377-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="48377-126">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="48377-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48377-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48377-127">See also</span></span>

- [<span data-ttu-id="48377-128">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="48377-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
