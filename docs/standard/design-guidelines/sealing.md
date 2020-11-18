---
title: Mühürleme
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 29023ad431f9d05caf44e59f66eccee24bfa0433
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828692"
---
# <a name="sealing"></a><span data-ttu-id="d0832-102">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="d0832-102">Sealing</span></span>
<span data-ttu-id="d0832-103">Nesne yönelimli çerçevelerin özelliklerinden biri, geliştiricilerin bunları çerçeve tasarımcıları tarafından beklenmeyen yollarla genişletebileceği ve özelleştirebilleridir.</span><span class="sxs-lookup"><span data-stu-id="d0832-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="d0832-104">Bu, Genişletilebilir tasarımın güç ve tehlike ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0832-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="d0832-105">Çatısını tasarladığınızda, bu, bu nedenle, gerektiğinde genişletilebilirlik için dikkatle tasarlamak ve çok önemli olduğunda genişletilebilirliği kısıtlamak için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d0832-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="d0832-106">Genişletilebilirlik 'in mühürlediği güçlü bir mekanizma.</span><span class="sxs-lookup"><span data-stu-id="d0832-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="d0832-107">Sınıfı ya da tek üyeleri mühürleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0832-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="d0832-108">Bir sınıfı mühürleyen, kullanıcıların sınıfından devralmasını önler.</span><span class="sxs-lookup"><span data-stu-id="d0832-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="d0832-109">Bir üyeyi mühürleyen, kullanıcıların belirli bir üyeyi geçersiz kılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="d0832-109">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="d0832-110">❌ Bunu yapmak için iyi bir neden olmadan sınıfları mühürlemeyin.</span><span class="sxs-lookup"><span data-stu-id="d0832-110">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="d0832-111">Bir sınıfı mühürleyen bir genişletilebilirlik senaryosunu düşünmek iyi bir neden değil.</span><span class="sxs-lookup"><span data-stu-id="d0832-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="d0832-112">Kullanışlı Üyeler ekleme gibi belirgin olmayan çeşitli nedenlerle sınıflardan devralması gibi Framework kullanıcıları.</span><span class="sxs-lookup"><span data-stu-id="d0832-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="d0832-113">Kullanıcıların bir türden kalýtýmla devralması için açık olmayan nedenler örnekleri için bkz. [korumasız sınıflar](unsealed-classes.md) .</span><span class="sxs-lookup"><span data-stu-id="d0832-113">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="d0832-114">Bir sınıfı mühürleyen olası nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d0832-114">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="d0832-115">Sınıfı statik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d0832-115">The class is a static class.</span></span> <span data-ttu-id="d0832-116">Bkz. [statik sınıf tasarımı](static-class.md).</span><span class="sxs-lookup"><span data-stu-id="d0832-116">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="d0832-117">Sınıfı, devralınan korunan üyelerde güvenlik duyarlı gizli dizileri depolar.</span><span class="sxs-lookup"><span data-stu-id="d0832-117">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="d0832-118">Sınıf birçok sanal üyeyi devralır ve tek tek mühürlemek, sınıfın korumasız bırakılması avantajlarından yararlanır.</span><span class="sxs-lookup"><span data-stu-id="d0832-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="d0832-119">Sınıfı çok hızlı çalışma zamanı araması gerektiren bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="d0832-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="d0832-120">Sealed öznitelikleri, korumasız olanlardan biraz daha yüksek performans düzeylerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d0832-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="d0832-121">Bkz. [öznitelikler](attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d0832-121">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="d0832-122">❌ Korumalı türler üzerinde korumalı veya sanal üye bildirme.</span><span class="sxs-lookup"><span data-stu-id="d0832-122">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="d0832-123">Tanım olarak, korumalı türler öğesinden devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="d0832-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="d0832-124">Bu, korumalı türlerdeki korunan üyelerin çağrılabilmesi ve korumalı türlerde Sanal yöntemlerin geçersiz kılınamayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0832-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="d0832-125">✔️, geçersiz kıldığınız üyeleri mühürden DEĞERLENDIRIN.</span><span class="sxs-lookup"><span data-stu-id="d0832-125">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="d0832-126">Sanal üyelere ( [sanal Üyelerde](virtual-members.md)ele alınan) neden olan sorunlar, çok daha az bir ölçüde geçersiz kılmalara de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d0832-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="d0832-127">Bir geçersiz kılmayı mühürleyen, devralma hiyerarşisindeki noktadan itibaren bu sorunlardan kalkan.</span><span class="sxs-lookup"><span data-stu-id="d0832-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="d0832-128">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="d0832-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d0832-129">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="d0832-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d0832-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0832-130">See also</span></span>

- [<span data-ttu-id="d0832-131">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d0832-131">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d0832-132">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="d0832-132">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="d0832-133">Korumasız sınıflar</span><span class="sxs-lookup"><span data-stu-id="d0832-133">Unsealed Classes</span></span>](unsealed-classes.md)
