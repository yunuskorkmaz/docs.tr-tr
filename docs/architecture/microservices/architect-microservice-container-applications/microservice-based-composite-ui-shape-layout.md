---
title: Mikro hizmetlere dayalı bileşik u-u ui oluşturma
description: Microservices mimarisi sadece arka uç için değildir. Ön uçta kullanarak bir göz görünümü alın.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72275734"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Mikro hizmetlere dayalı bileşik u-u ui oluşturma

Microservices mimarisi genellikle sunucu tarafı işleme verileri ve mantığı ile başlar, ancak, birçok durumda, uI hala bir monolit olarak işlenir. Ancak, daha gelişmiş bir yaklaşım, [mikro frontends](https://martinfowler.com/articles/micro-frontends.html)denilen, de mikro hizmetlere dayalı uygulama kullanıcı arabirimi tasarlamaktır. Bu, sunucuda mikro hizmetler ve mikro hizmetleri tüketen tek bir istemci uygulaması yerine, mikro hizmetler tarafından üretilen kompozit bir ui'ye sahip olmak anlamına gelir. Bu yaklaşımla oluşturduğunuz mikro hizmetler hem mantık hem de görsel gösterim ile tamamlanabilir.

Şekil 4-20, yekpare bir istemci uygulamasından sadece mikro hizmetleri tüketen daha basit bir yaklaşımı gösterir. Tabii ki, HTML ve JavaScript üreten arasında bir ASP.NET MVC hizmeti olabilir. Şekil, sadece mantık ve veri değil, UI şekli (HTML ve JavaScript) odaklanmak mikrohizmetleri tüketen tek bir (yekpare) istemci UI olduğunu vurgulayan bir basitleştirme olduğunu.

![Mikro hizmetlere bağlanan yekpare bir UI uygulamasının diyagramı.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**Şekil 4-20**. Arka uç mikro hizmetleri tüketen yekpare bir kullanıcı arası bilgi bir uygulama

Buna karşılık, kompozit bir ui tam olarak oluşturulur ve mikrohizmetler kendileri tarafından oluşturulur. Bazı mikro hizmetler, UI'nin belirli alanlarının görsel şeklini kullanır. Temel fark, şablonlara dayalı istemci ara birimi bileşenlerine (örneğin TypeScript sınıfları) sahip olması ve bu şablonlar için veri şekillendirme-UI ViewModel'in her mikro hizmetten gelmesidir.

İstemci uygulaması başlatma zamanında, istemci kullanıcı arabirimi bileşenlerinin her biri (örneğin TypeScript sınıfları), kendisini belirli bir senaryo için Görünüm Modelleri sağlama yeteneğine sahip bir altyapı mikro hizmetiyle kaydeder. Mikro hizmet şekli değiştirirse, UI de değişir.

Şekil 4-21 bu bileşik UI yaklaşımının bir sürümünü gösterir. Bu, farklı tekniklere dayanan parçalı parçaları biraraya getiren başka mikro hizmetleriniz olabileceğinden basitleştirilmiştir. Geleneksel bir web yaklaşımı (ASP.NET MVC) veya SPA (Tek Sayfa Uygulaması) oluşturmanıza bağlıdır.

![Birçok görünüm modelinden oluşan bileşik bir ui diyagramı.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**Şekil 4-21**. Arka uç mikro hizmetler tarafından şekillendirilen kompozit kullanıcı bir kullanıcı bir kullanıcı bir uygulama örneği

Bu UI kompozisyon mikro hizmetlerinin her biri küçük bir API Ağ Geçidi'ne benzer. Ama bu durumda, her biri küçük bir uI alan sorumludur.

Kullandığınız UI teknolojilerine bağlı olarak, mikro hizmetler tarafından yönlendirilen kompozit bir UI yaklaşımı daha zor veya daha az zor olabilir. Örneğin, bir SPA oluşturmak veya yerel mobil uygulama için kullandığınız geleneksel bir web uygulaması oluşturmak için aynı teknikleri kullanmazsınız (bu yaklaşım için daha zor olabilecek Xamarin uygulamaları geliştirirken olduğu gibi).

[eShopOnContainers](https://aka.ms/MicroservicesArchitecture) örnek uygulama birden çok nedenden dolayı monolitik Kullanıcı Arabirimi yaklaşımını kullanır. İlk olarak, mikro hizmetler ve konteynerler için bir giriş. Kompozit bir web sitesi daha gelişmiştir, ancak ui tasarlarken ve geliştirirken daha fazla karmaşıklık gerektirir. İkincisi, eShopOnContainers da Xamarin dayalı bir yerli mobil uygulama sağlar, hangi\# istemci C tarafında daha karmaşık hale getirecek.

Ancak, mikro hizmetlere dayalı kompozit u-kullanım hizmeti hakkında daha fazla bilgi edinmek için aşağıdaki referansları kullanmanızı öneririz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Mikro Frontends (Martin Fowler günlüğü)**  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- **Mikro Frontends (Michael Geers sitesi)**  
  <https://micro-frontends.org/>
  
- **ASP.NET kullanarak Kompozit UI (Özellikle Atölye)**  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. Microservices Mimarisinde Monolitik Cephe**  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. Daha iyi ui kompozisyon sırrı**  
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farciç. Front-End Web Bileşenleri microservices içine dahil**  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Microservices Mimarisinde Frontend'i Yönetme**  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Önceki](microservices-addressability-service-registry.md)
>[Sonraki](resilient-high-availability-microservices.md)
