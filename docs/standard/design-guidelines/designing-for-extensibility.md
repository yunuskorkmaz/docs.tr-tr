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
ms.openlocfilehash: 68419fe293dd25936aa3c1e3def10bbe8852e175
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571390"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="215ad-102">Genişletilebilirlik için tasarlama</span><span class="sxs-lookup"><span data-stu-id="215ad-102">Designing for Extensibility</span></span>
<span data-ttu-id="215ad-103">Bir çerçeve tasarlamanın önemli bir özelliği Genişletilebilirlik Çerçevesi dikkatle emin yapılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="215ad-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="215ad-104">Bu, çeşitli genişletilebilirlik mekanizmaları ile ilişkili yararlar ve maliyetleri anlamak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="215ad-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="215ad-105">Bu bölümde, genişletilebilirlik mekanizması karar vermenize yardımcı olan — sınıflara, olaylar, sanal üyeler, geri çağrılar ve benzeri —, framework gereksinimlerini en iyi karşılayabilecek.</span><span class="sxs-lookup"><span data-stu-id="215ad-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="215ad-106">Genişletilebilirlik içinde çerçeve izin vermek için birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="215ad-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="215ad-107">Bunlar daha az güçlü ancak daha az maliyetli pahalı ancak çok güçlü aralığının.</span><span class="sxs-lookup"><span data-stu-id="215ad-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="215ad-108">Tüm verilen genişletilebilirlik gereksinimini gereksinimlerini karşılayan en az maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="215ad-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="215ad-109">Daha fazla genişletilebilirlik daha sonra eklemek genellikle mümkündür, ancak hiçbir zaman onu hemen önemli değişiklikler oluşturmaksızın yapabileceğiniz aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="215ad-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="215ad-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="215ad-110">In This Section</span></span>  
 [<span data-ttu-id="215ad-111">Mühürsüz Sınıflar</span><span class="sxs-lookup"><span data-stu-id="215ad-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="215ad-112">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="215ad-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="215ad-113">Etkinlikler ve Geri Aramalar</span><span class="sxs-lookup"><span data-stu-id="215ad-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="215ad-114">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="215ad-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="215ad-115">Soyutlamalar (Soyut Türler ve Arabirimler)</span><span class="sxs-lookup"><span data-stu-id="215ad-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="215ad-116">Soyutlama Uygulamak için Temel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="215ad-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="215ad-117">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="215ad-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="215ad-118">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="215ad-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="215ad-119">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="215ad-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215ad-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="215ad-120">See Also</span></span>  
 [<span data-ttu-id="215ad-121">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="215ad-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
