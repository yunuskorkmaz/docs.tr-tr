---
title: Mühürsüz sınıflar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef0f1c4c9b2d1928d6f96d62ab12df9786756498
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891383"
---
# <a name="unsealed-classes"></a><span data-ttu-id="72d6c-102">Mühürsüz sınıflar</span><span class="sxs-lookup"><span data-stu-id="72d6c-102">Unsealed Classes</span></span>
<span data-ttu-id="72d6c-103">Sealed sınıfları devralınamayacağını ve bunlar genişletilebilirlik engeller.</span><span class="sxs-lookup"><span data-stu-id="72d6c-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="72d6c-104">Buna karşılık, öğesinden devralınan sınıflar mühürsüz sınıflar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="72d6c-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="72d6c-105">**✓ CONSIDER** olmadan korumasız sınıflarını kullanarak sanal ya da korumalı üyeleri ucuz sağlamak için kullanışlı bir yoludur henüz çok Genişletilebilirlik Çerçevesi için takdir olarak eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="72d6c-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="72d6c-106">Geliştiriciler genellikle özel oluşturucular, yeni bir yöntem veya yöntem aşırı yüklemeleri gibi kullanışlı üye eklemek için korumasız sınıflardan devralmasına izin istiyor.</span><span class="sxs-lookup"><span data-stu-id="72d6c-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="72d6c-107">Örneğin, `System.Messaging.MessageQueue` korumasız ve bu nedenle, kullanıcıların belirli bir kuyruk yolu, varsayılan özel kuyruklar oluşturmak veya belirli senaryolar için API kolaylaştırmak özel yöntemler için sağlar.</span><span class="sxs-lookup"><span data-stu-id="72d6c-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="72d6c-108">Varsayılan olarak çoğu programlama dilinden sınıfları korumasız ve çerçeveleri de çoğu sınıf için önerilen varsayılan de budur.</span><span class="sxs-lookup"><span data-stu-id="72d6c-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="72d6c-109">Mühürlenmemiş türler tarafından gösterilen genişletilebilirlik BİLDİRİMİNİZE çok değer veriyoruz framework kullanıcılar tarafından ve oldukça Hesaplı korumasız türleriyle ilişkili nispeten düşük test maliyetlerini nedeniyle sağlamak.</span><span class="sxs-lookup"><span data-stu-id="72d6c-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="72d6c-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="72d6c-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="72d6c-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="72d6c-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d6c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72d6c-112">See also</span></span>

- [<span data-ttu-id="72d6c-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="72d6c-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="72d6c-114">Genişletilebilirlik için Tasarlama</span><span class="sxs-lookup"><span data-stu-id="72d6c-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [<span data-ttu-id="72d6c-115">Mühürleme</span><span class="sxs-lookup"><span data-stu-id="72d6c-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
