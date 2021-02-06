---
description: 'Daha fazla bilgi edinin: genişletilebilirlik için tasarlama'
title: Genişletilebilirlik için Tasarlama
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 148ae25380698a5a1161fb9fbdd3cc60102e865d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642272"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="4b850-103">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="4b850-103">Designing for Extensibility</span></span>

<span data-ttu-id="4b850-104">Çerçeve tasarlamanın önemli bir yönü, Framework 'ün genişletilebilirliğini dikkatle ele aldığınızdan emin olmak.</span><span class="sxs-lookup"><span data-stu-id="4b850-104">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="4b850-105">Bunun için çeşitli genişletilebilirlik mekanizmalarıyla ilişkili maliyetleri ve avantajları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b850-105">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="4b850-106">Bu bölüm, genişletilebilirlik mekanizmalarının (altsınıflama, olaylar, sanal üyeler, geri çağırmalar vb.) en iyi şekilde ne kadar uygun olduğuna karar vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4b850-106">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="4b850-107">Çerçeveler içinde genişletilebilirlik sağlamak için birçok yol vardır.</span><span class="sxs-lookup"><span data-stu-id="4b850-107">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="4b850-108">Bunlar, daha az güçlü, ancak pahalı, ancak pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b850-108">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="4b850-109">Herhangi bir genişletilebilirlik gereksinimi için, gereksinimleri karşılayan en düşük maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b850-109">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="4b850-110">Daha sonra daha fazla genişletilebilirlik eklemek mümkün olsa da, önemli değişikliklere bildirmeden hiçbir zaman daha fazla işlem yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b850-110">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b850-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4b850-111">In This Section</span></span>  

 [<span data-ttu-id="4b850-112">Korumasız sınıflar</span><span class="sxs-lookup"><span data-stu-id="4b850-112">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="4b850-113">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="4b850-113">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="4b850-114">Olaylar ve geri çağrılar</span><span class="sxs-lookup"><span data-stu-id="4b850-114">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="4b850-115">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="4b850-115">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="4b850-116">Soyutlamalar (soyut türler ve arabirimler)</span><span class="sxs-lookup"><span data-stu-id="4b850-116">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="4b850-117">Soyutlamalar uygulamak için temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="4b850-117">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="4b850-118">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="4b850-118">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="4b850-119">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="4b850-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4b850-120">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="4b850-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b850-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b850-121">See also</span></span>

- [<span data-ttu-id="4b850-122">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4b850-122">Framework Design Guidelines</span></span>](index.md)
