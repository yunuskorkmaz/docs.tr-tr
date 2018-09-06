---
title: İç içe Geçmiş Türler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2593b85dd4747a3fbe365994c3e5d9beae3e3406
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891546"
---
# <a name="nested-types"></a><span data-ttu-id="f9730-102">İç içe Geçmiş Türler</span><span class="sxs-lookup"><span data-stu-id="f9730-102">Nested Types</span></span>
<span data-ttu-id="f9730-103">İç içe türü kapsayan tür adlı başka bir tür kapsamında tanımlanan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="f9730-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="f9730-104">İç içe türü, kapsayan türdeki tüm üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="f9730-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="f9730-105">Örneğin, kapsayan türdeki ve protected olarak kapsayan türdeki tüm üst öğelerinden içinde tanımlanan alanların tanımlı özel alanlara erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="f9730-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="f9730-106">Genel olarak, iç içe geçmiş türler kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9730-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="f9730-107">Bunun birkaç nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="f9730-107">There are several reasons for this.</span></span> <span data-ttu-id="f9730-108">Bazı geliştiriciler kavramı ile tamamen tanıdık olmayan.</span><span class="sxs-lookup"><span data-stu-id="f9730-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="f9730-109">Örneğin, bu geliştiricilerin iç içe geçmiş türlerinin değişkenleri bildirme söz dizimi ile ilgili sorunlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9730-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="f9730-110">İç içe geçmiş türler kapsayan türlerini de çok sıkı şekilde bağlı ve bu nedenle genel amaçlı türleri için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="f9730-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="f9730-111">İç içe geçmiş türler uygulama ayrıntılarını kapsayan türleri modellemek için uygundur.</span><span class="sxs-lookup"><span data-stu-id="f9730-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="f9730-112">Son kullanıcı, iç içe türün değişkenler bildirmek nadiren olmalıdır ve neredeyse hiç açıkça iç içe geçmiş türler oluşturmak sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9730-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="f9730-113">Örneğin, bir koleksiyonun Numaralandırıcı, koleksiyon iç içe geçmiş bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9730-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="f9730-114">Numaralandırıcılar genellikle kapsayan türü tarafından örneği oluşturulur ve birçok dilde foreach deyimi desteklediğinden, numaralandırıcı değişkenleri nadiren son kullanıcı tarafından bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9730-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="f9730-115">**✓ DO** üye erişilebilirlik semantiği istenen şekilde iç içe geçmiş tür ve dış türü arasındaki ilişkiyi olduğunda iç içe geçmiş türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9730-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="f9730-116">**X DO NOT** kullanım ortak iç içe geçmiş türler, mantıksal bir gruplandırma olarak oluşturun; ad alanları için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9730-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="f9730-117">**X AVOID** herkese açık şekilde iç içe geçmiş türler açık.</span><span class="sxs-lookup"><span data-stu-id="f9730-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="f9730-118">Tek özel durumu, iç içe türün değişkenleri yalnızca sınıflara veya diğer gelişmiş özelleştirme senaryoları gibi nadir senaryolarda bildirilmelidir gerektiğinde olur.</span><span class="sxs-lookup"><span data-stu-id="f9730-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="f9730-119">**X DO NOT** türü içeren türde dışında başvurulacak olasılığı olan iç içe geçmiş türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9730-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="f9730-120">Örneğin, bir sınıfta tanımlanan yönteme geçirilen bir sabit listesi sınıfı iç içe geçmiş tür olarak tanımlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9730-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="f9730-121">**X DO NOT** istemci kodu tarafından örneğinin oluşturulması gerekirse iç içe geçmiş türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="f9730-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="f9730-122">Bir tür genel bir oluşturucusu varsa, bu yuvalanmış olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f9730-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="f9730-123">Bir tür oluşturulabilir, kilitlersiniz türüne sahip bir yerde kendi framework belirtmek için (oluşturun, birlikte çalışmak ve dış türün kullanmadan yok) ve bu nedenle iç içe yerleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="f9730-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="f9730-124">İç türleri değil yaygın olarak yeniden kullanılabilir dışında herhangi bir ilişkisi olmayan dış türün dış türe vermemektedir.</span><span class="sxs-lookup"><span data-stu-id="f9730-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="f9730-125">**X DO NOT** iç içe geçmiş tür bir arabirim üye olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f9730-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="f9730-126">Birçok dilde bu tür bir yapı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f9730-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="f9730-127">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="f9730-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f9730-128">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="f9730-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9730-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9730-129">See also</span></span>

- [<span data-ttu-id="f9730-130">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f9730-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="f9730-131">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f9730-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
