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
ms.openlocfilehash: 14ef02a760c9d4b77fe058334baffd63fcf29cfd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709107"
---
# <a name="protected-members"></a><span data-ttu-id="e0e93-102">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="e0e93-102">Protected Members</span></span>
<span data-ttu-id="e0e93-103">Kendilerine göre korunan Üyeler herhangi bir genişletilebilirlik sağlamaz, ancak altsınıflama ile daha güçlü genişletilebilirlik yapabilir.</span><span class="sxs-lookup"><span data-stu-id="e0e93-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="e0e93-104">Bu kişiler, ana ortak arabirimi gereksiz şekilde bilmeden gelişmiş özelleştirme seçeneklerini göstermek için kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="e0e93-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>  
  
 <span data-ttu-id="e0e93-105">"Protected" adı yanlış bir güvenlik hissi verebildiğinden, çerçeve tasarımcılarının Korunan üyelere dikkatli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0e93-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="e0e93-106">Herhangi biri korumasız bir sınıfın alt sınıfını oluşturup korumalı üyelere erişebilir ve bu nedenle ortak üyeler için kullanılan tüm savunma kodlama uygulamalarının korunan üyeler için de uygulanması mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="e0e93-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>  
  
 <span data-ttu-id="e0e93-107">**✓ CONSIDER** kullanarak korumalı üyeler için Gelişmiş özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="e0e93-107">**✓ CONSIDER** using protected members for advanced customization.</span></span>  
  
 <span data-ttu-id="e0e93-108">**✓ DO** korumalı üyeleri korumasız sınıflarında güvenlik, belgelerine ve uyumluluk analiz amacıyla genel olarak ele alın.</span><span class="sxs-lookup"><span data-stu-id="e0e93-108">**✓ DO** treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>  
  
 <span data-ttu-id="e0e93-109">Herhangi biri bir sınıftan devralınabilir ve korunan üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e0e93-109">Anyone can inherit from a class and access the protected members.</span></span>  
  
 <span data-ttu-id="e0e93-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e0e93-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e0e93-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="e0e93-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0e93-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0e93-112">See also</span></span>

- [<span data-ttu-id="e0e93-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e0e93-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="e0e93-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="e0e93-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
