---
title: DDD ve CQRS desenleriyle bir mikro hizmetteki iş karmaşıklığını bağlayabileceğiniz
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | DDD ve CQRS desenleriyle bir mikro hizmetteki iş karmaşıklığını bağlayabileceğiniz
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 1af53f8f37e516219767fdde49eb7da9927d9e29
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182469"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>DDD ve CQRS desenleriyle bir mikro hizmetteki iş karmaşıklığını bağlayabileceğiniz

*Her mikro hizmet ya da iş etki alanının anlama yansıtır sınırlanmış bağlam için bir etki alanı modeli tasarlayın.*

Bu bölümde daha gelişmiş karmaşık alt sistemlerin üstesinden gerektiğinde uygulayan mikro hizmette veya etki alanı uzmanlarıyla durmaksızın değişen iş kuralları bilgisi türetilen mikro hizmetler ele alınmaktadır. Bu bölümde kullanılan mimarisi desenleri, Şekil 9-1'de gösterildiği gibi etki alanı Odaklı Tasarım (DDD) ve yaklaşım, komut ve sorgu sorumluluğu ayrımı (CQRS) bağlıdır.

![](./media/image1.png)

**Şekil 9-1**. Her mikro hizmet için iç mimari desenleri ve dış mikro hizmet mimarisi

Ancak, veri odaklı mikro hizmetler, bir ASP.NET Core Web API'si hizmeti uygulama veya Swashbuckle, Swagger meta verilerini nasıl sunacağınızı öğrenin gibi teknikler de DDD ile dahili olarak uygulanan daha gelişmiş mikro hizmetler için geçerli çoğu desenler. Bu bölümde, önceki bölümlerde uzantısı çünkü daha önce açıklanan yöntemler çoğunu burada veya her türden bir mikro hizmet için de geçerlidir.

Bu bölümde, ilk hizmetine başvuru uygulamada kullanılan Basitleştirilmiş CQRS desenleriyle ilgili ayrıntılar verilmektedir. Daha sonra uygulamalarınızda yeniden kullanabilirsiniz ortak desenler bulmanıza olanak sağlamak DDD teknikleri genel bir bakış alırsınız.

DDD zengin için kaynaklar ile büyük bir konudur. Kitapları gibi ile başlayabilirsiniz [etki alanı Odaklı Tasarım](https://domainlanguage.com/ddd/) Eric Evans ve ek Materyaller Vaughn Vernon, Jimmy Nilsson, Greg Young, UDI Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanlar tarafından. Ancak çoğu, tüm konuşmaları, Beyaz Tahta kullanımı ve etki alanı uzmanlarıyla somut iş etki alanınızda oturumları modelleme DDD teknikleri uygulama hakkında bilgi edinmek denemeniz gerekir.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="ddd-domain-driven-design"></a>DDD (etki alanı Odaklı Tasarım)

-   **Eric Evans. Etki alanı dil**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)

-   **Martin Fowler. Etki alanı Odaklı Tasarım**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard. Etki alanınızı güçlendirme: bir öncü**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>DDD kitaplar

-   **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım kalbi karmaşıklığı bağlayabileceğiniz**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Eric Evans. Etki alanı Odaklı Tasarım başvurusu: Tanımları ve desen özetleri**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon. Uygulama etki alanı Odaklı Tasarım**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon. Etki alanı Odaklı Tasarım biçimlendirileceğini**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson. Etki alanı Odaklı Tasarım ve desenleri uygulama**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Cesar de la Torre. .NET ile N katmanlı etki alanı odaklı Mimari Kılavuzu**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Abel Avram ve Floyd Marinescu. Etki alanı tasarım hızla odaklı**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

DDD eğitim

-   **Julie Lerman ve Steve Smith. Etki alanı Odaklı Tasarım ile ilgili temel bilgiler**
    [*https://bit.ly/PS-DDD*](https://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[İleri](apply-simplified-microservice-cqrs-ddd-patterns.md)