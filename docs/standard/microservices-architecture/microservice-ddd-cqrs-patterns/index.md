---
title: Bir Mikro Hizmetteki İş Karmaşıklığını DDD ve CQRS Desenleriyle Giderme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Nasıl başa çıkabileceğiniz DDD ve CQRS desenleriyle uygulama karmaşık iş senaryolarını anlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: f17acd6765de96bf8cec28c4e212733822fa0b73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019769"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Başa çıkmaya iş karmaşıklığını DDD ve CQRS desenleriyle bir mikro hizmetteki

*Her mikro hizmet ya da iş etki alanının anlama yansıtır sınırlanmış bağlam için bir etki alanı modeli tasarlayın.*

Bu bölümde daha gelişmiş karmaşık alt sistemlerin üstesinden gerektiğinde uygulayan mikro hizmette veya etki alanı uzmanlarıyla durmaksızın değişen iş kuralları bilgisi türetilen mikro hizmetler ele alınmaktadır. Bu bölümde kullanılan mimarisi desenleri, Şekil 7-1'de gösterildiği gibi etki alanı Odaklı Tasarım (DDD) ve yaklaşım, komut ve sorgu sorumluluğu ayrımı (CQRS) bağlıdır.

![Dış mimarisi arasındaki fark: mikro hizmet desenleri, API ağ geçitleri, dayanıklı iletişimleri, yayımlama/abonelik, vb. ve iç mimarisi: veri temelli/CRUD DDD deseni, bağımlılık ekleme, birden çok kitaplıkları, vs.](./media/image1.png)

**Şekil 7-1**. Her mikro hizmet için iç mimari desenleri ve dış mikro hizmet mimarisi

Ancak, veri odaklı mikro hizmetler, bir ASP.NET Core Web API'si hizmeti uygulama veya Swashbuckle veya NSwag, Swagger meta verileri nasıl sunacağınızı öğrenin gibi teknikler de ile dahili olarak uygulanan daha gelişmiş mikro hizmetler için uygulanabilir çoğu DDD deseni. Bu bölümde, önceki bölümlerde uzantısı çünkü daha önce açıklanan yöntemler çoğunu burada veya her türden bir mikro hizmet için de geçerlidir.

Bu bölümde, ilk hizmetine başvuru uygulamada kullanılan Basitleştirilmiş CQRS desenleriyle ilgili ayrıntılar verilmektedir. Daha sonra uygulamalarınızda yeniden kullanabilirsiniz ortak desenler bulmanıza olanak sağlamak DDD teknikleri genel bir bakış alırsınız.

DDD zengin için kaynaklar ile büyük bir konudur. Kitapları gibi ile başlayabilirsiniz [etki alanı Odaklı Tasarım](https://domainlanguage.com/ddd/) Eric Evans ve ek Materyaller Vaughn Vernon, Jimmy Nilsson, Greg Young, UDI Dahan, Jimmy Bogard ve diğer birçok DDD/CQRS uzmanlar tarafından. Ancak çoğu, tüm konuşmaları, Beyaz Tahta kullanımı ve etki alanı uzmanlarıyla somut iş etki alanınızda oturumları modelleme DDD teknikleri uygulama hakkında bilgi edinmek denemeniz gerekir.

#### <a name="additional-resources"></a>Ek kaynaklar

##### <a name="ddd-domain-driven-design"></a>DDD (etki alanı Odaklı Tasarım)

- **Eric Evans. Etki alanı dil** \
  <https://domainlanguage.com/>

- **Martin Fowler. Etki alanı Odaklı Tasarım** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard. Etki alanınızı güçlendirme: bir öncü** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>DDD kitaplar

- **Eric Evans. Etki alanı Odaklı Tasarım: Yazılım kalbi kuruluşlarda karmaşıklığı** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Etki alanı Odaklı Tasarım başvurusu: Tanımları ve desen özetleri** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon. Uygulama etki alanı Odaklı Tasarım** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon. Etki alanı Odaklı Tasarım biçimlendirileceğini** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Etki alanı Odaklı Tasarım ve desenleri uygulama** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre. .NET ile N katmanlı etki alanı odaklı Mimari Kılavuzu** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram ve Floyd Marinescu. Etki alanı tasarım hızla odaklı** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Nick ayarlama - desenleri, prensipleri ve etki alanı Odaklı Tasarım yöntemleri** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>DDD eğitim

- **Julie Lerman ve Steve Smith. Etki alanı Odaklı Tasarım ile ilgili temel bilgiler** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Önceki](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[İleri](apply-simplified-microservice-cqrs-ddd-patterns.md)
