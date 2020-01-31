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
ms.openlocfilehash: 44d342662e1aaeb51f14470f354f2dadd9a6f18d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743648"
---
# <a name="protected-members"></a><span data-ttu-id="13f7e-102">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="13f7e-102">Protected Members</span></span>
<span data-ttu-id="13f7e-103">Kendilerine göre korunan Üyeler herhangi bir genişletilebilirlik sağlamaz, ancak altsınıflama ile daha güçlü genişletilebilirlik yapabilir.</span><span class="sxs-lookup"><span data-stu-id="13f7e-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="13f7e-104">Bu kişiler, ana ortak arabirimi gereksiz şekilde bilmeden gelişmiş özelleştirme seçeneklerini göstermek için kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="13f7e-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="13f7e-105">"Protected" adı yanlış bir güvenlik hissi verebildiğinden, çerçeve tasarımcılarının Korunan üyelere dikkatli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="13f7e-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="13f7e-106">Herhangi biri korumasız bir sınıfın alt sınıfını oluşturup korumalı üyelere erişebilir ve bu nedenle ortak üyeler için kullanılan tüm savunma kodlama uygulamalarının korunan üyeler için de uygulanması mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="13f7e-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="13f7e-107">✔️ Gelişmiş özelleştirme için korumalı üyeleri kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="13f7e-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="13f7e-108">Güvenlik, belge ve uyumluluk analizine yönelik olarak korumasız sınıflarda korunan üyeleri ortak olarak işleme ✔️.</span><span class="sxs-lookup"><span data-stu-id="13f7e-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="13f7e-109">Herhangi biri bir sınıftan devralınabilir ve korunan üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="13f7e-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="13f7e-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="13f7e-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="13f7e-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="13f7e-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="13f7e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13f7e-112">See also</span></span>

- [<span data-ttu-id="13f7e-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="13f7e-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="13f7e-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="13f7e-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
