---
description: 'Daha fazla bilgi edinin: soyut sınıf tasarımı'
title: Soyut Sınıf Tasarımı
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 5b1cd833bf43e5bf5731176243809393187e84d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642467"
---
# <a name="abstract-class-design"></a><span data-ttu-id="9095e-103">Soyut Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="9095e-103">Abstract Class Design</span></span>

<span data-ttu-id="9095e-104">❌ Soyut türlerde ortak veya korumalı iç oluşturucular tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="9095e-104">❌ DO NOT define public or protected internal constructors in abstract types.</span></span>

 <span data-ttu-id="9095e-105">Oluşturucular, yalnızca kullanıcıların türün örneklerini oluşturması gerekiyorsa genel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9095e-105">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="9095e-106">Soyut bir türün örneklerini oluşturamadığı için ortak Oluşturucusu olan bir soyut tür, kullanıcılar için yanlış tasarlanmış ve yanıltıcı olur.</span><span class="sxs-lookup"><span data-stu-id="9095e-106">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>

 <span data-ttu-id="9095e-107">✔️ soyut sınıflarda korumalı veya dahili bir oluşturucu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9095e-107">✔️ DO define a protected or an internal constructor in abstract classes.</span></span>

 <span data-ttu-id="9095e-108">Korunan bir Oluşturucu daha yaygındır ve yalnızca alt türler oluşturulduğunda temel sınıfın kendi başlatmasını yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9095e-108">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>

 <span data-ttu-id="9095e-109">Bir iç Oluşturucu, soyut sınıfın somut uygulamalarını sınıfı tanımlayan derlemeyle sınırlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9095e-109">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>

 <span data-ttu-id="9095e-110">✔️, sevk ettiğiniz her soyut sınıftan devralan en az bir somut tür sağlar.</span><span class="sxs-lookup"><span data-stu-id="9095e-110">✔️ DO provide at least one concrete type that inherits from each abstract class that you ship.</span></span>

 <span data-ttu-id="9095e-111">Bunu yapmak, soyut sınıfın tasarımını doğrulamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9095e-111">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="9095e-112">Örneğin,  <xref:System.IO.FileStream?displayProperty=nameWithType> <xref:System.IO.Stream?displayProperty=nameWithType> soyut sınıfın bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="9095e-112">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>

 <span data-ttu-id="9095e-113">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9095e-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9095e-114">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="9095e-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9095e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9095e-115">See also</span></span>

- [<span data-ttu-id="9095e-116">Tür tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9095e-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="9095e-117">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9095e-117">Framework Design Guidelines</span></span>](index.md)
