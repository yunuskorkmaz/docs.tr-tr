---
title: "İç içe Geçmiş Türler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ae09df49b97cc2fe84285c3a37e1562da185f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types"></a><span data-ttu-id="840fa-102">İç içe Geçmiş Türler</span><span class="sxs-lookup"><span data-stu-id="840fa-102">Nested Types</span></span>
<span data-ttu-id="840fa-103">İç içe geçmiş tür, kendilerini kapsayan türle adlı başka bir tür kapsam içinde tanımlanan bir türüdür.</span><span class="sxs-lookup"><span data-stu-id="840fa-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="840fa-104">İç içe geçmiş tür kapsayan türü tüm üyeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="840fa-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="840fa-105">Örneğin, kendilerini kapsayan türle ve korumalı alanlarına kendilerini kapsayan türle tüm üst öğelerinden içinde tanımlanan tanımlı özel alanlara erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="840fa-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="840fa-106">Genel olarak, iç içe geçmiş türler kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="840fa-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="840fa-107">Bunun birkaç nedeni vardır.</span><span class="sxs-lookup"><span data-stu-id="840fa-107">There are several reasons for this.</span></span> <span data-ttu-id="840fa-108">Bazı geliştiriciler kavramına tam olarak aşina değildir.</span><span class="sxs-lookup"><span data-stu-id="840fa-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="840fa-109">Örneğin, bu geliştiriciler iç içe geçmiş türler değişkenleri bildirme sözdizimi ile ilgili sorun yaşayabilir.</span><span class="sxs-lookup"><span data-stu-id="840fa-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="840fa-110">İç içe geçmiş türler kapsayan kendi türleriyle aynı zamanda çok sıkı şekilde bağlı ve bu nedenle genel amaçlı türleri için uygundur değil.</span><span class="sxs-lookup"><span data-stu-id="840fa-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="840fa-111">İç içe geçmiş türler kapsayan türlerini uygulama ayrıntılarını modelleme için uygundur.</span><span class="sxs-lookup"><span data-stu-id="840fa-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="840fa-112">Son kullanıcı nadiren iç içe geçmiş tür değişkenler bildirmek olmalıdır ve açıkça iç içe geçmiş türler örneği oluşturmak neredeyse hiçbir zaman sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="840fa-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="840fa-113">Örneğin, bir koleksiyon öğesinin numaralandırıcısını o koleksiyonun iç içe geçmiş tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="840fa-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="840fa-114">Numaralandırıcılar genellikle kendilerini kapsayan türle tarafından oluşturulur ve birçok dilde foreach deyimi desteklediğinden, numaralandırıcı değişkenleri nadiren son kullanıcı tarafından bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="840fa-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="840fa-115">**✓ YAPMAK** üye erişilebilirlik semantiği istenen şekilde iç içe geçmiş tür ve dış türü arasındaki ilişkiyi olduğunda iç içe geçmiş türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="840fa-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="840fa-116">**X yok** kullanım ortak iç içe geçmiş türler, mantıksal bir gruplandırma olarak oluşturun; ad alanları için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="840fa-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="840fa-117">**KAÇININ x** herkese açık şekilde iç içe geçmiş türler açık.</span><span class="sxs-lookup"><span data-stu-id="840fa-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="840fa-118">Bunun tek istisnası, iç içe geçmiş tür değişkenler yalnızca senaryolarda nadir sınıflara veya diğer gelişmiş özelleştirme senaryoları gibi bildirilmesi gerekip gerekmediğini ' dir.</span><span class="sxs-lookup"><span data-stu-id="840fa-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="840fa-119">**X yok** türü içeren türde dışında başvurulacak olasılığı olan iç içe geçmiş türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="840fa-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="840fa-120">Örneğin, bir sınıf üzerinde tanımlı bir yönteme geçirilen enum iç içe bir sınıf türü olarak tanımlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="840fa-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="840fa-121">**X yok** istemci kodu tarafından örneğinin oluşturulması gerekirse iç içe geçmiş türler kullanın.</span><span class="sxs-lookup"><span data-stu-id="840fa-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="840fa-122">Bir türü bir public oluşturucuya varsa, iç içe olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="840fa-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="840fa-123">Bir türü örneği varsa, görünüyor türünde framework kendi başına bir yerde belirtmek için (Bu oluşturabilir, iş ile ve dış türü kullanmadan yok) ve bu nedenle iç içe değil.</span><span class="sxs-lookup"><span data-stu-id="840fa-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="840fa-124">İç türleri değil yaygın olarak yeniden kullanılabilir herhangi bir ilişki olmadan dış türü dışında dış türü yoktur.</span><span class="sxs-lookup"><span data-stu-id="840fa-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="840fa-125">**X yok** iç içe geçmiş tür bir arabirim üye olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="840fa-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="840fa-126">Birçok dilde bu tür bir yapı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="840fa-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="840fa-127">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="840fa-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="840fa-128">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="840fa-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="840fa-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="840fa-129">See Also</span></span>  
 [<span data-ttu-id="840fa-130">Türü tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="840fa-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="840fa-131">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="840fa-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
