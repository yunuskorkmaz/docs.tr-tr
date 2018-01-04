---
title: "Mikro hizmet başına veri egemenliği"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro hizmet başına veri egemenliği"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76265490d7cb0d53686b43b88cb797cf887d578a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="data-sovereignty-per-microservice"></a>Mikro hizmet başına veri egemenliği

Mikro mimarisi için önemli bir kuralı her mikro hizmet kendi etki alanı verileri ve mantığı ait olduğu ' dir. Bu nedenle tam bir uygulama mantığı ve verileri yalnızca sahip olduğu gibi her mikro hizmet mantığı ve verileri mikro hizmet başına bağımsız dağıtımla otonom bir yaşam döngüsü altında sahip olmanız gerekir.

Başka bir deyişle, etki alanının kavramsal model alt sistemleri veya mikro arasında farklılık gösterir. Kuruluş uygulamaları Müşteri İlişkileri Yönetimi (CRM) uygulamaları, işlem benzersiz Müşteri varlık öznitelikleri ve verileri her çağrıda satın alma, alt sistemleri ve müşteri destek alt sistemleri ve her farklı bir kullanan burada göz önünde bulundurun Sınırlanmış bağlamı (BC).

Bu ilkeyi benzer [etki alanı Odaklı Tasarım (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), burada her [ilişkisindeki bağlam](https://martinfowler.com/bliki/BoundedContext.html) veya otonom alt sistemi veya hizmet kendi etki alanı modeli (verileri artı mantığı ve davranış) sahip olmalıdır. İlişkisindeki her DDD bağlam karşılık gelen bir iş mikro (bir veya birkaç hizmet). (Biz bu noktasında sonraki bölümde ilişkisindeki bağlam desen hakkında genişletin.)

Öte yandan, birçok uygulamada kullanılan geleneksel (tek yapılı veri) tek bir merkezi veritabanı veya yalnızca birkaç veritabanlarına sahip yaklaşımdır. Bu, tüm uygulama ve tüm kendi iç alt sistemleri, kullanılan normalleştirilmiş bir SQL veritabanı Şekil 4-7'de gösterildiği gibi görülür.

![](./media/image7.png)

**Şekil 4-7**. Veri egemenliği karşılaştırması: tek yapılı veritabanı mikro karşılaştırması

Merkezi veritabanı yaklaşım başlangıçta daha basit arar ve her şeyi tutarlı yapmak için farklı alt sistemleri varlıklarda kullanılmasını etkinleştirme gibi görünüyor. Ancak gerçekte, birçok farklı alt sistemleri hizmet eden ve çoğu durumda öznitelikleri ve gerekli olmayan sütunları içeren büyük tabloları şunun. Bu, aynı fiziksel eşlemesi kısa izi yürüyüş, bir gün uzun araba seyahat alma ve Coğrafya öğrenme kullanmaya çalışıyor gibi olur.

Genellikle tek bir ilişkisel veritabanı tek yapılı bir uygulamayla iki önemli faydası vardır: [ACID işlemlerini](https://en.wikipedia.org/wiki/ACID) ve SQL dili, tüm tabloları ve uygulamanız ile ilgili veriler arasında her iki çalışma. Bu yaklaşım kolayca birden fazla tablolardaki verileri birleştiren bir sorgu yazmak için bir yol sağlar.

Ancak, bir mikro mimarisi taşıdığınızda veri erişimi çok daha karmaşık hale gelir. Ancak ACID işlemlerini olabilir veya bir mikro hizmet veya sınırlanmış bağlam içinde kullanılmalıdır olsa bile, her mikro hizmet tarafından ait verileri bu mikro hizmet özeldir ve yalnızca kendi mikro hizmet API üzerinden erişilebilir. Veri şifreleme mikro birbirine sıkı şekilde bağlı ve başka bağımsız olarak gelişmesi sağlar. Birden fazla hizmeti aynı verilere erişilirken, şema güncelleştirmeleri koordine güncelleştirmeleri tüm hizmetlere gerektirir. Bu mikro hizmet yaşam döngüsü otonomisi çalışmamasına neden. Ancak mikro arasında tek bir ACID işlemi yapamazsınız Dağıtılmış veri yapılarını anlamına gelir. Bu sırayla bir iş sürecini birden çok mikro yayıldığında nihai tutarlılık kullanmalısınız anlamına gelir. Bu basit SQL birleştirmeler uygulamak çok daha zordur; benzer şekilde, diğer birçok ilişkisel veritabanı özellikleri arasında birden çok mikro kullanılabilir değil.

Bile devam edilirse, farklı mikro genellikle farklı kullandığınız *tür* veritabanlarının. Modern uygulamalar depolama ve işlem farklı veri türlerini ve ilişkisel veritabanı değil her zaman en iyi seçenek. Bazı için kullanım örnekleri, bir NoSQL veritabanı Azure DocumentDB veya MongoDB gibi daha kullanışlı bir veri modeline sahiptir ve daha iyi performans ve ölçeklenebilirlik SQL Server gibi bir SQL veritabanı ya da Azure SQL veritabanı sağlar. Diğer durumlarda, bir ilişkisel veritabanı hala en iyi yaklaşımdır. Bu nedenle, mikro tabanlı uygulamalar bazen olarak adlandırılan bir karışımını NoSQL ve SQL veritabanları, sık kullandığınız [polyglot kalıcılığı](http://martinfowler.com/bliki/PolyglotPersistence.html) yaklaşım.

Veri depolama için bir bölümlenmiş, polyglot kalıcı mimarisini birçok avantaj vardır. Bunlar, geniş bağlı hizmetleri ve daha iyi performans, ölçeklenebilirlik, maliyetleri ve yönetilebilirlik içerir. Ancak, biz de anlatılmıştır gibi bazı Dağıtılmış veri yönetimi zorluklar getirebilir "[etki alanı modeli sınırları tanımlama](#identifying-domain-model-boundaries-for-each-microservice)" Bu bölümde daha sonra.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Mikro ve sınırlanmış içerik düzeni arasındaki ilişki

Mikro hizmet kavramını türetilen [ilişkisindeki bağlam (BC) deseni](http://martinfowler.com/bliki/BoundedContext.html) içinde [etki alanı Odaklı Tasarım (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD birden çok BCs bölme ve bunların sınırlarını hakkında açık büyük modelleri ile ilgilidir. Her BC kendi modeli ve veritabanı olmalıdır; benzer şekilde, her mikro hizmet ilgili verileri sahip olur. Ayrıca, her BC genellikle kendi sahip [bulunabilen dil](http://martinfowler.com/bliki/UbiquitousLanguage.html) yazılım geliştiricileri ve etki alanı uzmanlar arasındaki iletişimi yardımcı olacak.

Her yerden dilde ilgili koşullar (çoğunlukla etki alanı varlıklar) farklı ilişkisindeki bağlamlarda farklı adlara sahip, aynı kimliğe (depolama biriminden varlık okumak için kullanılan diğer bir deyişle, benzersiz kimliği) bile farklı etki alanı varlıkları paylaşın. Örneğin, sipariş ilişkisindeki bağlamda alıcı etki alanı varlığı ile kullanıcı profili sınırlanmış bir bağlamında, kullanıcı etki alanı varlığı kimlik paylaşabilen.

Bir mikro hizmet bu nedenle bir sınırlanmış bağlamı gibi olmakla birlikte, aynı zamanda Dağıtılmış bir hizmet olduğunu belirtir. İlişkisindeki her bağlam için ayrı bir işlem olarak oluşturulur ve HTTP/HTTPS gibi WebSockets, daha önce not ettiğiniz dağıtılmış protokolleri kullanması gerekir veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Sınırlanmış içerik düzeni ancak ilişkisindeki bağlam dağıtılmış bir hizmet olup olmadığı veya yalnızca mantıksal sınır (örneğin, bir genel alt sistemi) olup olmadığını dağıtım tek yapılı uygulama içinde belirtmiyor.

İlişkisindeki her bağlam için bir hizmet tanımlama başlatmak için uygun bir yerdir, vurgulamak önemlidir. Ancak ona tasarımınızı sınırlamak gerekmez. Bazen bir sınırlanmış bağlamı tasarlamanız gerekir veya iş mikro birkaç fiziksel hizmetlerinden oluşur. Ancak sonuç olarak, her iki desenleri — ilişkisindeki bağlamını ve mikro hizmet — yakından ilişkilidir.

GGG, dağıtılmış mikro biçiminde gerçek sınırları alarak mikro fayda sağlar. Ancak mikro arasında modeli paylaşmıyor gibi fikirleri ne de sınırlı bir bağlamda istiyorsunuz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Chris Uludağ. Desen: Veritabanı Hizmet**
    [*http://microservices.io/patterns/data/database-per-service.html*](http://microservices.io/patterns/data/database-per-service.html)

-   **Martin Fowler. BoundedContext**
    [*http://martinfowler.com/bliki/BoundedContext.html*](http://martinfowler.com/bliki/BoundedContext.html)

-   **Martin Fowler. PolyglotPersistence**
    [*http://martinfowler.com/bliki/PolyglotPersistence.html*](http://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Adı Brandolini. Yönetilen bir bağlam eşleme ile tasarım stratejik etki alanı**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[Önceki] (mikro-architecture.md) [sonraki] (mantıksal-karşı-fiziksel-architecture.md)
