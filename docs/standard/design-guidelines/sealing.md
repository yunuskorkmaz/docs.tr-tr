---
title: Mühürleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8c445de44a69f6c0cb1eaefa0e59d682288318
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44336920"
---
# <a name="sealing"></a><span data-ttu-id="a28bf-102">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="a28bf-102">Sealing</span></span>
<span data-ttu-id="a28bf-103">Nesne yönelimli çerçeveleri özelliklerinin geliştiriciler genişletmek ve framework Designer'ların beklenmedik şekilde özelleştirin biridir.</span><span class="sxs-lookup"><span data-stu-id="a28bf-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="a28bf-104">Güç ve Genişletilebilir tasarım tehlike budur.</span><span class="sxs-lookup"><span data-stu-id="a28bf-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="a28bf-105">Framework'ünüzün tasarlarken, bu nedenle olduğu için genişletilebilirlik, istendiğinde dikkatlice tasarlayın ve tehlikeli olduğunda genişletilebilirlik sınırlamak için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a28bf-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="a28bf-106">Genişletilebilirlik engelleyen güçlü bir mekanizma mühürleme.</span><span class="sxs-lookup"><span data-stu-id="a28bf-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="a28bf-107">Sınıf veya bireysel üyelere adımını.</span><span class="sxs-lookup"><span data-stu-id="a28bf-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="a28bf-108">Bir sınıf mühürleme kullanıcıların sınıftan devralmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="a28bf-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="a28bf-109">Üye mühürleme, kullanıcıların belirli bir üye geçersiz kılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="a28bf-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="a28bf-110">**X DO NOT** sınıfları Bunu yapmak için iyi bir neden olmadan mühürlemek.</span><span class="sxs-lookup"><span data-stu-id="a28bf-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="a28bf-111">Bir sınıf bir genişletilebilirlik senaryo düşündüğünüz olamaz çünkü mühürleme geçerli bir nedeniniz değil.</span><span class="sxs-lookup"><span data-stu-id="a28bf-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="a28bf-112">Framework kullanıcılarını kolaylık üyeleri ekleme gibi çeşitli nonobvious nedeniyle sınıflardan devralmasına izin ister.</span><span class="sxs-lookup"><span data-stu-id="a28bf-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="a28bf-113">Bkz: [Mühürsüz sınıflar](../../../docs/standard/design-guidelines/unsealed-classes.md) nonobvious nedenlerden örnekler için kullanıcıların bir türden devralmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="a28bf-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="a28bf-114">Bir sınıf mühürleme için iyi nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a28bf-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="a28bf-115">Sınıfı statik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="a28bf-115">The class is a static class.</span></span> <span data-ttu-id="a28bf-116">Bkz: [statik sınıf tasarımı](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="a28bf-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="a28bf-117">Sınıfı, güvenlik açısından duyarlı gizli dizileri devralınan korunan üyeleri depolar.</span><span class="sxs-lookup"><span data-stu-id="a28bf-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="a28bf-118">Sınıf çok sayıda sanal üyelerini devralır ve ayrı ayrı mühürleme maliyeti korumasız sınıfı bırakmanın basıyor.</span><span class="sxs-lookup"><span data-stu-id="a28bf-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="a28bf-119">Sınıf çok hızlı çalışma zamanı arama gerektiren bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="a28bf-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="a28bf-120">Korumalı öznitelikleri korumasız yapılandırılanlardan biraz daha yüksek performans düzeyine sahip.</span><span class="sxs-lookup"><span data-stu-id="a28bf-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="a28bf-121">bkz: [öznitelikleri](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a28bf-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="a28bf-122">**X DO NOT** korumalı türlerde korunan veya sanal üyeleri bildirme.</span><span class="sxs-lookup"><span data-stu-id="a28bf-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="a28bf-123">Tanımı gereği, mühürlenmiş türler öğesinden devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="a28bf-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="a28bf-124">Yani mühürlenmiş türler üzerindeki korunan üyeleri çağrılamaz ve mühürlenmiş türler üzerindeki sanal yöntemleri geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="a28bf-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="a28bf-125">**✓ CONSIDER** kılmanız üyeleri mühürleme.</span><span class="sxs-lookup"><span data-stu-id="a28bf-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="a28bf-126">Sanal üye eklemesini kaynaklanan sorunları (ele [sanal üyeleri](../../../docs/standard/design-guidelines/virtual-members.md)) ancak biraz daha düşük bir düzeyde de geçersiz kılmalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a28bf-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="a28bf-127">Bir geçersiz kılma mühürleme, devralma hiyerarşisinde o noktadan itibaren bu sorunlardan ayrıntılarından korur.</span><span class="sxs-lookup"><span data-stu-id="a28bf-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="a28bf-128">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="a28bf-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a28bf-129">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="a28bf-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28bf-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a28bf-130">See also</span></span>

- [<span data-ttu-id="a28bf-131">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a28bf-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="a28bf-132">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="a28bf-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [<span data-ttu-id="a28bf-133">Mühürsüz Sınıflar</span><span class="sxs-lookup"><span data-stu-id="a28bf-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
