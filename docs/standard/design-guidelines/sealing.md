---
title: "Mühürleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39bb29d36b6d81464b1213ebc0bf7aee6ceb5713
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="sealing"></a><span data-ttu-id="87743-102">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="87743-102">Sealing</span></span>
<span data-ttu-id="87743-103">Nesne odaklı çerçeveleri özelliklerini geliştiriciler genişletmek ve framework tasarımcıların beklenmedik şekilde özelleştirin biridir.</span><span class="sxs-lookup"><span data-stu-id="87743-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="87743-104">Güç ve Genişletilebilir tasarımının tehlike budur.</span><span class="sxs-lookup"><span data-stu-id="87743-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="87743-105">Framework'ünüzün tasarlarken, bu nedenle, olduğu, istendiğinde Genişletilebilirliğe dikkatle tasarlamak için ve genişletilebilirlik tehlikeli olduğunda sınırlamak için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="87743-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="87743-106">Genişletilebilirlik engeller güçlü bir mekanizma mühürleme.</span><span class="sxs-lookup"><span data-stu-id="87743-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="87743-107">Sınıf veya tek tek üyeleri korumaya.</span><span class="sxs-lookup"><span data-stu-id="87743-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="87743-108">Bir sınıf mühürleme kullanıcıların sınıfından devralan engeller.</span><span class="sxs-lookup"><span data-stu-id="87743-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="87743-109">Üye mühürleme, kullanıcıların belirli bir üye önlemiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="87743-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="87743-110">**X yok** sınıfları Bunu yapmak için iyi bir neden olmadan mühürlemek.</span><span class="sxs-lookup"><span data-stu-id="87743-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="87743-111">Bir sınıf bir genişletilebilirlik senaryo düşündüğünüz yapılamıyor çünkü mühürleme iyi bir nedenle değil.</span><span class="sxs-lookup"><span data-stu-id="87743-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="87743-112">Framework kullanıcılar kolaylık üye ekleme gibi çeşitli nonobvious nedeniyle sınıflardan devralmak ister.</span><span class="sxs-lookup"><span data-stu-id="87743-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="87743-113">Bkz: [korumasız sınıfları](../../../docs/standard/design-guidelines/unsealed-classes.md) nonobvious nedenleri örnekleri için kullanıcıları bir türünden devralan istiyor.</span><span class="sxs-lookup"><span data-stu-id="87743-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="87743-114">Bir sınıf mühürleme iyi nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="87743-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="87743-115">Sınıfı statik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="87743-115">The class is a static class.</span></span> <span data-ttu-id="87743-116">Bkz: [statik sınıf tasarımı](../../../docs/standard/design-guidelines/static-class.md).</span><span class="sxs-lookup"><span data-stu-id="87743-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="87743-117">Sınıfı, güvenlik açısından duyarlı gizli devralınan korunan üyeleri depolar.</span><span class="sxs-lookup"><span data-stu-id="87743-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="87743-118">Çok sayıda sanal üye sınıfı devralır ve tek tek mühürleme maliyetini korumasız sınıfı bırakarak, ağır basıyor.</span><span class="sxs-lookup"><span data-stu-id="87743-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="87743-119">Sınıf çok hızlı çalışma zamanı arama gerektiren bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="87743-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="87743-120">Korumalı öznitelikleri korumasız olanları daha biraz daha yüksek performans düzeyine sahip.</span><span class="sxs-lookup"><span data-stu-id="87743-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="87743-121">Bkz: [öznitelikleri](../../../docs/standard/design-guidelines/attributes.md).</span><span class="sxs-lookup"><span data-stu-id="87743-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="87743-122">**X yok** korumalı türlerde korunan veya sanal üyeleri bildirme.</span><span class="sxs-lookup"><span data-stu-id="87743-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="87743-123">Tanımı gereği, korumalı türlerde kaynağından devralındı olamaz.</span><span class="sxs-lookup"><span data-stu-id="87743-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="87743-124">Bu, korumalı türlerde korunan üyeleri çağrılamaz ve korumalı türlerde sanal yöntemleri geçersiz kılınamaz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="87743-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="87743-125">**✓ DÜŞÜNÜN** kılmanız üyeleri mühürleme.</span><span class="sxs-lookup"><span data-stu-id="87743-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="87743-126">Sanal üyeler Tanıtımı sonuçlanabilir sorunları (ele [sanal üyeler](../../../docs/standard/design-guidelines/virtual-members.md)) biraz daha düşük bir derecede rağmen de geçersiz kılmaları uygulamak.</span><span class="sxs-lookup"><span data-stu-id="87743-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="87743-127">Bir geçersiz kılma korumalı hale getirilmesiyle, devralma hiyerarşisinde o noktadan başlayarak bu sorunlardan ayrıntılarından korur.</span><span class="sxs-lookup"><span data-stu-id="87743-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="87743-128">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="87743-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="87743-129">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="87743-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87743-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87743-130">See Also</span></span>  
 [<span data-ttu-id="87743-131">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="87743-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="87743-132">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="87743-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="87743-133">Mühürsüz Sınıflar</span><span class="sxs-lookup"><span data-stu-id="87743-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
