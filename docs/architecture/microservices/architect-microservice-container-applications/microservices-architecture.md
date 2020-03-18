---
title: Mikro hizmetler mimarisi
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Microservices mimarisinin 30.000 feet görünümü.
ms.date: 09/20/2018
ms.openlocfilehash: d1c58d218be9e5f8c0ae8ae732f9bdd06674a2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834394"
---
# <a name="microservices-architecture"></a>Mikro hizmetler mimarisi

Adından da anlaşılacağı gibi, bir microservices mimarisi küçük hizmetler kümesi olarak bir sunucu uygulaması oluşturmak için bir yaklaşımdır. Bu bir mikrohizmet mimarisi ağırlıklı olarak arka uç odaklı olduğu anlamına gelir, yaklaşım da ön uç için kullanılıyor olsa. Her hizmet kendi sürecinde çalışır ve HTTP/HTTPS, WebSockets veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)gibi protokolleri kullanarak diğer işlemlerle iletişim kurar. Her microservice belirli bir bağlam sınırı içinde belirli bir uç-uç etki alanı veya iş yeteneği uygular ve her biri özerk olarak geliştirilmeli ve bağımsız olarak dağıtılabilir. Son olarak, her microservice ilgili etki alanı veri modeli ve etki alanı mantığı (egemenlik ve ademi merkeziyetçi veri yönetimi) sahibi olmalı ve farklı veri depolama teknolojileri (SQL, NoSQL) ve farklı programlama dillerine dayalı olabilir.

Bir mikro hizmet boyutu nda olmalıdır? Bir microservice geliştirirken, boyut önemli bir nokta olmamalıdır. Bunun yerine, önemli nokta, her hizmet için geliştirme, dağıtım ve ölçek özerkliğine sahip olmak için gevşek birleştirilmiş hizmetler oluşturmak olmalıdır. Tabii ki, mikro hizmetleri tanımlarken ve tasarlarken, diğer mikro hizmetlerle çok fazla doğrudan bağımlılığınız olmadığı sürece bunları mümkün olduğunca küçük yapmaya çalışmalısınız. Mikro hizmetin boyutundan daha önemli olan, sahip olması gereken iç uyum ve diğer hizmetlerden bağımsızlığıdır.

Neden bir microservices mimarisi? Kısacası, uzun vadeli çeviklik sağlar. Mikro hizmetler, her biri tanecikli ve özerk yaşam döngülerine sahip birçok bağımsız olarak dağıtılabilir hizmete dayalı uygulamalar oluşturmanıza izin vererek karmaşık, büyük ve yüksek ölçeklenebilir sistemlerde daha iyi korunabilirlik sağlar.

Ek bir avantaj olarak, mikro hizmetler bağımsız olarak ölçeklendirilebilir. Birim olarak ölçeklendirmeniz gereken tek bir yekpare uygulamaya sahip olmak yerine, belirli mikro hizmetleri ölçeklendirebilirsiniz. Bu şekilde, uygulamanın ölçeklenmesi gerekmeyen diğer alanlarını ölçeklendirmek yerine talebi desteklemek için daha fazla işlem gücü veya ağ bant genişliğine ihtiyaç duyan işlevsel alanı ölçeklendirebilirsiniz. Bu, daha az donanıma ihtiyacınız olduğundan maliyet tasarrufu anlamına gelir.

![İki dağıtım yöntemi arasındaki farkların diyagramı.](./media/microservices-architecture/monolith-deployment-vs-microservice-approach.png)

**Şekil 4-6**. Mikro hizmetler yaklaşımına karşı monolitik dağıtım

Şekil 4-6'nın gösterdiği gibi, geleneksel yekpare yaklaşımda, uygulama tüm uygulamayı çeşitli sunucularda/VM'de klonlayarak ölçeklendirin. Mikro hizmetler yaklaşımında, işlevsellik daha küçük hizmetlerde ayrılmıştır, böylece her hizmet bağımsız olarak ölçeklenebilir. Mikro hizmetler yaklaşımı, karmaşık, büyük ve ölçeklenebilir uygulamaların belirli, küçük alanlarını değiştirebileceğinizden, çevik değişikliklere ve her bir microservice'in hızlı yinelemesine olanak tanır.

İnce taneli mikrohizmetler tabanlı uygulamaların tasarlanması, sürekli entegrasyon ve sürekli teslimat uygulamaları sağlar. Ayrıca uygulamaya yeni işlevlerin teslimini hızlandırır. Uygulamaların ince taneli bileşimi, mikro hizmetleri izole olarak çalıştırmanızı ve test etmenizi ve aralarındaki net sözleşmeleri korurken bunları özerk olarak geliştirmenizi de sağlar. Arabirimleri veya sözleşmeleri değiştirmediğiniz sürece, herhangi bir mikro hizmetin dahili uygulamasını değiştirebilir veya diğer mikro hizmetleri bozmadan yeni işlevler ekleyebilirsiniz.

Mikro hizmet tabanlı bir sistemle üretime girerken başarıyı sağlayacak önemli hususlar şunlardır:

- Hizmetlerin ve altyapının izlenmesi ve sağlık kontrolleri.

- Hizmetler için ölçeklenebilir altyapı (yani bulut ve orkestratörler).

- Birden fazla düzeyde güvenlik tasarımı ve uygulanması: kimlik doğrulama, yetkilendirme, sırlar yönetimi, güvenli iletişim, vb.

- Hızlı uygulama teslimatı, genellikle farklı mikro hizmetlere odaklanan farklı ekiplerle.

- DevOps ve CI / CD uygulamaları ve altyapı.

Bunlardan sadece ilk üçü bu kılavuzda ele alınır veya tanıtılır. Uygulama yaşam döngüsüile ilgili son iki nokta, Microsoft Platformu ve Tools e-kitap ile ek [Containerized Docker Uygulama Yaşam Döngüsü](https://aka.ms/dockerlifecycleebook) kapsamındadır.

## <a name="additional-resources"></a>Ek kaynaklar

- **Mark Russinovich. Microservices: Bulut tarafından desteklenen bir uygulama devrimi** \
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Martin Fowler' ı. Mikro Hizmetler** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Martin Fowler' ı. Microservice Ön Koşulları** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson' ı. Chunk Bulut Bilgi İşlem** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Cesar de la Torre. Microsoft Platform ve Araçları ile KonteynerDocker Uygulama Yaşam Döngüsü** (indirilebilir e-kitap) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Önceki](service-oriented-architecture.md)
>[Sonraki](data-sovereignty-per-microservice.md)
