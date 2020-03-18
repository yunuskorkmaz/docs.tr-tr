---
title: Bir Mikro Hizmetteki İş Karmaşıklığını DDD ve CQRS Desenleriyle Giderme
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | DDD ve CQRS Desenleri uygulayan karmaşık iş senaryoları ile nasıl başa çılayacağımı anlama
ms.date: 10/08/2018
ms.openlocfilehash: 88b105b68307c8587f877bb9ddf370e143d8539b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73739842"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>DDD ve CQRS Desenleri ile Microservice'te İş Karmaşıklığıyla Mücadele

*Her microservice veya Bounded Context için iş etki alanının anlaşılmasını yansıtan bir etki alanı modeli tasarla.*

Bu bölümde, karmaşık alt sistemlerle başa çıkmak için gereken de uyguladığınız daha gelişmiş mikro hizmetler veya sürekli değişen iş kurallarına sahip etki alanı uzmanlarının bilgisinden elde edilen mikro hizmetler üzerinde duruluyor. Bu bölümde kullanılan mimari desenler, Şekil 7-1'de gösterildiği gibi etki alanı odaklı tasarım (DDD) ve Komut ve Sorgu Sorumluluğu Ayrımı (CQRS) yaklaşımlarına dayanmaktadır.

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Dış ve iç mimari desenleri karşılaştıran diyagram.":::
Dış mimari arasındaki fark: mikrohizmet kalıpları, API ağ geçitleri, esnek iletişim, pub/alt, vb. ve dahili mimari: veri odaklı/CRUD, DDD desenleri, bağımlılık enjeksiyonu, birden fazla kitaplık, vb.
:::image-end:::

**Şekil 7-1**. Her mikro hizmet için harici microservice mimarisi ve iç mimari desenleri

Ancak, ASP.NET Core Web API hizmetinin nasıl uygulanacağı veya Swagger meta verilerinin Swashbuckle veya NSwag ile nasıl ifşa edilecek gibi veri odaklı mikro hizmetler için tekniklerin çoğu, dahili olarak uygulanan daha gelişmiş mikro hizmetler için de geçerlidir. DDD desenleri. Daha önce açıklanan uygulamaların çoğu burada veya her türlü mikro hizmet için de geçerli olduğundan, bu bölüm önceki bölümlerin bir uzantısıdır.

Bu bölümde ilk olarak eShopOnContainers başvuru uygulamasında kullanılan basitleştirilmiş CQRS desenleri hakkında ayrıntılı bilgi verilmektedir. Daha sonra, uygulamalarınızda yeniden kullanabileceğiniz ortak desenleri bulmanızı sağlayan DDD tekniklerine genel bir bakış elde elabilirsiniz.

DDD öğrenme için kaynakların zengin bir dizi ile büyük bir konudur. Eric Evans'ın [Domain-Driven Design](https://domainlanguage.com/ddd/) gibi kitaplarla ve Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanından ek materyallerle başlayabilirsiniz. Ama en önemlisi nasıl konuşmaları, whiteboarding ve etki alanı modelleme oturumları somut iş alanında uzmanlarla DDD teknikleri uygulamak için öğrenmek için denemek gerekir.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="ddd-domain-driven-design"></a>DDD (Etki Alanı Odaklı Tasarım)

- **Eric Evans' ı. Etki Alanı Dili** \
  <https://domainlanguage.com/>

- **Martin Fowler' ı. Etki Alanı Odaklı Tasarım** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard' ı. Etki alanınızı güçlendirme: bir astar** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>DDD kitaplar

- **Eric Evans' ı. Etki Alanı Odaklı Tasarım: Yazılımın Kalbinde karmaşıklıkla mücadele** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans' ı. Etki Alanı Odaklı Tasarım Referansı: Tanımlar ve Örüntü Özetleri** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon' u. Etki Alanı Odaklı Tasarımın Uygulanması** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon' u. Etki Alanı Odaklı Tasarım Distile** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson' ı. Etki Alanına Dayalı Tasarım ve Desenleruygulama** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre. .NET ile N Katmanlı Etki Alanı Odaklı Mimari Rehberi** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram ve Floyd Marinescu. Etki Alanı Odaklı Tasarım Hızlı** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Nick Tune - Etki Alanı Odaklı Tasarım Desenleri, İlkeleri ve Uygulamaları** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>DDD eğitimi

- **Julie Lerman ve Steve Smith. Etki Alanı Odaklı Tasarım Temelleri** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[Sonraki](apply-simplified-microservice-cqrs-ddd-patterns.md)
