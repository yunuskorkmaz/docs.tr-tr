---
title: Mikro hizmet başına veri hakimiyeti
description: Mikro hizmet başına veri egementy, mikro hizmetlerin önemli noktalarından biridir. Her mikro hizmet veritabanının tek sahibi olmalıdır ve onu başka hiçbir olmadan paylaşmalıdır. Tabii ki, bir mikro hizmetin tüm örnekleri aynı yüksek kullanılabilirlik veritabanına bağlanır.
ms.date: 09/20/2018
ms.openlocfilehash: cd7be23800394b231e15bdc503d15a960a25a20a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "70296806"
---
# <a name="data-sovereignty-per-microservice"></a>Mikro hizmet başına veri hakimiyeti

Mikro hizmetler mimarisi için önemli bir kural, her mikro hizmetin kendi etki alanı verilerine ve mantığına sahip olması gerekir. Tam bir uygulamanın Logic ve verilerinin sahibi olduğu için, her mikro hizmetin kendi mantığını ve verileri, mikro hizmet başına bağımsız dağıtım ile bir otonom yaşam döngüsü altında sahip olması gerekir.

Bu, etki alanı kavramsal modelinin alt sistemler veya mikro hizmetler arasında farklı olacağı anlamına gelir. Müşteri ilişkileri yönetimi (CRM) uygulamaları, işlem satın alma alt sistemleri ve müşteri destek alt sistemlerinin her biri benzersiz müşteri varlığı öznitelikleri ve verileri üzerinde her çağrının ve her birinin farklı bir şekilde kullanıldığı kurumsal uygulamaları göz önünde bulundurun. Sınırlanmış bağlam (BC).

Bu ilke, her [sınırlanmış bağlam](https://martinfowler.com/bliki/BoundedContext.html) veya özerk alt sistem ya da hizmetin kendi etki alanı modeline sahip olması gerektiği [etki alanı ODAKLı tasarım (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)ile benzerdir (veri ve mantık ve davranış). Her DDD sınırlı bağlam, bir iş mikro hizmeti (bir veya birkaç hizmet) ile ilişkili. Sınırlanmış bağlam deseninin bu noktası sonraki bölümde genişletilir.

Diğer taraftan, birçok uygulamada kullanılan geleneksel (tek parçalı veriler) yaklaşımının tek bir merkezi veritabanı veya yalnızca birkaç veritabanı olması gerekir. Bu genellikle Şekil 4-7 ' de gösterildiği gibi, tüm uygulama ve tüm iç alt sistemleri için kullanılan normalleştirilmiş bir SQL veritabanıdır.

![Geleneksel yaklaşımda, genellikle katmanlı bir mimaride tüm hizmetler genelinde paylaşılan tek bir veritabanı vardır. Mikro hizmetler yaklaşımında her mikro hizmet modelin/verilerinin sahibi olur](./media/image7.png)

**Şekil 4-7**. Veri egemenlik karşılaştırması: tek parçalı veritabanı ve mikro hizmetler karşılaştırması

Merkezi veritabanı yaklaşımı başlangıçta daha basit bir şekilde görünür ve her şeyi tutarlı hale getirmek için farklı alt sistemlerde varlıkların yeniden kullanımını etkinleştirmek gibi görünüyor. Ancak gerçekliği, birçok farklı alt sistemi sunan ve çoğu durumda gerekmeyen öznitelikleri ve sütunları içeren çok büyük tablolar ile sona erdirmek ister. Kısa bir izleme için aynı fiziksel eşlemeyi kullanmaya çalışmak, gün uzunluğunda bir otomobil yolculuğu ve öğrenme Coğrafya almak gibidir.

Genellikle tek bir ilişkisel veritabanına sahip tek parçalı bir uygulama iki önemli avantaja sahiptir: [ACID işlemleri](https://en.wikipedia.org/wiki/ACID) ve SQL dili, her ikisi de uygulamanızla ilgili tüm tablolar ve veriler üzerinde çalışır. Bu yaklaşım, birden çok tablodan verileri birleştiren bir sorguyu kolayca yazmak için bir yol sağlar.

Ancak, mikro hizmetler mimarisine geçtiğinizde veri erişimi çok daha karmaşık hale gelir. Ancak, bir mikro hizmet veya sınırlı bağlam içinde ACID işlemleri de kullanılabilir olduğunda bile, her bir mikro hizmetin sahip olduğu veriler bu mikro hizmete özeldir ve yalnızca mikro hizmet API 'SI aracılığıyla erişilebilir. Verilerin kapsüllenmesi, mikro hizmetlerin gevşek bir şekilde bağlanmış olmasını sağlar ve birbirinden bağımsız olarak gelişebilirler. Aynı verilere birden çok hizmet erişiyorsa, şema güncelleştirmeleri tüm hizmetlere yönelik Eşgüdümlü güncelleştirmeler gerektirir. Bu, mikro hizmet yaşam döngüsü bağımsız çalışma sınırı kesintiye uğratır. Ancak dağıtılmış veri yapıları, mikro hizmetler genelinde tek bir ACID işlemi yapamayacağınız anlamına gelir. Buna karşılık, bir iş süreci birden çok mikro hizmete yayıldığında nihai tutarlılığı kullanmanız gerekir. Bu, daha sonra açıklandığımız gibi, bütünlük kısıtlamaları oluşturamadığından veya ayrı veritabanları arasında dağıtılmış işlemler kullanamadığından basit SQL birleştirmelere uygulama çok daha zordur. Benzer şekilde, çok sayıda diğer ilişkisel veritabanı özelliği birden fazla mikro hizmette kullanılamaz.

Daha da farklı mikro hizmetler, genellikle farklı *türlerde* veritabanları kullanır. Modern uygulamalar çeşitli veri türlerini depolar ve işler ve ilişkisel veritabanı her zaman en iyi seçenektir. Bazı kullanım durumları için, Azure CosmosDB veya MongoDB gibi bir NoSQL veritabanının daha uygun bir veri modeli olabilir ve SQL Server veya Azure SQL veritabanı gibi bir SQL veritabanından daha iyi performans ve ölçeklenebilirlik sunar. Diğer durumlarda, ilişkisel bir veritabanı hala en iyi yaklaşımdır. Bu nedenle, mikro hizmet tabanlı uygulamalar genellikle [çok yönlü Kalıcılık](https://martinfowler.com/bliki/PolyglotPersistence.html) yaklaşımı olarak adlandırılan SQL ve NoSQL veritabanlarının bir karışımını kullanır.

Veri depolama için bölümlenmiş, çok yönlü kalıcı mimarinin birçok avantajı vardır. Bunlar arasında gevşek olarak bağlanmış hizmetler, daha iyi performans, ölçeklenebilirlik, maliyetler ve yönetilebilirlik bulunur. Ancak, bu bölümün devamındaki "[etki alanı model sınırlarını tanımlama](identify-microservice-domain-model-boundaries.md)" bölümünde açıklandığı gibi bazı dağıtılmış veri yönetimi sorunlarını ortaya çıkarabilir.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Mikro hizmetler ve sınırlanmış bağlam deseninin arasındaki ilişki

Mikro hizmet kavramı, [etki alanı odaklı tasarımda (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design) [SıNıRLANMıŞ bağlam (BC)](https://martinfowler.com/bliki/BoundedContext.html) düzeninden türetilir. DDD, büyük modellerle anlaşmalar yaparak bunları birden çok BCs dönüştürür ve sınırları hakkında açık bir şekilde yapılır. Her bir BC kendi modeli ve veritabanına sahip olmalıdır; benzer şekilde, her mikro hizmet ilgili verilerin sahibidir. Ayrıca, her bir BC yazılım geliştiricileri ve etki alanı uzmanları arasındaki iletişime yardımcı olmak için genellikle kendi [ubititous diline](https://martinfowler.com/bliki/UbiquitousLanguage.html) sahiptir.

Ubititous dilinde söz konusu şartlar (genellikle etki alanı varlıkları) farklı sınırlanmış bağlamlarda farklı adlara sahip olabilir, farklı etki alanı varlıkları aynı kimliği paylaşır (yani, varlığı depolamadan okumak için kullanılan benzersiz KIMLIK). Örneğin, Kullanıcı profili sınırlı bağlamında, Kullanıcı etki alanı varlığı, kimlik sıralama bağlantılı bağlamdaki alıcı etki alanı varlığı ile kimlik paylaşabilir.

Bu nedenle, bir mikro hizmet sınırlanmış bir bağlam gibidir, ancak aynı zamanda dağıtılmış bir hizmet olduğunu da belirtir. Her sınırlanmış bağlam için ayrı bir işlem olarak oluşturulmuştur ve HTTP/HTTPS, WebSockets veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)gibi daha önce belirtilen dağıtılmış protokolleri kullanmalıdır. Bununla sınırlı bağlam deseninin, bir tek parçalı dağıtım uygulaması içinde, sınırlanmış bağlamın dağıtılmış bir hizmet olup olmadığını ya da yalnızca bir mantıksal sınır (genel alt sistem gibi) belirtilmediğini belirtmez.

Her sınırlanmış bağlam için bir hizmet tanımlamanın başlamak için iyi bir yerdir. Ancak tasarımınızı buna karşı kısıtlamak zorunda değilsiniz. Bazen, birkaç fiziksel hizmetten oluşan sınırlı bir bağlam veya iş mikro hizmeti tasarlamanız gerekir. Ancak, her ikisi de desenler ile sınırlanmış bağlam ve mikro hizmet ile yakından ilgilidir.

, Dağıtılmış mikro hizmetler biçiminde gerçek sınırlar alarak mikro hizmetlerden faydalanır. Bununla birlikte, mikro hizmetler arasında modeli paylaşmayan fikirler da sınırlanmış bir bağlamda olmasını istediğiniz şeydir.

### <a name="additional-resources"></a>Ek kaynaklar

- **Chris Richardson. Kalıp Hizmet başına veritabanı** \
  <https://microservices.io/patterns/data/database-per-service.html>

- **Marwler. BoundedContext** \
  <https://martinfowler.com/bliki/BoundedContext.html>

- **Marwler. PolyglotPersistence** \
  <https://martinfowler.com/bliki/PolyglotPersistence.html>

- **Alberto Brandolini. Bağlam eşleme ile stratejik etki alanı odaklı tasarım** \
  <https://www.infoq.com/articles/ddd-contextmapping>

>[!div class="step-by-step"]
>[Önceki](microservices-architecture.md)İleri
>[](logical-versus-physical-architecture.md)
