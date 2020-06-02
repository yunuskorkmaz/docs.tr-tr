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
ms.openlocfilehash: 406c15b6ce42b637ed1bbb61761d05e040995579
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280250"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="00763-102">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="00763-102">Designing for Extensibility</span></span>
<span data-ttu-id="00763-103">Çerçeve tasarlamanın önemli bir yönü, Framework 'ün genişletilebilirliğini dikkatle ele aldığınızdan emin olmak.</span><span class="sxs-lookup"><span data-stu-id="00763-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="00763-104">Bunun için çeşitli genişletilebilirlik mekanizmalarıyla ilişkili maliyetleri ve avantajları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00763-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="00763-105">Bu bölüm, genişletilebilirlik mekanizmalarının (altsınıflama, olaylar, sanal üyeler, geri çağırmalar vb.) en iyi şekilde ne kadar uygun olduğuna karar vermenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="00763-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="00763-106">Çerçeveler içinde genişletilebilirlik sağlamak için birçok yol vardır.</span><span class="sxs-lookup"><span data-stu-id="00763-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="00763-107">Bunlar, daha az güçlü, ancak pahalı, ancak pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="00763-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="00763-108">Herhangi bir genişletilebilirlik gereksinimi için, gereksinimleri karşılayan en düşük maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="00763-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="00763-109">Daha sonra daha fazla genişletilebilirlik eklemek mümkün olsa da, önemli değişikliklere bildirmeden hiçbir zaman daha fazla işlem yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00763-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00763-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="00763-110">In This Section</span></span>  
 [<span data-ttu-id="00763-111">Korumasız sınıflar</span><span class="sxs-lookup"><span data-stu-id="00763-111">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="00763-112">Korumalı Üyeler</span><span class="sxs-lookup"><span data-stu-id="00763-112">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="00763-113">Olaylar ve geri çağrılar</span><span class="sxs-lookup"><span data-stu-id="00763-113">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="00763-114">Sanal Üyeler</span><span class="sxs-lookup"><span data-stu-id="00763-114">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="00763-115">Soyutlamalar (soyut türler ve arabirimler)</span><span class="sxs-lookup"><span data-stu-id="00763-115">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="00763-116">Soyutlamalar uygulamak için temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="00763-116">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="00763-117">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="00763-117">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="00763-118">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="00763-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="00763-119">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="00763-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00763-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00763-120">See also</span></span>

- [<span data-ttu-id="00763-121">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="00763-121">Framework Design Guidelines</span></span>](index.md)
