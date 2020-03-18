---
title: Mikro hizmet başına veri hakimiyeti
description: Mikro hizmet başına veri egemenliği, mikro hizmetlerin kilit noktalarından biridir. Her microservice kendi veritabanının tek sahibi olmalı, başka bir ile paylaşan. Tabii ki bir microservice tüm örnekleri aynı yüksek kullanılabilirlik veritabanına bağlayın.
ms.date: 09/20/2018
ms.openlocfilehash: f606d6314f38bf3e2c163871af432806dddc7446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73191912"
---
# <a name="data-sovereignty-per-microservice"></a>Mikro hizmet başına veri hakimiyeti

Mikro hizmetler mimarisi için önemli bir kural, her microservice kendi etki alanı veri ve mantık sahibi olması gerektiğidir. Tam bir uygulamanın kendi mantığına ve verilerine sahip olması gibi, her mikro hizmet in kendi mantığına ve verilerine, mikro hizmet başına bağımsız dağıtımla özerk bir yaşam döngüsü altında sahip olmalıdır.

Bu, etki alanının kavramsal modelinin alt sistemler veya mikro hizmetler arasında farklılık olacağı anlamına gelir. Müşteri ilişkileri yönetimi (CRM) uygulamalarının, işlemsel satın alma alt sistemlerinin ve müşteri destek alt sistemlerinin her birinin benzersiz müşteri varlık öznitelikleri ve verilerini aradığı ve her birinin farklı bir Sınırlanmış Bağlam (BC).

Bu ilke, her [Sınırlı Bağlam](https://martinfowler.com/bliki/BoundedContext.html) veya özerk alt sistem veya hizmetin etki alanı modeline (veri artı mantık ve davranış) sahip olması gereken Etki Alanı [tabanlı tasarımda (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)benzerdir. Her DDD Sınırlı Bağlam, bir iş microservice (bir veya birkaç hizmet) ile ilişkilidir. Bağlı Bağlam deseni yle ilgili bu nokta sonraki bölümde genişletilir.

Öte yandan, birçok uygulamada kullanılan geleneksel (yekpare veri) yaklaşımı tek bir merkezi veritabanı veya sadece birkaç veritabanları olmasıdır. Bu genellikle Şekil 4-7'de gösterildiği gibi, tüm uygulama ve tüm dahili alt sistemleri için kullanılan normalleştirilmiş bir SQL veritabanıdır.

![İki veritabanı yaklaşımını güsteren diyagram.](./media/data-sovereignty-per-microservice/data-sovereignty-comparison.png)

**Şekil 4-7**. Veri egemenliği karşılaştırması: monolitik veritabanı ve mikrohizmetler

Geleneksel yaklaşımda, genellikle katmanlı mimaride tüm hizmetler arasında paylaşılan tek bir veritabanı vardır. Mikro hizmetler yaklaşımında, her microservice kendi modeline/verilerine sahip. Merkezi leştirilmiş veritabanı yaklaşımı başlangıçta daha basit görünür ve her şeyi tutarlı hale getirmek için farklı alt sistemlerdeki varlıkların yeniden kullanılmasını sağlar gibi görünür. Ama gerçek şu ki, birçok farklı alt sistemlere hizmet veren ve çoğu durumda gerekli olmayan öznitelikleri ve sütunları içeren büyük tablolarla sonuçlanır. Kısa bir patikada yürüyüş yapmak, bir günlük araba gezisi yapmak ve coğrafya öğrenmek için aynı fiziksel haritayı kullanmaya çalışmak gibi.

Genellikle tek bir ilişkisel veritabanına sahip yekpare bir uygulamanın iki önemli faydası vardır: [ASİt hareketleri](https://en.wikipedia.org/wiki/ACID) ve SQL dili, hem uygulamanızla ilgili tüm tablolarda hem de verilerde çalışır. Bu yaklaşım, birden çok tablodaki verileri birleştiren bir sorguyazmak için kolayca bir yol sağlar.

Ancak, bir mikro hizmetler mimarisine geçtikçe veri erişimi çok daha karmaşık hale gelir. Bir microservice veya Bounded Context içinde ACID işlemleri kullanırken bile, her bir mikro hizmete ait verilerin bu mikro hizmete özel olduğunu ve yalnızca API uç noktaları üzerinden eşzamanlı olarak erişilmesi gerektiğini göz önünde bulundurmak önemlidir (REST, gRPC, SOAP, vb) veya mesajlaşma (AMQP veya benzeri) yoluyla eşzamanlı olarak.

Verilerin kapsüllemesi, mikro hizmetlerin gevşek bir şekilde birleştiğini ve birbirinden bağımsız olarak evrimleşebilmesini sağlar. Birden çok hizmet aynı verilere erişiyorsa, şema güncelleştirmeleri tüm hizmetler için eşgüdümlü güncelleştirmeler gerektirir. Bu mikrohizmet yaşam döngüsü özerkliğini kıracak. Ancak dağıtılmış veri yapıları, mikro hizmetler arasında tek bir ASİt işlemi yapamadığınız anlamına gelir. Bu da, bir iş süreci birden çok mikro hizmeti kapsadığında nihai tutarlılığı kullanmanız gerektiği anlamına gelir. Bunu uygulamak basit SQL birleşimlerinden çok daha zordur, çünkü daha sonra açıklayacağımız gibi, bütünlük kısıtlamaları oluşturamaz veya ayrı veritabanları arasında dağıtılmış hareketler kullanamazsınız. Benzer şekilde, diğer birçok ilişkisel veritabanı özelliği birden çok mikro hizmette kullanılamaz.

Daha da ileri giderek, farklı mikro hizmetler genellikle farklı *veritabanları kullanır.* Modern uygulamalar çeşitli veri türlerini depolar ve işlenir ve ilişkisel veritabanı her zaman en iyi seçim değildir. Bazı kullanım durumlarında, Azure CosmosDB veya MongoDB gibi bir NoSQL veritabanı daha kullanışlı bir veri modeline sahip olabilir ve SQL Server veya Azure SQL Veritabanı gibi bir SQL veritabanından daha iyi performans ve ölçeklenebilirlik sunabilir. Diğer durumlarda, ilişkisel bir veritabanı hala en iyi yaklaşımdır. Bu nedenle, mikrohizmet tabanlı uygulamalar genellikle bazen [çokdilli kalıcılık](https://martinfowler.com/bliki/PolyglotPersistence.html) yaklaşımı olarak adlandırılan SQL ve NoSQL veritabanlarının bir karışımını kullanır.

Veri depolama için bölümlenmiş, çok dilli kalıcı mimarinin birçok faydası vardır. Bunlar arasında gevşek birleştirilmiş hizmetler ve daha iyi performans, ölçeklenebilirlik, maliyetler ve yönetilebilirlik yer almaktadır. Ancak, bu bölümün ilerleyen bölümlerinde " Etki[alanı modeli sınırlarını belirleme"](identify-microservice-domain-model-boundaries.md)bölümünde açıklandığı gibi, bazı dağıtılmış veri yönetimi zorlukları getirebilir.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Mikro hizmetler ve Sınırlı Bağlam deseni arasındaki ilişki

Mikrohizmet [kavramı, etki alanı odaklı tasarımda (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design) [Sınırlı Bağlam (BC) deseninden](https://martinfowler.com/bliki/BoundedContext.html) türetilmiştir. DDD, büyük modelleri birden çok BC'ye bölerek ve sınırları hakkında açık olarak ele alar. Her BC'nin kendi modeli ve veritabanı olmalıdır; aynı şekilde, her microservice kendi ilgili verilere sahip. Buna ek olarak, her BC genellikle yazılım [geliştiricileri](https://martinfowler.com/bliki/UbiquitousLanguage.html) ve etki alanı uzmanları arasındaki iletişimyardımcı olmak için kendi her yerde dil vardır.

Her yerde bulunan dildeki bu terimler (özellikle etki alanı varlıkları), farklı etki alanı varlıkları aynı kimliği paylaşsa bile (diğer bir deyişle, varlığı depolamadan okumak için kullanılan benzersiz kimlik) farklı Bağlı Bağlamlarda farklı adlara sahip olabilir. Örneğin, kullanıcı profili Sınırlanmış Bağlam'da, Kullanıcı etki alanı varlığı, Sınırlı Bağlam'ı sıralayan alan varlığında kimliği Alıcı etki alanı varlığıyla paylaşabilir.

Bir microservice bu nedenle Sınırlı Bağlam gibidir, ancak dağıtılmış bir hizmet olduğunu da belirtir. Her Bağlı Bağlam için ayrı bir işlem olarak oluşturulmuştur ve http/HTTPS, WebSockets veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)gibi daha önce belirtilen dağıtılmış protokolleri kullanmalıdır. Ancak, Sınırlandırılmış Bağlam deseni, Sınırlandırılmış Bağlam'ın dağıtılmış bir hizmet olup olmadığını veya tek şey liyakatli dağıtım uygulaması içinde yalnızca mantıksal bir sınır (genel bir alt sistem gibi) olup olmadığını belirtmez.

Her Bağlı Bağlam için bir hizmet tanımlamanın başlamak için iyi bir yer olduğunu vurgulamak önemlidir. Ama tasarımınızı buna kısıtlamak zorunda değilsiniz. Bazen, çeşitli fiziksel hizmetlerden oluşan Bir Sınırlı Bağlam veya iş microservice tasarlamanız gerekir. Ama sonuçta, her iki desen -Sınırlı Bağlam ve microservice- yakından ilişkilidir.

DDD, dağıtılmış mikro hizmetler şeklinde gerçek sınırlar elde ederek mikro hizmetlerden yararlanır. Ancak modeli mikro hizmetler arasında paylaşmamak gibi fikirler, Sınırlı Bağlamda da istediğiniz şeydir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Chris Richardson' ı. Desen: Hizmet başına veritabanı** \
  <https://microservices.io/patterns/data/database-per-service.html>

- **Martin Fowler' ı. Sınırlı Bağlam** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Martin Fowler' ı. PoliglotKalıcılık** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Bağlam Haritalama ile Stratejik Etki Alanı Odaklı Tasarım** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Önceki](microservices-architecture.md)
>[Sonraki](logical-versus-physical-architecture.md)
