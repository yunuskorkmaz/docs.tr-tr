---
title: Mikro hizmet DDD ve CQRS desenler ile iş karmaşıklığı tackling
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet DDD ve CQRS desenler ile iş karmaşıklığı tackling
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ef8e0b08c7ba4ddb78144df54d407998cd40fc55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577195"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Mikro hizmet DDD ve CQRS desenler ile iş karmaşıklığı tackling

*Her mikro hizmet veya iş etki alanının anlama yansıtır ilişkisindeki bağlamı için bir etki alanı modeli tasarlayın.*

Bu bölümde daha gelişmiş karmaşık alt sistemleri üstesinden gelmek gerektiğinde uygulayan mikro veya sürekli değişen iş kuralları etki alanı uzmanlarıyla bilgi türetilmiş mikro odaklanır. Bu bölümde kullanılan mimarisi desenleri etki alanı Odaklı Tasarım (DDD) ve komut ve sorgu sorumluluk ayrımı (CQRS) yaklaşım, Şekil 9-1'de gösterildiği gibi temel alır.

![](./media/image1.png)

**Şekil 9-1**. Her mikro hizmet için iç mimari desenleri karşı dış mikro hizmet mimarisi

Ancak, bir ASP.NET çekirdek Web API hizmeti uygulama veya Swashbuckle, Swagger meta verilerini kullanıma sunmak nasıl gibi mikro verilerle teknikleri de dahili DDD ile uygulanan daha gelişmiş mikro uygulanabilir çoğu desenler. Bu bölümde önceki bölümlerde uzantısı çünkü daha önce açıklanan uygulamalarının çoğu burada veya mikro hizmet herhangi bir tür için de geçerlidir.

Bu bölümde ilk eShopOnContainers başvuru uygulamada kullanılan Basitleştirilmiş CQRS desenleri ayrıntıları sağlar. Daha sonra uygulamalarınızda yeniden kullanabilirsiniz ortak desenler bulmak etkinleştirmeniz DDD teknikleri genel bir bakış alırsınız.

GGG, zengin bir bilgi edinme kaynakları ile büyük bir konudur. Gibi kitaplarıyla başlatabilirsiniz [Domain-Driven tasarım](https://domainlanguage.com/ddd/) Eric Evans ve ek malzemeleri Vaughn Vernon, Jimmy Nilsson, Greg Young, UDI Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanlar tarafından. Ancak, tüm çoğunu görüşmeleri, whiteboarding ve etki alanı somut iş etki alanınızdaki uzmanlarla oturumları modelleme DDD teknikleri uygulamak öğrenmek denemeniz gerekir.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="ddd-domain-driven-design"></a>DDD (etki alanı tabanlı tasarım)

-   **Eric Evans. Etki alanı dili**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)

-   **Martin Fowler. Etki alanı Odaklı Tasarım**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard. Etki alanınızı güçlendirme: öncü**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>DDD defterleri

-   **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım Kalp karmaşıklığı Tackling**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Eric Evans. Etki alanı Odaklı Tasarım başvuru: Tanımları ve desen özetleri**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon. Etki alanı tabanlı tasarımı uygulama**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon. Etki alanı tabanlı tasarım biçimlendirileceğini**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson. Etki alanı Odaklı Tasarım ve desenleri uygulama**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Cesar de la Torre. .NET ile N katmanlı etki alanı odaklı Mimari Kılavuzu**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Abel Avram ve Floyd Marinescu. Etki alanı tasarım hızla temelli**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

DDD eğitim

-   **Julie Lerman ve Steve Smith. Etki alanı Odaklı Tasarım temelleri**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[Önceki] (.. / multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md) [sonraki] (apply-simplified-microservice-cqrs-ddd-patterns.md)
