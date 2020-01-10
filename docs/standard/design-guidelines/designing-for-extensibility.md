---
title: Genişletilebilirlik için Tasarlama
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709471"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="e803d-102">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="e803d-102">Designing for Extensibility</span></span>
<span data-ttu-id="e803d-103">Çerçeve tasarlamanın önemli bir yönü, Framework 'ün genişletilebilirliğini dikkatle ele aldığınızdan emin olmak.</span><span class="sxs-lookup"><span data-stu-id="e803d-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="e803d-104">Bunun için çeşitli genişletilebilirlik mekanizmalarıyla ilişkili maliyetleri ve avantajları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e803d-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="e803d-105">Bu bölüm, genişletilebilirlik mekanizmalarının (altsınıflama, olaylar, sanal üyeler, geri çağırmalar vb.) en iyi şekilde ne kadar uygun olduğuna karar vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e803d-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="e803d-106">Çerçeveler içinde genişletilebilirlik sağlamak için birçok yol vardır.</span><span class="sxs-lookup"><span data-stu-id="e803d-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="e803d-107">Bunlar, daha az güçlü, ancak pahalı, ancak pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="e803d-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="e803d-108">Herhangi bir genişletilebilirlik gereksinimi için, gereksinimleri karşılayan en düşük maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e803d-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="e803d-109">Daha sonra daha fazla genişletilebilirlik eklemek mümkün olsa da, önemli değişikliklere bildirmeden hiçbir zaman daha fazla işlem yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e803d-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e803d-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e803d-110">In This Section</span></span>  
 [<span data-ttu-id="e803d-111">Mühürsüz Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e803d-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="e803d-112">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="e803d-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="e803d-113">Etkinlikler ve Geri Aramalar</span><span class="sxs-lookup"><span data-stu-id="e803d-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="e803d-114">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="e803d-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="e803d-115">Soyutlamalar (Soyut Türler ve Arabirimler)</span><span class="sxs-lookup"><span data-stu-id="e803d-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="e803d-116">Soyutlama Uygulamak için Temel Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e803d-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="e803d-117">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="e803d-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="e803d-118">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e803d-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e803d-119">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="e803d-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e803d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e803d-120">See also</span></span>

- [<span data-ttu-id="e803d-121">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e803d-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
