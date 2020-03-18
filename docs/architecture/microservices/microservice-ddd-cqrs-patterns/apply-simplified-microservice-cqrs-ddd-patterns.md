---
title: Bir mikro hizmete CQRS ve DDD desenlerini uygulama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | CQRS ve DDD desenleri arasındaki genel ilişkiyi anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: f42b553fd30fdffdc6e325b11740fe9162aab7c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834310"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Basitleştirilmiş CQRS ve DDD desenlerini microservice'e uygulayın

CQRS, veri okuma ve yazma modellerini birbirinden ayıran mimari bir desendir. İlgili terim [Komut Sorgusu Ayırma (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) aslında Bertrand Meyer tarafından kitabında Nesne *Yönelimli Yazılım İnşaat*tanımlanmıştır. Temel fikir, bir sistemin işlemlerini keskin bir şekilde ayrılmış iki kategoriye bölebilirsiniz:

- Sorgu. Bu bir sonuç dönmek ve sistemin durumunu değiştirmez, ve yan etkileri ücretsizdir.

- Komut. Bunlar sistemin durumunu değiştirir.

CQS basit bir kavramdır-aynı nesne içinde sorgular veya komutlar olan yöntemler hakkında. Her yöntem durumu döndürür veya durumu mutasyona uğratsa da her ikisini birden döndürmez. Tek bir depo deseni nesnesi bile CQS ile uyumlu olabilir. CQS, CQRS için temel bir ilke olarak kabul edilebilir.

[Komut ve Sorgu Sorumluluk Ayrımı (CQRS)](https://martinfowler.com/bliki/CQRS.html) Greg Young tarafından tanıtıldı ve kuvvetle Udi Dahan ve diğerleri tarafından teşvik. Daha ayrıntılı olmasına rağmen, CQS ilkesine dayanmaktadır. Komutlara ve olaylara ve isteğe bağlı olarak eşzamanlı iletilere dayalı bir desen olarak kabul edilebilir. Çoğu durumda, CQRS daha gelişmiş senaryolar ile ilgilidir, okumalar için farklı bir fiziksel veritabanı olması gibi (sorgular) yazma (güncelleştirmeler). Ayrıca, daha gelişmiş bir CQRS sistemi güncelleştirme veritabanınız için [Olay Kaynağı (ES)](https://martinfowler.com/eaaDev/EventSourcing.html) uygulayabilir, böylece olayları geçerli durum verilerini depolamak yerine yalnızca etki alanı modelinde depolarsınız. Ancak, bu kılavuzda kullanılan yaklaşım bu değildir; sorguları komutlardan ayırmaktan oluşan en basit CQRS yaklaşımını kullanıyoruz.

CQRS ayırma yönü bir katmanda sorgu işlemleri gruplandırma ve başka bir katmanda komutları elde edilir. Her katmanın kendi veri modeli vardır (model dediğimize dikkat edin, farklı bir veritabanı değil) ve kendi desen ve teknoloji kombinasyonu kullanılarak oluşturulmuştur. Daha da önemlisi, iki katman, bu kılavuz için kullanılan örnekte (sipariş mikroservice) olduğu gibi, aynı katman veya microservice içinde olabilir. Ya da farklı mikro hizmetler de veya süreçlerde uygulanabilir, böylece birbirlerini etkilemeden ayrı ayrı optimize edilebilir ve ölçeklendirilebilir.

CQRS, diğer bağlamlarda bir tane nin bulunduğu bir okuma/yazma işlemi için iki nesneye sahip olmak anlamına gelir. Daha gelişmiş CQRS literatüründe öğrenebileceğiniz normalleştirilmiş okuma veritabanına sahip olmak için nedenler vardır. Ancak burada, amacın sorgularda daha fazla esnekliğe sahip olmak yerine, sorguları agrega gibi DDD desenleri kısıtlamalarıyla sınırlamak olduğu bu yaklaşımı kullanmıyoruz.

Bu tür bir hizmet örneği eShopOnContainers referans uygulamasından sipariş microservice olduğunu. Bu hizmet basitleştirilmiş bir CQRS yaklaşımına dayalı bir microservice uygular. Tek bir veri kaynağı veya veritabanı kullanır, ancak şekil 7-2'de gösterildiği gibi, işlem etki alanı için iki mantıksal model ve DDD desenleri kullanır.

![Yüksek düzeyde Basitleştirilmiş CQRS ve DDD microservice gösteren diyagram.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Şekil 7-2**. Basitleştirilmiş CQRS ve DDD tabanlı mikrohizmet

Mantıksal "Sipariş" Microservice olabilir, ancak aynı Docker ana bilgisayar olmak zorunda değildir Sipariş veritabanı içerir. Veritabanının aynı Docker ana bilgisayarda olması geliştirme için iyidir, ancak üretim için değildir.

Uygulama katmanı Web API'nin kendisi olabilir. Burada önemli tasarım yönü microservice komutları, etki alanı modeli ve CQRS desen aşağıdaki işlemlerden sorguları ve ViewModels (özellikle istemci uygulamaları için oluşturulan veri modelleri) bölünmüş olmasıdır. Bu yaklaşım, sorguları, sonraki bölümlerde açıklandığı gibi yalnızca hareketler ve güncelleştirmeler için anlamlı olan DDD desenlerinden gelen kısıtlamalardan ve kısıtlamalardan bağımsız tutar.

## <a name="additional-resources"></a>Ek kaynaklar

- **Greg Young' ı. Bir Olay Kaynaklı Sistemde Sürüm** (Online e-kitap okumak için ücretsiz) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](eshoponcontainers-cqrs-ddd-microservice.md)
