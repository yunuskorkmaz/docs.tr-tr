---
title: Genişletilebilirlik için Tasarlama
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 9e75ef433f3bd9af34e8dd40331a8267755e59fe
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821391"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="eac95-102">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="eac95-102">Designing for Extensibility</span></span>
<span data-ttu-id="eac95-103">Çerçeve tasarlamanın önemli bir yönü, Framework 'ün genişletilebilirliğini dikkatle ele aldığınızdan emin olmak.</span><span class="sxs-lookup"><span data-stu-id="eac95-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="eac95-104">Bunun için çeşitli genişletilebilirlik mekanizmalarıyla ilişkili maliyetleri ve avantajları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eac95-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="eac95-105">Bu bölüm, genişletilebilirlik mekanizmalarının (altsınıflama, olaylar, sanal üyeler, geri çağırmalar vb.) en iyi şekilde ne kadar uygun olduğuna karar vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="eac95-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="eac95-106">Çerçeveler içinde genişletilebilirlik sağlamak için birçok yol vardır.</span><span class="sxs-lookup"><span data-stu-id="eac95-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="eac95-107">Bunlar, daha az güçlü, ancak pahalı, ancak pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="eac95-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="eac95-108">Herhangi bir genişletilebilirlik gereksinimi için, gereksinimleri karşılayan en düşük maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eac95-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="eac95-109">Daha sonra daha fazla genişletilebilirlik eklemek mümkün olsa da, önemli değişikliklere bildirmeden hiçbir zaman daha fazla işlem yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eac95-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eac95-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eac95-110">In This Section</span></span>  
 [<span data-ttu-id="eac95-111">Korumasız sınıflar</span><span class="sxs-lookup"><span data-stu-id="eac95-111">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="eac95-112">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="eac95-112">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="eac95-113">Olaylar ve geri çağrılar</span><span class="sxs-lookup"><span data-stu-id="eac95-113">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="eac95-114">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="eac95-114">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="eac95-115">Soyutlamalar (soyut türler ve arabirimler)</span><span class="sxs-lookup"><span data-stu-id="eac95-115">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="eac95-116">Soyutlamalar uygulamak için temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="eac95-116">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="eac95-117">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="eac95-117">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="eac95-118">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="eac95-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="eac95-119">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="eac95-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac95-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eac95-120">See also</span></span>

- [<span data-ttu-id="eac95-121">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="eac95-121">Framework Design Guidelines</span></span>](index.md)
