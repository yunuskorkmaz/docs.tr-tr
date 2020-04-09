---
title: Mikro hizmet uygulama katmanı ve Web API’sini tasarlama
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Uygulama katmanının tasarımına ilişkin SOLID ilkelerinden kısa bir söz.
ms.date: 10/08/2018
ms.openlocfilehash: 491aa7bd90910c7f6c1d0ab56edfe0ae057ca006
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988459"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Mikro hizmet uygulama katmanını ve Web API'sini tasarlayın

## <a name="use-solid-principles-and-dependency-injection"></a>SOLID prensipleri ve Bağımlılık Enjeksiyonu kullanın

SOLID ilkeleri, DDD desenli bir mikro hizmet geliştirmek gibi her türlü modern ve görev açısından kritik uygulamada kullanılacak kritik tekniklerdir. SOLID, beş temel ilkeyi bir arada gösteren bir kısaltmadır:

- Tek Sorumluluk ilkesi

- Açık/kapalı ilke

- Liskov ikame ilkesi

- Arayüz Ayrımı ilkesi

- Bağımlılık Ters Çevirme ilkesi

SOLID, uygulamanızı veya microservice iç katmanlarınızı nasıl tasarladığınız ve aralarındaki bağımlılıkları nasıl ayırdığınızla ilgilidir. Etki alanıyla değil, uygulamanın teknik tasarımıyla ilgilidir. Son ilke, Bağımlılık Inversion ilkesi, DDD katmanlarıdaha iyi bir ayrılmış uygulama sağlar katmanları, geri kalanından altyapı katmanı ayırmak için izin verir.

Bağımlılık Enjeksiyon (DI) Bağımlılık Inversion ilkesini uygulamak için bir yoldur. Bu nesneler ve onların bağımlılıkları arasında gevşek bağlantı elde etmek için bir tekniktir. İşbirlikçileri doğrudan anında kullanmak veya statik başvuruları kullanmak (diğer bir deyişle yeni...) kullanmak yerine, bir sınıfın eylemlerini gerçekleştirmek için ihtiyaç duyduğu nesneler sınıfa sağlanır (veya "enjekte edilir"). Çoğu zaman, sınıflar bağımlılıklarını yapıcıları aracılığıyla beyan ederek Açık Bağımlılıklar ilkesine uymalarını sağlarlar. Bağımlılık Enjeksiyonu genellikle kontrol (IoC) kaplarının belirli ters çevrilmelerine dayanır. ASP.NET Core basit bir dahili IoC konteyner sağlar, ancak autofac veya Ninject gibi en sevdiğiniz IoC konteyner kullanabilirsiniz.

SOLID ilkelerini izleyerek, sınıflarınız doğal olarak küçük, iyi faktörlü ve kolayca test edilebilir olma eğiliminde olacaktır. Ama sınıflarınıza çok fazla bağımlılık enjekte edilip edilip edilmeyişemelerini nasıl bilebilirsiniz? Di'yi oluşturucu aracılığıyla kullanırsanız, bunu sadece oluşturucunuz için parametrelerin sayısına bakarak algılamak kolay olacaktır. Çok fazla bağımlılık varsa, bu genellikle bir işaret [(kod kokusu)](https://deviq.com/code-smells/)sınıf çok fazla yapmaya çalışıyor ve büyük olasılıkla Tek Sorumluluk ilkesini ihlal ediyor.

Bu ayrıntılı olarak SOLID kapsayacak şekilde başka bir rehber alacaktı. Bu nedenle, bu kılavuz, bu konular hakkında yalnızca en az bilgiye sahip olmayı gerektirir.

#### <a name="additional-resources"></a>Ek kaynaklar

- **SOLID: Temel OOP İlkeleri** \
  <https://deviq.com/solid/>

- **Kontrol Kaplarının Ters Çevrilmesi ve Bağımlılık Enjeksiyonu deseni** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith' i. Yeni Tutkal olduğunu** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Önceki](nosql-database-persistence-infrastructure.md)
> [Sonraki](microservice-application-layer-implementation-web-api.md)
