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
ms.openlocfilehash: 2a3cca0139974cbc92ce85a19db73dfb3d13d1a0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743574"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="8145c-102">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8145c-102">Type Design Guidelines</span></span>
<span data-ttu-id="8145c-103">CLR perspektifinden, türlerin yalnızca iki kategorisi vardır: başvuru türleri ve değer türleri, ancak çerçeve tasarımı hakkında bir tartışma amacıyla, türleri, her biri kendi belirli tasarım kurallarına sahip daha fazla mantıksal gruba böyoruz.</span><span class="sxs-lookup"><span data-stu-id="8145c-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="8145c-104">Sınıflar, başvuru türlerinin genel durumdur.</span><span class="sxs-lookup"><span data-stu-id="8145c-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="8145c-105">Bu kişiler, çerçevelerin çoğunluğunda türlerin toplu olarak kullanılabilmesini sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="8145c-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="8145c-106">Sınıflar, destekledikleri ve genel uygulanabilirliği olan zengin nesne yönelimli özellikler kümesi için popülerliğini borçlar.</span><span class="sxs-lookup"><span data-stu-id="8145c-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="8145c-107">Taban Sınıflar ve soyut sınıflar, genişletilebilirlik ile ilgili özel mantıksal gruplardır.</span><span class="sxs-lookup"><span data-stu-id="8145c-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="8145c-108">Arabirimler, başvuru türleri ve değer türleri tarafından uygulanabilen türlerdir.</span><span class="sxs-lookup"><span data-stu-id="8145c-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="8145c-109">Bunlar, bu nedenle, polimorfik, başvuru türleri ve değer türleri için kökler olarak işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="8145c-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="8145c-110">Ayrıca, arabirimler, CLR tarafından yerel olarak desteklenmeyen birden çok devralmanın benzetimini yapmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8145c-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="8145c-111">Yapılar, değer türlerinin genel durumdur ve dil temel elemanlarına benzer küçük, basit türler için ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8145c-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="8145c-112">Numaralandırmalar, haftanın günleri, konsol renkleri vb. gibi kısa değer kümelerini tanımlamak için kullanılan değer türlerinin özel bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="8145c-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="8145c-113">Statik sınıflar, statik üyeler için kapsayıcılar olması amaçlanan türlerdir.</span><span class="sxs-lookup"><span data-stu-id="8145c-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="8145c-114">Bunlar genellikle diğer işlemlere kısayollar sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8145c-114">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="8145c-115">Temsilciler, özel durumlar, öznitelikler, diziler ve koleksiyonlar, belirli kullanımlar için tasarlanan başvuru türlerinin tüm özel durumlarıyla ve tasarım ve kullanımlarıyla ilgili yönergelerin bu kitapta başka bir yerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="8145c-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="8145c-116">✔️ Her türün iyi tanımlanmış bir ilgili üye kümesi olduğundan emin olmak için, yalnızca, ilişkisiz işlevlerin rastgele bir koleksiyonunu değil.</span><span class="sxs-lookup"><span data-stu-id="8145c-116">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8145c-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8145c-117">In This Section</span></span>
 <span data-ttu-id="8145c-118">[Sınıf ve yapı](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md) [soyut sınıf tasarımı](../../../docs/standard/design-guidelines/abstract-class.md) arasında seçim yapma [statik sınıf tasarımı](../../../docs/standard/design-guidelines/static-class.md) [arabirim tasarım](../../../docs/standard/design-guidelines/interface.md) [yapı birimi](../../../docs/standard/design-guidelines/struct.md) tasarım [enum](../../../docs/standard/design-guidelines/enum.md) tasarım [iç içe türler](../../../docs/standard/design-guidelines/nested-types.md) *bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="8145c-118">[Choosing Between Class and Struct](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md) [Abstract Class Design](../../../docs/standard/design-guidelines/abstract-class.md) [Static Class Design](../../../docs/standard/design-guidelines/static-class.md) [Interface Design](../../../docs/standard/design-guidelines/interface.md) [Struct Design](../../../docs/standard/design-guidelines/struct.md) [Enum Design](../../../docs/standard/design-guidelines/enum.md) [Nested Types](../../../docs/standard/design-guidelines/nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8145c-119">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="8145c-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8145c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8145c-120">See also</span></span>

- [<span data-ttu-id="8145c-121">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8145c-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
