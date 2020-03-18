---
title: Bulut-yerel uygulamalarda elastik arama
description: Bulut taşıyıcı uygulamalara Elastik Arama özellikleri ekleme ü
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 1bce255b6315006b11e0b6ac77040300f67ed984
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141295"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Bulut ayarı uygulamasında elasticsearch

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elasticsearch, farklı veri türleri arasında karmaşık arama yetenekleri sağlayan dağıtılmış bir arama ve analiz sistemidir. Açık kaynak ve yaygın olarak popüler. Aşağıdaki şirketlerin Elasticsearch'u uygulamalarına nasıl entegre ettiklerine göz önünde bulundurun:

- Tam metin ve artımlı (yazarken arama) arama için [Vikipedi.](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)
- [GitHub,](https://www.elastic.co/customers/github) 8 milyondan fazla kod deposunu dizine ekleyip ortaya çıkarır.  
- Konteyner kütüphanesini keşfedilebilir hale getirmek için [Docker.](https://www.elastic.co/customers/docker)

[Elasticsearch, Apache Lucene](https://lucene.apache.org/core/) tam metin arama motorunun üzerine inşa edilmiştir. Lucene yüksek performanslı belge dizini ve sorgusağlar. Verileri ters bir dizin oluşturma şemasıyla dizine alır – sayfaları anahtar kelimelerle eşlemek yerine, anahtar kelimeleri kitabın sonundaki bir sözlük gibi sayfalara eşler. Lucene güçlü sorgu sözdizimi yeteneklerine sahiptir ve verileri şu şekilde sorgulayabilir:

- Terim (tam kelime)
- Önek (sözcük ile başlar)
- Joker karakter (" "\*veya "?" filtreleri kullanarak)
- Tümcecik (belgedeki metin sırası)
- Boolean değeri (sorguları birleştiren karmaşık aramalar)

Lucene arama için düşük seviyeli sıhhi tesisat sağlarken, Elasticsearch Lucene üstüne oturur sunucu sağlar. Elasticsearch, Lucene'nin dizin oluşturma ve arama işlevlerine erişmek için yeniden yapılan api de dahil olmak üzere, lucene'nin çalışmasını basitleştirmek için daha üst düzey işlevsellik ekler. Ayrıca, büyük ölçeklenebilirlik, hata toleransı ve yüksek kullanılabilirlik yeteneğine sahip dağıtılmış bir altyapı sağlar.

Karmaşık arama gereksinimlerine sahip daha büyük bulut yerel uygulamalar için Elasticsearch, Azure'da yönetilen hizmet olarak kullanılabilir. Microsoft Azure Marketi, geliştiricilerin Azure'da Bir Elasticsearch kümesidağıtmak için kullanabilecekleri önceden yapılandırılmış şablonlar sunar.

Geliştiriciler, Microsoft Azure Marketi'nden, Azure'da Elasticsearch kümesini hızla dağıtmak için önceden yapılandırılmış şablonlar kullanabilir. Azure tarafından yönetilen teklifi kullanarak, en fazla 50 veri düğümü, 20 eşgüdüm düğümü ve üç özel ana düğüm dağıtabilirsiniz.

## <a name="summary"></a>Özet

Bu bölümde bulut ayarı sistemlerdeki verilere ayrıntılı bir bakış sunulmuştur. Bulut ait sistemlerdeki veri depolama desenleri ile yekpare uygulamalarda veri depolamayı karşılaştırarak başladık. Yüksek hacimli sistemlerle başa çıkmak için çapraz hizmet sorguları, dağıtılmış işlemler ve desenler de dahil olmak üzere bulut ayarı sistemlerinde uygulanan veri kalıplarına baktık. SQL ile NoSQL verileri arasında zıtlık yaptık. Azure'da hem Microsoft merkezli hem de açık kaynak seçenekleri içeren veri depolama seçeneklerini inceledik. Son olarak, bir bulut-yerel uygulamada önbelleğe alma ve Elasticsearch tartışıldı.

### <a name="references"></a>Başvurular

- [Komut ve Sorgu Sorumluluğu Ayrımı (CQRS) deseni](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Olay Kaynak deseni](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [RDBMSs vs. NoSQL Veritabanları: Genel Bakış](https://maxivak.com/rdbms-vs-nosql-databases/)

- [NEDEN CAP Teoremi'nde RDBMS Bölüm toleranslı değildir ve neden kullanılabilir?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Materyalize Görünüm](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Tüm gerçekten açık kaynak veritabanları hakkında bilmeniz gereken](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Telafi İşlemi deseni](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Destan Deseni](https://microservices.io/patterns/data/saga.html)

- [Destan Desenleri | Mikro hizmetleri kullanarak ticari işlemler nasıl uygulanır?](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Telafi İşlemi deseni](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [9-Top Arkasında Başlarken: Cosmos DB Tutarlılık Düzeyleri Açıkladı](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [NoSQL Veritabanları Bölüm II farklı türde keşfetmek](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [RDBMS, NoSQL ve NewSQL veritabanlarında. John Ryan ile röportaj](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: Tam Karşılaştırma](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH: Kubernetes-Native Veritabanları dört özellikleri](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [Hamamböceği](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elasticsearch: Definitive Kılavuzu](http://shop.oreilly.com/product/0636920028505.do)
  
- [Apache Lucene'ye Giriş](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Önceki](azure-caching.md)
>[Sonraki](resiliency.md) <!-- Next Chapter -->
