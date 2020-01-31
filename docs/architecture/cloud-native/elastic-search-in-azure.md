---
title: Bulutta yerel uygulamalarda elaun arama
description: Bulutta yerel uygulamalara elastik arama özellikleri ekleme hakkında bilgi edinin.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 6ea237eddc89a8c6843d6b34b05b1b71515a99b6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794879"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Bulutta yerel bir uygulamada elaun arama

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elaun Search, farklı türlerde veriler arasında karmaşık arama özellikleri sağlayan bir dağıtılmış arama ve analiz sistemidir. Açık kaynak ve yaygın popüler. Aşağıdaki şirketlerin, Elai aramasını kendi uygulamasına nasıl tümleştirtireceğini göz önünde bulundurun:

- Tam metin ve artımlı (yazarken ara) araması için [Vikipedi](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) .
- 8\.000.000 kod depolarında dizin oluşturmak ve kullanıma sunmak için [GitHub](https://www.elastic.co/customers/github) .  
- Kapsayıcı kitaplığını bulunabilir hale getirmek için [Docker](https://www.elastic.co/customers/docker) .

Elaun Search, [Apache Lucene](https://lucene.apache.org/core/) tam metin arama altyapısının üzerine kurulmuştur. Lucene yüksek performanslı belge dizini oluşturma ve sorgulama sağlar. Ters erişimli bir dizin oluşturma düzeniyle verileri dizinlendirir; sayfaları anahtar sözcüklere eşlemek yerine, bir kitabın sonundaki bir sözlükte olduğu gibi, anahtar sözcükleri sayfalara eşler. Lucene güçlü sorgu sözdizimi özelliklerine sahiptir ve verileri şu şekilde sorgulayabilir:

- Terim (tam kelime) 
- Ön ek (Word ile başlar)
- Joker karakter ("\*" veya "?" filtrelerini kullanarak)
- Tümcecik (bir belgedeki metin dizisi)
- Boole değeri (sorguları birleştiren karmaşık aramalar)

Lucene arama için düşük düzey bir sıhhi tesisat sağlarken, Elaun Search, Lucene üzerinde bulunan sunucuyu sağlar. Elaun Search, Lucene 'in dizin oluşturma ve arama işlevselliğine erişme için yeniden bir API de dahil olmak üzere, çalışma Lucene 'i basitleştirmek için daha yüksek düzeyde işlevsellik ekler. Ayrıca, büyük ölçeklenebilirlik, hataya dayanıklılık ve yüksek kullanılabilirliğe sahip dağıtılmış bir altyapı sağlar.

Karmaşık arama gereksinimlerine sahip daha büyük bulut yerel uygulamalar için, Azure 'da yönetilen hizmet olarak Elaun Search kullanılabilir. Microsoft Azure Market, geliştiricilerin Azure 'da bir elaya arama kümesi dağıtmak için kullanabileceği önceden yapılandırılmış Şablonlar sunar.

Microsoft Azure Market, geliştiriciler Azure 'da bir elaa arama kümesini hızlı bir şekilde dağıtmak için oluşturulmuş önceden yapılandırılmış şablonları kullanabilir. Azure tarafından yönetilen teklifi kullanarak en çok 50 veri düğümü, 20 koordinasyon düğümü ve üç adanmış ana düğüm dağıtabilirsiniz.

## <a name="summary"></a>Özet

Bu bölümde, bulutta yerel sistemlerdeki verilere ayrıntılı bir bakış sunulmuştur. Bulut Yerel sistemlerdeki veri depolama desenleriyle tek parçalı uygulamalarda veri depolama alanı ile çalışmaya başladık. Platformlar arası, dağıtılmış işlemler ve yüksek hacimli sistemlerle başa çıkmak üzere desenler de dahil olmak üzere, bulutta yerel sistemlerde uygulanan veri desenlerine baktık. NoSQL verileriyle SQL 'in maliyetli olduğunu belirledik. Azure 'da bulunan ve hem Microsoft merkezli hem de açık kaynaklı seçenekleri içeren veri depolama seçeneklerine baktık. Son olarak, önbelleğe alma ve elak aramasını bulutta yerel bir uygulamada ele aldık.

### <a name="references"></a>Referanslar

- [Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS) deseninin](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Olay kaynağını belirleme kalıbı](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [RDBMSs vs. NoSQL veritabanları: genel bakış](https://maxivak.com/rdbms-vs-nosql-databases/)

- [Neden RDBMS bölümü dayanıklı değildir ve neden kullanılabilir?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Gerçekleştirilmiş görünüm](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Açık kaynak veritabanları hakkında bilmeniz gerekenler](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Telafi Işlem kriteri](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Saga kalıbı](https://microservices.io/patterns/data/saga.html)

- [Saga desenleri | Mikro hizmetleri kullanarak iş işlemlerini uygulama](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Telafi Işlem kriteri](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [9-Ball ' ın arkasında alma: Cosmos DB tutarlılık düzeyleri açıklanmaktadır](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Farklı NoSQL veritabanlarının Bölüm II türlerini keşfetme](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [RDBMS 'de NoSQL ve NewSQL veritabanları. John Ryan ile görüşme](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: tam karşılaştırma](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [TIRE: Kubernetes-Native veritabanlarının dört özelliği](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [CockroachDB](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [Yugabrivtedb](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elana Search: kesin kılavuz](http://shop.oreilly.com/product/0636920028505.do)
  
- [Apache Lucene 'e giriş](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Önceki](azure-caching.md)
>[İleri](resiliency.md) <!-- Next Chapter -->
