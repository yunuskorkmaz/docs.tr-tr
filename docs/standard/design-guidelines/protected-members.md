---
title: Korumalı Üyeler
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 3cc2ab3e605cfb5382f107dead0c95495858fc6b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828731"
---
# <a name="protected-members"></a><span data-ttu-id="dc0aa-102">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="dc0aa-102">Protected Members</span></span>
<span data-ttu-id="dc0aa-103">Kendilerine göre korunan Üyeler herhangi bir genişletilebilirlik sağlamaz, ancak altsınıflama ile daha güçlü genişletilebilirlik yapabilir.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="dc0aa-104">Bu kişiler, ana ortak arabirimi gereksiz şekilde bilmeden gelişmiş özelleştirme seçeneklerini göstermek için kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="dc0aa-105">"Protected" adı yanlış bir güvenlik hissi verebildiğinden, çerçeve tasarımcılarının Korunan üyelere dikkatli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="dc0aa-106">Herhangi biri korumasız bir sınıfın alt sınıfını oluşturup korumalı üyelere erişebilir ve bu nedenle ortak üyeler için kullanılan tüm savunma kodlama uygulamalarının korunan üyeler için de uygulanması mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="dc0aa-107">✔️ Gelişmiş özelleştirme için korumalı üyeleri kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="dc0aa-108">Güvenlik, belge ve uyumluluk analizine yönelik olarak korumasız sınıflarda korunan üyeleri ortak olarak işleme ✔️.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="dc0aa-109">Herhangi biri bir sınıftan devralınabilir ve korunan üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="dc0aa-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="dc0aa-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="dc0aa-111">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="dc0aa-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="dc0aa-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc0aa-112">See also</span></span>

- [<span data-ttu-id="dc0aa-113">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dc0aa-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="dc0aa-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="dc0aa-114">Designing for Extensibility</span></span>](designing-for-extensibility.md)
