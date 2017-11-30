---
title: "Üye tasarım yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5df4ad5f6c947d8b3bf62c3bf7eb8426419e5f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="member-design-guidelines"></a><span data-ttu-id="ae814-102">Üye tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ae814-102">Member Design Guidelines</span></span>
<span data-ttu-id="ae814-103">Yöntemler, özellikler, olaylar, Oluşturucular ve alanları topluca için üye olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ae814-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="ae814-104">Sonuçta framework işlevselliği bir çerçeve son kullanıcılara sunulur anlamına gelir üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="ae814-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="ae814-105">Üyeleri sanal veya sanal olmayan, somut veya soyut, statik veya örnek olabilir ve erişilebilirlik birkaç farklı kapsamlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae814-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="ae814-106">Bu çeşitli inanılmaz anlamlılık sağlar ancak aynı anda framework Tasarımcısı bölümüne dikkat gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ae814-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="ae814-107">Bu bölüm üyeleri herhangi bir türde tasarlarken izlenmesi gereken temel yönergeler sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae814-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae814-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ae814-108">In This Section</span></span>  
 [<span data-ttu-id="ae814-109">Üye aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="ae814-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="ae814-110">Özellik Tasarım</span><span class="sxs-lookup"><span data-stu-id="ae814-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="ae814-111">Oluşturucu tasarım</span><span class="sxs-lookup"><span data-stu-id="ae814-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="ae814-112">Olay tasarım</span><span class="sxs-lookup"><span data-stu-id="ae814-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="ae814-113">Alan tasarım</span><span class="sxs-lookup"><span data-stu-id="ae814-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="ae814-114">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ae814-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="ae814-115">İşleç aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="ae814-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="ae814-116">Parametre tasarım</span><span class="sxs-lookup"><span data-stu-id="ae814-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="ae814-117">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ae814-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ae814-118">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="ae814-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae814-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae814-119">See Also</span></span>  
 [<span data-ttu-id="ae814-120">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ae814-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
