---
title: Üye Tasarımı Yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
author: KrzysztofCwalina
ms.openlocfilehash: d7023bbe59eb3590af47952a2fe24c5f40b3ca68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945528"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="d68e9-102">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d68e9-102">Member Design Guidelines</span></span>
<span data-ttu-id="d68e9-103">Yöntemler, özellikler, olaylar, Oluşturucular ve alanları topluca için üyeleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d68e9-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="d68e9-104">Üyeleri, sonuçta bir framework'ün son kullanıcılara gösterilen framework işlevleri tarafından araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="d68e9-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="d68e9-105">Üyeleri sanal veya sanal olmayan, somut veya abstract, statik veya örnek olabilir ve erişilebilirlik birkaç farklı kapsamlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="d68e9-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="d68e9-106">Bu çeşitli inanılmaz anlamlılık sağlar ancak aynı anda framework Tasarımcısı yoluna bakım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d68e9-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="d68e9-107">Bu bölüm, herhangi bir türün üyeleri tasarlarken izlenmesi gereken temel yönergeler sunar.</span><span class="sxs-lookup"><span data-stu-id="d68e9-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d68e9-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d68e9-108">In This Section</span></span>  
 [<span data-ttu-id="d68e9-109">Üye Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="d68e9-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="d68e9-110">Özellik Tasarımı</span><span class="sxs-lookup"><span data-stu-id="d68e9-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="d68e9-111">Oluşturucu Tasarımı</span><span class="sxs-lookup"><span data-stu-id="d68e9-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="d68e9-112">Olay Tasarımı</span><span class="sxs-lookup"><span data-stu-id="d68e9-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="d68e9-113">Alan Tasarımı</span><span class="sxs-lookup"><span data-stu-id="d68e9-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="d68e9-114">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="d68e9-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="d68e9-115">İşleç Aşırı Yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="d68e9-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="d68e9-116">Parametre Tasarımı</span><span class="sxs-lookup"><span data-stu-id="d68e9-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="d68e9-117">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="d68e9-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d68e9-118">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="d68e9-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68e9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d68e9-119">See also</span></span>

- [<span data-ttu-id="d68e9-120">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d68e9-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
