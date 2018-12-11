---
title: Bir mikro hizmet Basitleştirilmiş CQRS ve DDD desenlerini uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | CQRS ve DDD desenlerini arasındaki genel ilişki anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ef3260143c91c2500becd7c8c1a6cd0b81dbf3d2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148073"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Bir mikro hizmet Basitleştirilmiş CQRS ve DDD desenlerini uygulama

CQRS için veri okuma ve yazma modelleri ayıran bir mimari modelidir. İlgili dönem [komut sorgu ayırma (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) ilk olarak nitelemiştir Bertrand Meyer tarafından tanımlanan *nesne yönelimli yazılım yapısına*. Sistem işlemleri keskin ayrılmış iki alt kategorilere ayırabilirsiniz temel olur:

- Sorgular. Bu bir sonuç döndürür ve sistemin durumunu değiştirmeyin ve yan etkileri ücretsizdir.

- Komutları. Bu bir sistem durumunu değiştirin.

CQS olan basit bir kavram — aynı nesneye yöntemlerinde hakkındadır sorguları veya komutları oluşturuluyor. Her bir yöntemin durumunu döndürür veya durumu, ancak ikisini birden değiştirdiği. Hatta tek depo düzeni nesne CQS ile uyumlu. Temel bir ilke CQS CQRS için kabul edilebilir.

[Komut ve sorgu sorumluluğu ayrımı (CQRS)](https://martinfowler.com/bliki/CQRS.html) Greg Young tarafından sunulan ve UDI Dahan ve başkaları tarafından kesinlikle yükseltildi. Daha ayrıntılı rağmen CQS ilkesine temel alır. Komutlar ve olayları ve isteğe bağlı olarak zaman uyumsuz iletiler alan bir deseni kabul edilebilir. Çoğu durumda okuma (sorgular) için yazma işlemleri (güncelleştirmeler) için farklı bir fiziksel veritabanı sahip gibi daha gelişmiş senaryoları CQRS ilgilidir. Ayrıca, daha fazla sistem gereksinimleri bir CQRS sistem uygulayabilir [olay kaynağını belirleme (ES)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) güncelleştirmeleri veritabanınız için bu nedenle yalnızca depoladığınız olayları geçerli durumu verilerini depolamak yerine etki alanı modeli içinde. Ancak, bu kılavuzda kullanılan yaklaşım değildir; sorguları komutlardan yalnızca ayırma oluşan basit CQRS yaklaşımı kullanıyoruz.

CQRS ayrımı yönüyle bir katmandaki sorgu işlemleri ve başka bir katmanda komutları gruplandırma tarafından sağlanır. Her katmanın kendi veri modelinin (Not dediğimiz modeli, farklı bir veritabanı gerekmez) ve kendi birleşim desenleri ve teknolojiler kullanılarak oluşturulmuştur. Daha da önemlisi, iki katman aynı katmandaki veya (mikro hizmet sıralama) örnekte olduğu gibi bu kılavuzda kullanılan mikro içinde olabilir. Veya en iyi duruma getirilmiş edilebilmeleri ve ayrı olarak başka bir etkilemeden ölçeği böylece bunlar farklı mikro hizmetler ve işlemlerde uygulanabilir.

CQRS, diğer bağlamlarda var olduğu bir okuma/yazma işlemi için iki nesne olması anlamına gelir. İçin daha gelişmiş CQRS belgelerinde hakkında bilgi edinebilirsiniz normalleştirilmişlikten çıkarılmış okuma veritabanının neden vardır. Ancak burada, bu yaklaşımı hedef DDD deseni toplamalar gibi kısıtlamalardan sorgularla sınırlama yerine sorgularda daha fazla esnekliğe sahip olduğu kullanıyoruz değil.

Bu tür bir hizmeti hizmetine başvuru uygulamadaki sıralama mikro hizmet örneğidir. Bu hizmet, Basitleştirilmiş bir CQRS yaklaşımı tabanlı bir mikro hizmet uygular. Tek bir veri kaynağı veya veritabanı, ancak iki mantıksal modellerini artı DDD deseni işlem etki alanı için Şekil 7-2'de gösterildiği gibi kullanır.

![Mantıksal sıralama mikro hizmet olabilir veya aynı Docker'da barındırma sipariş veritabanı içerir. Veritabanı aynı Docker ana bilgisayara sahip iyi geliştirme, ancak üretim için değil.](./media/image2.png)

**Şekil 7-2**. CQRS ve DDD tabanlı mikro hizmet Basitleştirilmiş

Uygulama katmanı Web API'si olabilir. Önemli tasarım burada mikro hizmet sorguları ve Viewmodel'lar (özellikle istemci uygulamaları için oluşturulan veri modelleri) bölündü komutlarını, etki alanı modeli ve CQRS modelinin aşağıdaki işlemleri yönüdür. Bu yaklaşım sorguları sınırlamaları ve kısıtlamalar sonraki bölümlerde açıklandığı gibi işlemleri ve güncelleştirmeler için anlamlı yalnızca DDD deseni geldiğini bağımsız olarak korur.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](eshoponcontainers-cqrs-ddd-microservice.md)