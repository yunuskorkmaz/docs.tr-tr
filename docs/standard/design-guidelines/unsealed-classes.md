---
description: 'Daha fazla bilgi edinin: korumasız sınıflar'
title: Mühürsüz Sınıflar
ms.date: 10/22/2008
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6fe30c3a2ef8df6b983d857b9502805e90ab83dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641830"
---
# <a name="unsealed-classes"></a><span data-ttu-id="e3733-103">Mühürsüz Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e3733-103">Unsealed Classes</span></span>

<span data-ttu-id="e3733-104">Korumalı sınıflar öğesinden devralınamaz ve genişletilebilirliği engeller.</span><span class="sxs-lookup"><span data-stu-id="e3733-104">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="e3733-105">Buna karşılık, öğesinden devralınılabilecek sınıflar korumasız sınıflar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e3733-105">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="e3733-106">✔️, bir çerçeveye pahalı ve çok daha fazla bir genişletilebilirlik sağlamak için, eklenmiş bir sanal veya korumalı üye olmadan korumasız sınıflar kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e3733-106">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="e3733-107">Geliştiriciler, özel oluşturucular, yeni yöntemler veya yöntem aşırı yüklemeleri gibi kolay Üyeler eklemek için genellikle korumasız sınıflardan devralması ister.</span><span class="sxs-lookup"><span data-stu-id="e3733-107">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="e3733-108">Örneğin,  `System.Messaging.MessageQueue` korumasız olduğundan, kullanıcıların belirli bir sıra yoluna varsayılan olarak özel kuyruklar oluşturmalarına veya belirli senaryolar için API 'yi basitleştiren özel yöntemler eklemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e3733-108">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="e3733-109">Sınıflar çoğu programlama dilinde varsayılan olarak korumasız olur ve çerçeveler içindeki çoğu sınıf için de önerilen varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="e3733-109">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="e3733-110">Korumasız türler tarafından sağlanan genişletilebilirlik, çatı kullanıcıları tarafından çok daha fazla teşekkürler ve korumasız türlerle ilişkili görece düşük test maliyetlerinden dolayı sağlanması oldukça ucuzdur.</span><span class="sxs-lookup"><span data-stu-id="e3733-110">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="e3733-111">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e3733-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e3733-112">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="e3733-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e3733-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3733-113">See also</span></span>

- [<span data-ttu-id="e3733-114">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e3733-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="e3733-115">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="e3733-115">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="e3733-116">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="e3733-116">Sealing</span></span>](sealing.md)
