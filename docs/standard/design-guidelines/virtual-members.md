---
description: 'Daha fazla bilgi edinin: sanal Üyeler'
title: Sanal Üyeler
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 7618686764fb3a24ef53e5168b871366b7ffb5bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641791"
---
# <a name="virtual-members"></a><span data-ttu-id="08260-103">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="08260-103">Virtual Members</span></span>

<span data-ttu-id="08260-104">Sanal Üyeler geçersiz kılınabilir, böylece alt sınıfın davranışı değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="08260-104">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="08260-105">Bunlar, sağladıkları genişletilebilirlik açısından geri çağırmaları oldukça benzerdir ancak yürütme performansı ve bellek tüketimi açısından daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="08260-105">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="08260-106">Ayrıca, sanal Üyeler var olan türde (özelleşme) özel bir tür oluşturulmasını gerektiren senaryolarda daha doğal bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="08260-106">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="08260-107">Sanal Üyeler geri çağırmaları ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemlerle daha iyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="08260-107">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="08260-108">Sanal üyelerin ana dezavantajı, sanal bir üyenin davranışının yalnızca derleme sırasında değiştirilebilmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="08260-108">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="08260-109">Bir geri aramanın davranışı çalışma zamanında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="08260-109">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="08260-110">Bir sanal üyeye yapılan herhangi bir çağrı öngörülemeyen yollarla geçersiz kılınabileceğinden ve rastgele kod yürütebildiğinden, geri çağırmalar (ve geri çağırmaların daha fazlası) gibi sanal Üyeler tasarım, test ve bakım açısından maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="08260-110">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="08260-111">Ayrıca, sanal üyelerin sözleşmesini açıkça tanımlamak için çok daha fazla çaba gerekir. bu nedenle, bunları tasarlama ve belgeleme maliyeti daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="08260-111">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="08260-112">❌ Bunu yapmak için iyi bir nedeniniz olmadığı için, Üyeler sanal yapmayın ve sanal üyelerin tasarlanması, sınanması ve saklanması ile ilgili tüm maliyetlerden haberdar olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08260-112">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="08260-113">Sanal üyeler, uyumluluk bozmadan bu kullanıcılara yapılabilecek değişikliklere göre daha az yasaklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="08260-113">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="08260-114">Ayrıca bunlar sanal olmayan üyelerden daha yavaştır, ancak sanal üyelere yapılan çağrılar satır içine alınmadı.</span><span class="sxs-lookup"><span data-stu-id="08260-114">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="08260-115">✔️ genişletilebilirliği yalnızca kesinlikle gerekli olan şekilde sınırlandırmaya yarar.</span><span class="sxs-lookup"><span data-stu-id="08260-115">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="08260-116">✔️, sanal üyeler için genel erişilebilirlik üzerinden korumalı erişilebilirliği tercih eder.</span><span class="sxs-lookup"><span data-stu-id="08260-116">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="08260-117">Ortak Üyeler korumalı bir sanal üyeye çağırarak genişletilebilirlik (gerekliyse) sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="08260-117">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="08260-118">Bir sınıfın ortak üyeleri, bu sınıfın doğrudan tüketicilere yönelik doğru işlevsellik kümesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="08260-118">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="08260-119">Sanal üyeler, alt sınıflarda geçersiz kılınabilecek şekilde tasarlanmıştır ve korumalı erişilebilirlik, tüm sanal genişletilebilirlik noktalarını, kullanılabilecekleri yere kapsamı için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="08260-119">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="08260-120">*Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="08260-120">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="08260-121">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="08260-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="08260-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08260-122">See also</span></span>

- [<span data-ttu-id="08260-123">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="08260-123">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="08260-124">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="08260-124">Designing for Extensibility</span></span>](designing-for-extensibility.md)
