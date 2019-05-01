---
title: Korumalı Üyeler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
author: KrzysztofCwalina
ms.openlocfilehash: 7d940f10799df2efc6c6d031781e1ef7cf777dd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937403"
---
# <a name="protected-members"></a><span data-ttu-id="4a5de-102">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="4a5de-102">Protected Members</span></span>
<span data-ttu-id="4a5de-103">Korumalı üyeler başlarına herhangi bir genişletilebilirlik sağlamaz, ancak bunlar sınıflara aracılığıyla genişletilebilirlik daha güçlü hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a5de-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="4a5de-104">Ana ortak arabirim gereksiz derecede karmaşık olmadan Gelişmiş özelleştirme seçeneklerini göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a5de-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="4a5de-105">Framework tasarımcıları "korumalı" adı yanlış bir güvenlik fikir verebilir çünkü korumalı üyeleri ile dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a5de-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="4a5de-106">Herkesin alt korumasız bir sınıf ve korunan üyeleri için mümkün ve bu nedenle aynı korumalı üyeler için kullanılan genel üyeler için savunma kodlama uygulamalarını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4a5de-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="4a5de-107">**✓ CONSIDER** kullanarak korumalı üyeler için Gelişmiş özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="4a5de-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="4a5de-108">**✓ DO** korumalı üyeleri korumasız sınıflarında güvenlik, belgelerine ve uyumluluk analiz amacıyla genel olarak ele alın.</span><span class="sxs-lookup"><span data-stu-id="4a5de-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="4a5de-109">Herhangi bir sınıftan ve korumalı üyelere erişim.</span><span class="sxs-lookup"><span data-stu-id="4a5de-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="4a5de-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="4a5de-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4a5de-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="4a5de-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5de-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a5de-112">See also</span></span>

- [<span data-ttu-id="4a5de-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4a5de-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="4a5de-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="4a5de-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
