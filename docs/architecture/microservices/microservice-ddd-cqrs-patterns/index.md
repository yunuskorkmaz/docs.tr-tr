---
title: Bir Mikro Hizmetteki İş Karmaşıklığını DDD ve CQRS Desenleriyle Giderme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | DDD ve CQRS desenleri uygulayan karmaşık iş senaryolarına nasıl karar vermek istediğinizi anlayın
ms.date: 10/08/2018
ms.openlocfilehash: 852073548a66fbe568fc5c2531342db944d5a8b0
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144649"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Bir Mikro Hizmetteki İş Karmaşıklığını DDD ve CQRS Desenleriyle Giderme

*Her mikro hizmet için veya iş etki alanının anlaşılmasına ilişkin sınırlı bağlam için bir etki alanı modeli tasarlayın.*

Bu bölüm, karmaşık alt sistemleri veya sürekli değişen iş kurallarıyla etki alanı uzmanlarından oluşan mikro hizmetleri bir arada açmak istediğinizde uyguladığınız daha gelişmiş mikro hizmetlere odaklanır. Bu bölümde kullanılan mimari desenleri, Şekil 7-1 ' de gösterildiği gibi etki alanı odaklı tasarım (DDD) ve Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS) yaklaşımlarına dayanır.

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Dış ve iç mimari desenlerini karşılaştıran diyagram.":::
Dış mimari arasındaki fark: mikro hizmet desenleri, API ağ geçitleri, dayanıklı iletişimler, yayın/alt, vb. ve dahili mimari: veri odaklı/CRUD, DDD desenleri, bağımlılık ekleme, birden çok kitaplık, vb.
:::image-end:::

**Şekil 7-1**. Her mikro hizmet için dış mikro hizmet mimarisi, iç mimari desenlerine karşı

Ancak, ASP.NET Core Web API hizmetini uygulama ya da swashbuckle veya NSwag ile Swagger meta verilerini kullanıma sunma gibi veri odaklı mikro hizmetlere yönelik çoğu teknikte, ayrıca DDD desenleriyle dahili olarak uygulanan daha gelişmiş mikro hizmetler için de geçerlidir. Bu bölüm önceki bölümlerin bir uzantısıdır, çünkü daha önce açıklanan uygulamaların çoğu, burada veya herhangi bir mikro hizmet türü için de geçerlidir.

Bu bölüm öncelikle eShopOnContainers başvuru uygulamasında kullanılan Basitleştirilmiş CQRS desenleriyle ilgili ayrıntıları sağlar. Daha sonra, uygulamalarınızda yeniden kullanabileceğiniz ortak desenleri bulmanızı sağlayan DDD tekniklerine genel bir bakış alacaksınız.

DDD, öğrenme için zengin kaynak kümesi içeren büyük bir konudur. Eric Evans tarafından [etki alanı odaklı tasarım](https://domainlanguage.com/ddd/) ve Vaughn versuz, Jimmy Nilsson, Greg Başak, UDI Dahan, Jimmy Bogard ve bırçok başka ddd/CQRS uzmanından ek malzemeler gibi kitaplarla başlayabilirsiniz. Ancak bunların çoğu, somut iş etki alanındaki uzmanlar ile konuşmalar, beyaz taslak ve etki alanı modelleme oturumlarından DDD tekniklerini nasıl uygulayacağınızı öğrenmeyi denemeniz gerekir.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="ddd-domain-driven-design"></a>DDD (etki alanı odaklı tasarım)

- **Eric Evans. Etki alanı dili** \
  <https://domainlanguage.com/>

- **Marwler. Etki alanı odaklı tasarım** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard. Etki alanınızı güçlendirerek: bir öncü** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>DDD kitapları

- **Eric Evans. Etki alanı odaklı tasarım: yazılım Kalbunda karmaşıklık karmaşıklığı** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Etki alanı odaklı tasarım başvurusu: tanımlar ve desenli özetler** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn versuz. Etki alanı odaklı tasarımı uygulama** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn versuz. Etki alanı odaklı tasarım geri ışığı** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Etki alanı odaklı tasarım ve desenleri uygulama** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de La Torre. .NET ile N katmanlı etki alanı odaklı mimari Kılavuzu** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram ve Floyd Marinescu. Etki alanı odaklı tasarım hızlı** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Nick ayarı-etki alanı odaklı tasarımın desenleri, Ilkeleri ve uygulamaları** \
  <https://www.wiley.com/Patterns%2C+Principles%2C+and+Practices+of+Domain+Driven+Design-p-9781118714706>

##### <a name="ddd-training"></a>DDD eğitimi

- **Julie Lerman ve Steve Smith. Etki alanı odaklı tasarım temelleri** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md) 
> [Sonraki](apply-simplified-microservice-cqrs-ddd-patterns.md)
