---
title: Genişletilebilirlik için tasarlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46485606"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="04a2a-102">Genişletilebilirlik için tasarlama</span><span class="sxs-lookup"><span data-stu-id="04a2a-102">Designing for Extensibility</span></span>
<span data-ttu-id="04a2a-103">Bir çerçeve tasarlamanın önemli yönlerinden biri framework'ün genişletilebilirlik dikkatle emin olmak.</span><span class="sxs-lookup"><span data-stu-id="04a2a-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="04a2a-104">Bu, çeşitli genişletilebilirlik mekanizması ile ilişkili avantajlarını ve maliyetlerini anlamak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="04a2a-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="04a2a-105">Bu bölümde, genişletilebilirlik mekanizması karar vermenize yardımcı olur — sınıflara, olayları, sanal üyeleri, geri çağrılar ve benzeri — Çerçevenizi gereksinimlerini en iyi karşılayabilecek.</span><span class="sxs-lookup"><span data-stu-id="04a2a-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="04a2a-106">Genişletilebilirlik çerçeveleri alanında izin vermek için birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="04a2a-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="04a2a-107">Bunlar daha güçlü ancak daha az maliyetli pahalı ancak çok güçlü aralığının.</span><span class="sxs-lookup"><span data-stu-id="04a2a-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="04a2a-108">Herhangi bir belirli genişletilebilirlik gereksinim için gereksinimleri karşılayan az maliyetli genişletilebilirlik mekanizması seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="04a2a-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="04a2a-109">Daha sonra daha fazla genişletilebilirlik eklemek genellikle mümkündür, ancak hiçbir zaman onu hemen bozucu değişiklikleri oluşturmaksızın uygulayabileceğiniz aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="04a2a-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04a2a-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="04a2a-110">In This Section</span></span>  
 [<span data-ttu-id="04a2a-111">Mühürsüz Sınıflar</span><span class="sxs-lookup"><span data-stu-id="04a2a-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="04a2a-112">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="04a2a-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="04a2a-113">Etkinlikler ve Geri Aramalar</span><span class="sxs-lookup"><span data-stu-id="04a2a-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="04a2a-114">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="04a2a-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="04a2a-115">Soyutlamalar (Soyut Türler ve Arabirimler)</span><span class="sxs-lookup"><span data-stu-id="04a2a-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="04a2a-116">Soyutlama Uygulamak için Temel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="04a2a-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="04a2a-117">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="04a2a-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="04a2a-118">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="04a2a-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="04a2a-119">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="04a2a-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a2a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04a2a-120">See also</span></span>

- [<span data-ttu-id="04a2a-121">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="04a2a-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
