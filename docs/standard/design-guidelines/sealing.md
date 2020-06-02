---
title: Mühürleme
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: a54c68efb4ac114fe0e5a5712eca877bef35c103
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290116"
---
# <a name="sealing"></a><span data-ttu-id="55743-102">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="55743-102">Sealing</span></span>
<span data-ttu-id="55743-103">Nesne yönelimli çerçevelerin özelliklerinden biri, geliştiricilerin bunları çerçeve tasarımcıları tarafından beklenmeyen yollarla genişletebileceği ve özelleştirebilleridir.</span><span class="sxs-lookup"><span data-stu-id="55743-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="55743-104">Bu, Genişletilebilir tasarımın güç ve tehlike ' dir.</span><span class="sxs-lookup"><span data-stu-id="55743-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="55743-105">Çatısını tasarladığınızda, bu, bu nedenle, gerektiğinde genişletilebilirlik için dikkatle tasarlamak ve çok önemli olduğunda genişletilebilirliği kısıtlamak için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="55743-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="55743-106">Genişletilebilirlik 'in mühürlediği güçlü bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="55743-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="55743-107">Sınıfı ya da tek üyeleri mühürleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55743-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="55743-108">Bir sınıfı mühürleyen, kullanıcıların sınıfından devralmasını önler.</span><span class="sxs-lookup"><span data-stu-id="55743-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="55743-109">Bir üyeyi mühürleyen, kullanıcıların belirli bir üyeyi geçersiz kılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="55743-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="55743-110">❌Bunu yapmak için iyi bir neden olmadan sınıfları mühürlemeyin.</span><span class="sxs-lookup"><span data-stu-id="55743-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="55743-111">Bir sınıfı mühürleyen bir genişletilebilirlik senaryosunu düşünmek iyi bir neden değil.</span><span class="sxs-lookup"><span data-stu-id="55743-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="55743-112">Kullanışlı Üyeler ekleme gibi belirgin olmayan çeşitli nedenlerle sınıflardan devralması gibi Framework kullanıcıları.</span><span class="sxs-lookup"><span data-stu-id="55743-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="55743-113">Kullanıcıların bir türden kalýtýmla devralması için açık olmayan nedenler örnekleri için bkz. [korumasız sınıflar](unsealed-classes.md) .</span><span class="sxs-lookup"><span data-stu-id="55743-113">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="55743-114">Bir sınıfı mühürleyen olası nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="55743-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="55743-115">Sınıfı statik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="55743-115">The class is a static class.</span></span> <span data-ttu-id="55743-116">Bkz. [statik sınıf tasarımı](static-class.md).</span><span class="sxs-lookup"><span data-stu-id="55743-116">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="55743-117">Sınıfı, devralınan korunan üyelerde güvenlik duyarlı gizli dizileri depolar.</span><span class="sxs-lookup"><span data-stu-id="55743-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="55743-118">Sınıf birçok sanal üyeyi devralır ve tek tek mühürlemek, sınıfın korumasız bırakılması avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="55743-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="55743-119">Sınıfı çok hızlı çalışma zamanı araması gerektiren bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="55743-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="55743-120">Sealed öznitelikleri, korumasız olanlardan biraz daha yüksek performans düzeylerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="55743-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="55743-121">Bkz. [öznitelikler](attributes.md).</span><span class="sxs-lookup"><span data-stu-id="55743-121">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="55743-122">❌Korumalı türler üzerinde korumalı veya sanal üye bildirme.</span><span class="sxs-lookup"><span data-stu-id="55743-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="55743-123">Tanım olarak, korumalı türler öğesinden devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="55743-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="55743-124">Bu, korumalı türlerdeki korunan üyelerin çağrılabilmesi ve korumalı türlerde Sanal yöntemlerin geçersiz kılınamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55743-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="55743-125">✔️, geçersiz kıldığınız üyeleri mühürden DEĞERLENDIRIN.</span><span class="sxs-lookup"><span data-stu-id="55743-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="55743-126">Sanal üyelere ( [sanal Üyelerde](virtual-members.md)ele alınan) neden olan sorunlar, çok daha az bir ölçüde geçersiz kılmalara de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="55743-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="55743-127">Bir geçersiz kılmayı mühürleyen, devralma hiyerarşisindeki noktadan itibaren bu sorunlardan kalkan.</span><span class="sxs-lookup"><span data-stu-id="55743-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="55743-128">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="55743-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="55743-129">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="55743-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="55743-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55743-130">See also</span></span>

- [<span data-ttu-id="55743-131">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="55743-131">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="55743-132">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="55743-132">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="55743-133">Korumasız sınıflar</span><span class="sxs-lookup"><span data-stu-id="55743-133">Unsealed Classes</span></span>](unsealed-classes.md)
