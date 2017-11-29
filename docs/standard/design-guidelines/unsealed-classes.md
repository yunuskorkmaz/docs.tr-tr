---
title: "Korumasız sınıfları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f950d8de2681868fe28e09e4b51bd8156cd12e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unsealed-classes"></a><span data-ttu-id="3fc03-102">Korumasız sınıfları</span><span class="sxs-lookup"><span data-stu-id="3fc03-102">Unsealed Classes</span></span>
<span data-ttu-id="3fc03-103">Sealed sınıfları devralınan olamaz ve bunlar genişletilebilirlik engeller.</span><span class="sxs-lookup"><span data-stu-id="3fc03-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="3fc03-104">Buna karşılık, kaynağından devralındı sınıfları korumasız sınıfları denir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="3fc03-105">**✓ DÜŞÜNÜN** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="3fc03-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="3fc03-106">Geliştiriciler genellikle özel oluşturucular, yeni yöntemleri veya yöntemi aşırı gibi kolaylık üye eklemek amacıyla korumasız sınıflardan devralan istersiniz.</span><span class="sxs-lookup"><span data-stu-id="3fc03-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="3fc03-107">Örneğin, `System.Messaging.MessageQueue` korumasız olduğundan ve bu nedenle kullanıcıların belirli sıra yolu için varsayılan özel kuyruk oluşturmak için veya belirli senaryolar için API basitleştirmek özel yöntemler eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3fc03-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="3fc03-108">Varsayılan olarak en programlama dillerinde sınıfları korumasız ve ayrıca çerçeveleri çoğu sınıfları için önerilen varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="3fc03-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="3fc03-109">Korumasız türleri tarafından karşılanan genişletilebilirlik çok takdir framework kullanıcılar tarafından ve korumasız türleriyle ilişkili nispeten düşük test maliyetleri nedeniyle sağlamak oldukça uygun maliyetli ' dir.</span><span class="sxs-lookup"><span data-stu-id="3fc03-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="3fc03-110">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="3fc03-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3fc03-111">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="3fc03-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc03-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fc03-112">See Also</span></span>  
 [<span data-ttu-id="3fc03-113">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="3fc03-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="3fc03-114">Genişletilebilirlik için tasarlama</span><span class="sxs-lookup"><span data-stu-id="3fc03-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="3fc03-115">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="3fc03-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
