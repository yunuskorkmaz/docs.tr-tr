---
title: Soyut Sınıf Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 19482199648a8fb9c4b2c796fb1ab5d62c896abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709601"
---
# <a name="abstract-class-design"></a><span data-ttu-id="46576-102">Soyut Sınıf Tasarımı</span><span class="sxs-lookup"><span data-stu-id="46576-102">Abstract Class Design</span></span>
<span data-ttu-id="46576-103">**X DO NOT** soyut türlerinde genel ya da korumalı iç oluşturucuları tanımlama.</span><span class="sxs-lookup"><span data-stu-id="46576-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="46576-104">Oluşturucular, yalnızca kullanıcıların türün örneklerini oluşturması gerekiyorsa genel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46576-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="46576-105">Soyut bir türün örneklerini oluşturamadığı için ortak Oluşturucusu olan bir soyut tür, kullanıcılar için yanlış tasarlanmış ve yanıltıcı olur.</span><span class="sxs-lookup"><span data-stu-id="46576-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="46576-106">**✓ DO** korumalı bir ya da bir iç Oluşturucusu soyut sınıflarda tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="46576-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="46576-107">Korunan bir Oluşturucu daha yaygındır ve yalnızca alt türler oluşturulduğunda temel sınıfın kendi başlatmasını yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="46576-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="46576-108">Bir iç Oluşturucu, soyut sınıfın somut uygulamalarını sınıfı tanımlayan derlemeyle sınırlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46576-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="46576-109">**✓ DO** sevk her soyut sınıfından devralan en az bir somut türü sağlayın.</span><span class="sxs-lookup"><span data-stu-id="46576-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="46576-110">Bunu yapmak, soyut sınıfın tasarımını doğrulamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="46576-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="46576-111">Örneğin, <xref:System.IO.FileStream?displayProperty=nameWithType>, <xref:System.IO.Stream?displayProperty=nameWithType> soyut sınıfının bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="46576-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="46576-112">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="46576-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="46576-113">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="46576-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46576-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46576-114">See also</span></span>

- [<span data-ttu-id="46576-115">Tür Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="46576-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="46576-116">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="46576-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
