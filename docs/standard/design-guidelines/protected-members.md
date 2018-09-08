---
title: Korumalı üyeler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4574dffc3f9dd1b60d655bfde33a4ddc1a81d350
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199745"
---
# <a name="protected-members"></a><span data-ttu-id="6e1d0-102">Korumalı üyeler</span><span class="sxs-lookup"><span data-stu-id="6e1d0-102">Protected Members</span></span>
<span data-ttu-id="6e1d0-103">Korumalı üyeler başlarına herhangi bir genişletilebilirlik sağlamaz, ancak bunlar sınıflara aracılığıyla genişletilebilirlik daha güçlü hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="6e1d0-104">Ana ortak arabirim gereksiz derecede karmaşık olmadan Gelişmiş özelleştirme seçeneklerini göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="6e1d0-105">Framework tasarımcıları "korumalı" adı yanlış bir güvenlik fikir verebilir çünkü korumalı üyeleri ile dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="6e1d0-106">Herkesin alt korumasız bir sınıf ve korunan üyeleri için mümkün ve bu nedenle aynı korumalı üyeler için kullanılan genel üyeler için savunma kodlama uygulamalarını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="6e1d0-107">**✓ CONSIDER** kullanarak korumalı üyeler için Gelişmiş özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="6e1d0-108">**✓ DO** korumalı üyeleri korumasız sınıflarında güvenlik, belgelerine ve uyumluluk analiz amacıyla genel olarak ele alın.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="6e1d0-109">Herhangi bir sınıftan ve korumalı üyelere erişim.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="6e1d0-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="6e1d0-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6e1d0-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="6e1d0-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1d0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e1d0-112">See also</span></span>

- [<span data-ttu-id="6e1d0-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6e1d0-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="6e1d0-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="6e1d0-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
