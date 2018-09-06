---
title: Üye tasarımı yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1598ac63af38f1ca3e11104bc8e1cd6323d35ed
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871025"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="a1be1-102">Üye tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a1be1-102">Member Design Guidelines</span></span>
<span data-ttu-id="a1be1-103">Yöntemler, özellikler, olaylar, Oluşturucular ve alanları topluca için üyeleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a1be1-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="a1be1-104">Üyeleri, sonuçta bir framework'ün son kullanıcılara gösterilen framework işlevleri tarafından araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="a1be1-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="a1be1-105">Üyeleri sanal veya sanal olmayan, somut veya abstract, statik veya örnek olabilir ve erişilebilirlik birkaç farklı kapsamlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1be1-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="a1be1-106">Bu çeşitli inanılmaz anlamlılık sağlar ancak aynı anda framework Tasarımcısı yoluna bakım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a1be1-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="a1be1-107">Bu bölüm, herhangi bir türün üyeleri tasarlarken izlenmesi gereken temel yönergeler sunar.</span><span class="sxs-lookup"><span data-stu-id="a1be1-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1be1-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a1be1-108">In This Section</span></span>  
 [<span data-ttu-id="a1be1-109">Üye Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="a1be1-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="a1be1-110">Özellik Tasarımı</span><span class="sxs-lookup"><span data-stu-id="a1be1-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="a1be1-111">Oluşturucu Tasarımı</span><span class="sxs-lookup"><span data-stu-id="a1be1-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="a1be1-112">Olay Tasarımı</span><span class="sxs-lookup"><span data-stu-id="a1be1-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="a1be1-113">Alan Tasarımı</span><span class="sxs-lookup"><span data-stu-id="a1be1-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="a1be1-114">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a1be1-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="a1be1-115">İşleç Aşırı Yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="a1be1-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="a1be1-116">Parametre Tasarımı</span><span class="sxs-lookup"><span data-stu-id="a1be1-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="a1be1-117">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="a1be1-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a1be1-118">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="a1be1-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1be1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1be1-119">See also</span></span>

- [<span data-ttu-id="a1be1-120">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a1be1-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
