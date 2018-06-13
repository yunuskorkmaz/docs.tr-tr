---
title: Üye tasarım yönergeleri
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
ms.openlocfilehash: 1c04b431224a1d4f03e85397b854a52856e114e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571403"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="19bdc-102">Üye tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="19bdc-102">Member Design Guidelines</span></span>
<span data-ttu-id="19bdc-103">Yöntemler, özellikler, olaylar, Oluşturucular ve alanları topluca için üye olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="19bdc-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="19bdc-104">Sonuçta framework işlevselliği bir çerçeve son kullanıcılara sunulur anlamına gelir üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="19bdc-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="19bdc-105">Üyeleri sanal veya sanal olmayan, somut veya soyut, statik veya örnek olabilir ve erişilebilirlik birkaç farklı kapsamlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="19bdc-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="19bdc-106">Bu çeşitli inanılmaz anlamlılık sağlar ancak aynı anda framework Tasarımcısı bölümüne dikkat gerektirir.</span><span class="sxs-lookup"><span data-stu-id="19bdc-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="19bdc-107">Bu bölüm üyeleri herhangi bir türde tasarlarken izlenmesi gereken temel yönergeler sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19bdc-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19bdc-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="19bdc-108">In This Section</span></span>  
 [<span data-ttu-id="19bdc-109">Üye Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="19bdc-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="19bdc-110">Özellik Tasarımı</span><span class="sxs-lookup"><span data-stu-id="19bdc-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="19bdc-111">Oluşturucu Tasarımı</span><span class="sxs-lookup"><span data-stu-id="19bdc-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="19bdc-112">Olay Tasarımı</span><span class="sxs-lookup"><span data-stu-id="19bdc-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="19bdc-113">Alan Tasarımı</span><span class="sxs-lookup"><span data-stu-id="19bdc-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="19bdc-114">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="19bdc-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="19bdc-115">İşleç Aşırı Yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="19bdc-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="19bdc-116">Parametre Tasarımı</span><span class="sxs-lookup"><span data-stu-id="19bdc-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="19bdc-117">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="19bdc-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="19bdc-118">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="19bdc-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bdc-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19bdc-119">See Also</span></span>  
 [<span data-ttu-id="19bdc-120">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="19bdc-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
