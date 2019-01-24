---
title: Mühürsüz sınıflar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616945"
---
# <a name="unsealed-classes"></a><span data-ttu-id="ab029-102">Mühürsüz sınıflar</span><span class="sxs-lookup"><span data-stu-id="ab029-102">Unsealed Classes</span></span>
<span data-ttu-id="ab029-103">Sealed sınıfları devralınamayacağını ve bunlar genişletilebilirlik engeller.</span><span class="sxs-lookup"><span data-stu-id="ab029-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="ab029-104">Buna karşılık, öğesinden devralınan sınıflar mühürsüz sınıflar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ab029-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="ab029-105">**✓ CONSIDER** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="ab029-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="ab029-106">Geliştiriciler genellikle özel oluşturucular, yeni bir yöntem veya yöntem aşırı yüklemeleri gibi kullanışlı üye eklemek için korumasız sınıflardan devralmasına izin istiyor.</span><span class="sxs-lookup"><span data-stu-id="ab029-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="ab029-107">Örneğin, `System.Messaging.MessageQueue` korumasız ve bu nedenle, kullanıcıların belirli bir kuyruk yolu, varsayılan özel kuyruklar oluşturmak veya belirli senaryolar için API kolaylaştırmak özel yöntemler için sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab029-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="ab029-108">Varsayılan olarak çoğu programlama dilinden sınıfları korumasız ve çerçeveleri de çoğu sınıf için önerilen varsayılan de budur.</span><span class="sxs-lookup"><span data-stu-id="ab029-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="ab029-109">Mühürlenmemiş türler tarafından gösterilen genişletilebilirlik BİLDİRİMİNİZE çok değer veriyoruz framework kullanıcılar tarafından ve oldukça Hesaplı korumasız türleriyle ilişkili nispeten düşük test maliyetlerini nedeniyle sağlamak.</span><span class="sxs-lookup"><span data-stu-id="ab029-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="ab029-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ab029-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ab029-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="ab029-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab029-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab029-112">See also</span></span>

- [<span data-ttu-id="ab029-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ab029-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ab029-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="ab029-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="ab029-115">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="ab029-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
