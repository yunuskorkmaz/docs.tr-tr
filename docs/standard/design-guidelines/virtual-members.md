---
title: Sanal üyeler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1b7abe1dbeb7f4888dd8ee4001b410cc583935c4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="virtual-members"></a><span data-ttu-id="b0ce0-102">Sanal üyeler</span><span class="sxs-lookup"><span data-stu-id="b0ce0-102">Virtual Members</span></span>
<span data-ttu-id="b0ce0-103">Sanal üyeler, bu nedenle bir alt davranışını değiştirme geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="b0ce0-104">Geri aramalar sağladıkları genişletilebilirlik bakımından oldukça benzer, ancak yürütme performans ve bellek tüketimi bakımından daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="b0ce0-105">Ayrıca, sanal üyeleri bir özel tür mevcut bir türle (uzmanlık) oluşturma gerektiren senaryolarda daha doğal eşitleyerek.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="b0ce0-106">Sanal üyeler geri aramalar ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemler daha iyi gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="b0ce0-107">Sanal üyeler ana dezavantajı sanal üyesi davranışını yalnızca derleme zamanında değiştirilmesi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="b0ce0-108">Bir geri çağırma davranışını çalışma zamanında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="b0ce0-109">Geri aramalar (ve belki de birden çok geri aramalar) gibi sanal üyeler tasarlamak, test ve çünkü sanal üyesi için herhangi bir çağrı beklenmedik şekilde geçersiz kılınabilir ve rasgele kod yürütebilir korumak maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="b0ce0-110">Ayrıca, çok daha fazla çaba genellikle tasarlama ve bunları belgeleme maliyeti daha yüksek olacak şekilde sözleşme sanal üyeleri açıkça tanımlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="b0ce0-111">**X yok** üyeleri sanal sürece bunu yapmak için iyi bir nedeniniz yoksa ve tasarlamak, test ve sanal üyeleri koruma ile ilgili tüm maliyetler farkında olun.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="b0ce0-112">Bunlara uyumluluk bozmadan yapılabilir değişiklikler açısından daha az forgiving sanal üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="b0ce0-113">Çoğunlukla çağrıları sanal üyelerine içermesinden olmadığından Ayrıca, kullanıcılar sanal olmayan üyeler yavaştır.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="b0ce0-114">**✓ DÜŞÜNÜN** yalnızca kesinlikle gerekli nedir için genişletilebilirlik sınırlama.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="b0ce0-115">**✓ YAPMAK** korumalı erişilebilirlik ortak erişilebilirlik sanal üyeleri için tercih eder.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="b0ce0-116">Genel üyeler genişletilebilirlik (gerekliyse) korumalı sanal üyesi çağırarak sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="b0ce0-117">Bir sınıfın ortak üyelerine o sınıfın doğrudan Tüketiciler için işlev sağ kümesi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="b0ce0-118">Sanal üyeler sınıflarında geçersiz kılınmak üzere tasarlanmıştır ve korumalı erişilebilirlik burada kullanılabilmeleri için tüm sanal genişletilebilirlik noktaları kapsam için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="b0ce0-119">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="b0ce0-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b0ce0-120">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="b0ce0-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ce0-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-121">See Also</span></span>  
 [<span data-ttu-id="b0ce0-122">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b0ce0-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b0ce0-123">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="b0ce0-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
