---
title: Mühürsüz Sınıflar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743557"
---
# <a name="unsealed-classes"></a><span data-ttu-id="05e3c-102">Mühürsüz Sınıflar</span><span class="sxs-lookup"><span data-stu-id="05e3c-102">Unsealed Classes</span></span>
<span data-ttu-id="05e3c-103">Korumalı sınıflar öğesinden devralınamaz ve genişletilebilirliği engeller.</span><span class="sxs-lookup"><span data-stu-id="05e3c-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="05e3c-104">Buna karşılık, öğesinden devralınılabilecek sınıflar korumasız sınıflar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="05e3c-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="05e3c-105">✔️, bir çerçeveye pahalı ve çok daha fazla bir genişletilebilirlik sağlamak için, eklenmiş bir sanal veya korumalı üye olmadan korumasız sınıflar kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="05e3c-105">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="05e3c-106">Geliştiriciler, özel oluşturucular, yeni yöntemler veya yöntem aşırı yüklemeleri gibi kolay Üyeler eklemek için genellikle korumasız sınıflardan devralması ister.</span><span class="sxs-lookup"><span data-stu-id="05e3c-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="05e3c-107">Örneğin, `System.Messaging.MessageQueue` korumasız olur ve bu sayede kullanıcıların belirli bir sıra yolu için varsayılan olarak özel kuyruklar oluşturmalarına veya belirli senaryolar için API 'YI basitleştiren özel yöntemler eklemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="05e3c-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="05e3c-108">Sınıflar çoğu programlama dilinde varsayılan olarak korumasız olur ve çerçeveler içindeki çoğu sınıf için de önerilen varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="05e3c-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="05e3c-109">Korumasız türler tarafından sağlanan genişletilebilirlik, çatı kullanıcıları tarafından çok daha fazla teşekkürler ve korumasız türlerle ilişkili görece düşük test maliyetlerinden dolayı sağlanması oldukça ucuzdur.</span><span class="sxs-lookup"><span data-stu-id="05e3c-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="05e3c-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="05e3c-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="05e3c-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="05e3c-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="05e3c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05e3c-112">See also</span></span>

- [<span data-ttu-id="05e3c-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="05e3c-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="05e3c-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="05e3c-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="05e3c-115">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="05e3c-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
