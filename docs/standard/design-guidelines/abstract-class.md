---
title: "Soyut sınıf tasarımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d7b680c3377cbfa40734a57f9408d9487dbf3769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-class-design"></a><span data-ttu-id="2c2aa-102">Soyut sınıf tasarımı</span><span class="sxs-lookup"><span data-stu-id="2c2aa-102">Abstract Class Design</span></span>
<span data-ttu-id="2c2aa-103">**X yok** soyut türlerinde genel ya da korumalı iç oluşturucuları tanımlama.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="2c2aa-104">Oluşturucular kullanıcılar türdeki örneklerin oluşturmanız gerekir, ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="2c2aa-105">Soyut bir tür örneklerini oluşturamazsınız çünkü bir public oluşturucuya sahip soyut bir tür tasarlanmış ve kullanıcılara yanıltıcı yanlış.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="2c2aa-106">**✓ YAPMAK** korumalı bir ya da bir iç Oluşturucusu soyut sınıflarda tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="2c2aa-107">Korumalı Oluşturucu daha yaygın bir durumdur ve yalnızca alt oluşturulduğunda kendi başlatma yapmak temel sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="2c2aa-108">Bir iç Oluşturucusu sınıfını tanımlama derleme Özet sınıf, somut uygulamalarını sınırlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="2c2aa-109">**✓ YAPMAK** sevk her soyut sınıfından devralan en az bir somut türü sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="2c2aa-110">Soyut sınıf tasarımını doğrulamak için bu yardımcı yapılıyor.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="2c2aa-111">Örneğin, <xref:System.IO.FileStream?displayProperty=nameWithType> uygulamasıdır <xref:System.IO.Stream?displayProperty=nameWithType> soyut sınıf.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="2c2aa-112">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="2c2aa-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2c2aa-113">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="2c2aa-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2aa-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c2aa-114">See Also</span></span>  
 [<span data-ttu-id="2c2aa-115">Türü tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2c2aa-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="2c2aa-116">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2c2aa-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
