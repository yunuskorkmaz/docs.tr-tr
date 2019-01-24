---
title: Sanal üyeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: KrzysztofCwalina
ms.openlocfilehash: 4943ddcdf1bc4e3e32c8d664cbcc5c50ae3959bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543834"
---
# <a name="virtual-members"></a><span data-ttu-id="f9554-102">Sanal üyeler</span><span class="sxs-lookup"><span data-stu-id="f9554-102">Virtual Members</span></span>
<span data-ttu-id="f9554-103">Sanal üyeler, bu nedenle alt davranışını değiştirme geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="f9554-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="f9554-104">Bunlar geri çağırmaları sağladıkları genişletilebilirlik açısından oldukça benzer, ancak bunlar yürütme performans ve bellek tüketimi açısından daha iyi.</span><span class="sxs-lookup"><span data-stu-id="f9554-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="f9554-105">Ayrıca, sanal üyeleri özel bir tür var olan bir tür (özelleştirmesi) oluşturma gerektiren senaryolar daha doğal gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9554-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="f9554-106">Sanal üyeler geri çağrıları ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemlerde daha iyi gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="f9554-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="f9554-107">Sanal üyeler dezavantajı, bir sanal üye davranışını yalnızca derleme zamanında değiştirilebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="f9554-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="f9554-108">Bir geri çağırma davranışını çalışma zamanında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f9554-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="f9554-109">Geri çağırmalar (ve belki birden çok geri çağırmaları) gibi sanal üyelerini tasarlamanıza, test ve nedeni herhangi bir sanal üye çağrısı beklenmeyen şekilde geçersiz kılınabilir ve rastgele kod yürütebilir korumak yüksek maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="f9554-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="f9554-110">Ayrıca, çok daha fazla çaba tasarlama ve bunları belgeleme maliyeti daha yüksek olacak şekilde sanal üyelerinin sözleşmeyi açıkça tanımlamak için genellikle gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f9554-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="f9554-111">**X DO NOT** üyeleri sanal sürece bunu yapmak için iyi bir nedeniniz yoksa ve tasarlamak, test ve sanal üyeleri koruma ile ilgili tüm maliyetler farkında olun.</span><span class="sxs-lookup"><span data-stu-id="f9554-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="f9554-112">Bunlara uyumluluk bozup olmadan yapılabilecek değişiklikler açısından daha az forgiving sanal üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="f9554-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="f9554-113">Genellikle çağrıları sanal üyelerine satır içine alınmış olmadığından Ayrıca, sanal olmayan üyeleri yavaştır.</span><span class="sxs-lookup"><span data-stu-id="f9554-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="f9554-114">**✓ CONSIDER** yalnızca kesinlikle gerekli nedir için genişletilebilirlik sınırlama.</span><span class="sxs-lookup"><span data-stu-id="f9554-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="f9554-115">**✓ DO** korumalı erişilebilirlik ortak erişilebilirlik sanal üyeleri için tercih eder.</span><span class="sxs-lookup"><span data-stu-id="f9554-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="f9554-116">Genel üyeler genişletilebilirlik (gerekliyse) bir korumalı sanal üye çağırarak sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9554-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="f9554-117">Genel bir sınıf üyesi işlevleri doğru ortaklık kümesi söz konusu sınıfın doğrudan müşterileri için sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9554-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="f9554-118">Sanal üyeler sınıflarında geçersiz kılınacak tasarlanmıştır ve korumalı erişilebilirlik nerede kullanılabilmesi için tüm sanal genişletilebilirlik noktaları kapsamını belirlemek için harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f9554-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="f9554-119">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="f9554-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f9554-120">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="f9554-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9554-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9554-121">See also</span></span>

- [<span data-ttu-id="f9554-122">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f9554-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f9554-123">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="f9554-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
