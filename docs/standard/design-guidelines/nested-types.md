---
title: İç içe Geçmiş Türler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: a3b090b39e1e907826551ed152d4eece4885ce41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290142"
---
# <a name="nested-types"></a><span data-ttu-id="0bb2c-102">İç içe Geçmiş Türler</span><span class="sxs-lookup"><span data-stu-id="0bb2c-102">Nested Types</span></span>
<span data-ttu-id="0bb2c-103">İç içe bir tür, kapsayan tür olarak adlandırılan başka bir türün kapsamı içinde tanımlanan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="0bb2c-104">İç içe bir tür, kapsayan türünün tüm üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="0bb2c-105">Örneğin, kapsayan tür ' de tanımlanan özel alanlara ve kapsayan türün tüm yokler ' de tanımlanan korumalı alanlara erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>

 <span data-ttu-id="0bb2c-106">Genel olarak, iç içe türler gelişigüzel kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="0bb2c-107">Bunun birçok nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-107">There are several reasons for this.</span></span> <span data-ttu-id="0bb2c-108">Bazı geliştiriciler kavram ile tam olarak tanıdık değildir.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="0bb2c-109">Bu geliştiriciler Örneğin, iç içe geçmiş türlerin değişkenlerini bildirme söz dizimi ile ilgili sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="0bb2c-110">İç içe türler aynı zamanda kapsayan türleriyle çok sıkı bir şekilde bağlanmış ve bu nedenle genel amaçlı türler gibi uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>

 <span data-ttu-id="0bb2c-111">İç içe türler, kapsayan türlerin modelleme uygulama ayrıntıları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="0bb2c-112">Son Kullanıcı nadiren iç içe bir türün değişkenlerini bildirmeli ve neredeyse asla iç içe geçmiş türleri örneklemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="0bb2c-113">Örneğin, bir koleksiyonun numaralandırıcısı, o koleksiyonun iç içe bir türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="0bb2c-114">Numaralandırıcılar genellikle kapsayan türlerine göre örneklenmiştir ve birçok dil foreach ifadesini destekledikleri için, Numaralandırıcı değişkenlerinin Son Kullanıcı tarafından bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>

 <span data-ttu-id="0bb2c-115">iç içe geçmiş türü ve onun dış türü arasındaki ilişki, üye erişilebilirlik semantiklerine göre istenmediğinde iç içe türler kullanın ✔️.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-115">✔️ DO use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>

 <span data-ttu-id="0bb2c-116">❌Genel iç içe türler mantıksal gruplandırma yapısı olarak kullanmayın; Bu ad alanlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-116">❌ DO NOT use public nested types as a logical grouping construct; use namespaces for this.</span></span>

 <span data-ttu-id="0bb2c-117">❌Genel kullanıma açık iç içe türler kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-117">❌ AVOID publicly exposed nested types.</span></span> <span data-ttu-id="0bb2c-118">Bunun tek istisnası, iç içe türün değişkenlerinin yalnızca altsınıflama veya diğer gelişmiş özelleştirme senaryoları gibi nadir senaryolarda bildirilmesine ihtiyaç duymalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>

 <span data-ttu-id="0bb2c-119">❌Tür, kapsayan tür dışında başvuruluyorsa iç içe türler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-119">❌ DO NOT use nested types if the type is likely to be referenced outside of the containing type.</span></span>

 <span data-ttu-id="0bb2c-120">Örneğin, bir sınıfta tanımlanan bir metoda geçirilen Enum, sınıfta iç içe geçmiş bir tür olarak tanımlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>

 <span data-ttu-id="0bb2c-121">❌İç içe türler, istemci kodu tarafından örneklenmeleri gerekiyorsa kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-121">❌ DO NOT use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="0bb2c-122">Bir türün ortak Oluşturucusu varsa, muhtemelen iç içe olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-122">If a type has a public constructor, it should probably not be nested.</span></span>

 <span data-ttu-id="0bb2c-123">Bir tür örneği oluşturulabilir, bu, türün kendi çerçevesinde bir yerde yer aldığı anlamına gelir (bunu oluşturabilir, onunla çalışabilir ve dış türü kullanmadan yok edebilir) ve bu nedenle iç içe geçmemelidir.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="0bb2c-124">İç türler, dış tür herhangi bir ilişki olmadan dış türün dışında yaygın olarak yeniden kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>

 <span data-ttu-id="0bb2c-125">❌İç içe bir türü arabirimin üyesi olarak tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-125">❌ DO NOT define a nested type as a member of an interface.</span></span> <span data-ttu-id="0bb2c-126">Birçok dil böyle bir yapıyı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-126">Many languages do not support such a construct.</span></span>

 <span data-ttu-id="0bb2c-127">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="0bb2c-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="0bb2c-128">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="0bb2c-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="0bb2c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bb2c-129">See also</span></span>

- [<span data-ttu-id="0bb2c-130">Tür tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0bb2c-130">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="0bb2c-131">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0bb2c-131">Framework Design Guidelines</span></span>](index.md)
