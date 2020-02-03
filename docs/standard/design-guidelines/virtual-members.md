---
title: Sanal Üyeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 8ed519a01162056151d8ae6398c0d06495911afd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743532"
---
# <a name="virtual-members"></a><span data-ttu-id="ed45e-102">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="ed45e-102">Virtual Members</span></span>
<span data-ttu-id="ed45e-103">Sanal Üyeler geçersiz kılınabilir, böylece alt sınıfın davranışı değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ed45e-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="ed45e-104">Bunlar, sağladıkları genişletilebilirlik açısından geri çağırmaları oldukça benzerdir ancak yürütme performansı ve bellek tüketimi açısından daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="ed45e-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="ed45e-105">Ayrıca, sanal Üyeler var olan türde (özelleşme) özel bir tür oluşturulmasını gerektiren senaryolarda daha doğal bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ed45e-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="ed45e-106">Sanal Üyeler geri çağırmaları ve olayları daha iyi gerçekleştirir, ancak sanal olmayan yöntemlerle daha iyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="ed45e-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="ed45e-107">Sanal üyelerin ana dezavantajı, sanal bir üyenin davranışının yalnızca derleme sırasında değiştirilebilmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed45e-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="ed45e-108">Bir geri aramanın davranışı çalışma zamanında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ed45e-108">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="ed45e-109">Bir sanal üyeye yapılan herhangi bir çağrı öngörülemeyen yollarla geçersiz kılınabileceğinden ve rastgele kod yürütebildiğinden, geri çağırmalar (ve geri çağırmaların daha fazlası) gibi sanal Üyeler tasarım, test ve bakım açısından maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="ed45e-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="ed45e-110">Ayrıca, sanal üyelerin sözleşmesini açıkça tanımlamak için çok daha fazla çaba gerekir. bu nedenle, bunları tasarlama ve belgeleme maliyeti daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="ed45e-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="ed45e-111">❌, bunu yapmak için iyi bir nedeniniz yoksa, sanal üyeleri tasarlama, test etme ve sürdürme ile ilgili tüm maliyetlerden haberdar olmanız durumunda, Üyeler sanal yapmayın.</span><span class="sxs-lookup"><span data-stu-id="ed45e-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="ed45e-112">Sanal üyeler, uyumluluk bozmadan bu kullanıcılara yapılabilecek değişikliklere göre daha az yasaklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed45e-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="ed45e-113">Ayrıca bunlar sanal olmayan üyelerden daha yavaştır, ancak sanal üyelere yapılan çağrılar satır içine alınmadı.</span><span class="sxs-lookup"><span data-stu-id="ed45e-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="ed45e-114">✔️ genişletilebilirliği yalnızca kesinlikle gerekli olan şekilde sınırlandırmaya yarar.</span><span class="sxs-lookup"><span data-stu-id="ed45e-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="ed45e-115">✔️, sanal üyeler için genel erişilebilirlik üzerinden korumalı erişilebilirliği tercih eder.</span><span class="sxs-lookup"><span data-stu-id="ed45e-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="ed45e-116">Ortak Üyeler korumalı bir sanal üyeye çağırarak genişletilebilirlik (gerekliyse) sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed45e-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="ed45e-117">Bir sınıfın ortak üyeleri, bu sınıfın doğrudan tüketicilere yönelik doğru işlevsellik kümesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed45e-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="ed45e-118">Sanal üyeler, alt sınıflarda geçersiz kılınabilecek şekilde tasarlanmıştır ve korumalı erişilebilirlik, tüm sanal genişletilebilirlik noktalarını, kullanılabilecekleri yere kapsamı için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ed45e-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="ed45e-119">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ed45e-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ed45e-120">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="ed45e-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ed45e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed45e-121">See also</span></span>

- [<span data-ttu-id="ed45e-122">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ed45e-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ed45e-123">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="ed45e-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
