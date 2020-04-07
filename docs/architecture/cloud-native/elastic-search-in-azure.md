---
title: Bulut-yerel uygulamalarda elastik arama
description: Bulut taşıyıcı uygulamalara Elastik Arama özellikleri ekleme ü
author: robvet
ms.date: 03/02/2020
ms.openlocfilehash: da6b9402cf266f5a298b05cf837805b2377bc75a
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805570"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="74283-103">Bulut ayarı uygulamasında elasticsearch</span><span class="sxs-lookup"><span data-stu-id="74283-103">Elasticsearch in a cloud-native app</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="74283-104">Elasticsearch, farklı veri türleri arasında karmaşık arama yetenekleri sağlayan dağıtılmış bir arama ve analiz sistemidir.</span><span class="sxs-lookup"><span data-stu-id="74283-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="74283-105">Açık kaynak ve yaygın olarak popüler.</span><span class="sxs-lookup"><span data-stu-id="74283-105">It's open source and widely popular.</span></span> <span data-ttu-id="74283-106">Aşağıdaki şirketlerin Elasticsearch'u uygulamalarına nasıl entegre ettiklerine göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="74283-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="74283-107">Tam metin ve artımlı (yazarken arama) arama için [Vikipedi.](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/)</span><span class="sxs-lookup"><span data-stu-id="74283-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="74283-108">[GitHub,](https://www.elastic.co/customers/github) 8 milyondan fazla kod deposunu dizine ekleyip ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="74283-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="74283-109">Konteyner kütüphanesini keşfedilebilir hale getirmek için [Docker.](https://www.elastic.co/customers/docker)</span><span class="sxs-lookup"><span data-stu-id="74283-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="74283-110">[Elasticsearch, Apache Lucene](https://lucene.apache.org/core/) tam metin arama motorunun üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="74283-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="74283-111">Lucene yüksek performanslı belge dizini ve sorgusağlar.</span><span class="sxs-lookup"><span data-stu-id="74283-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="74283-112">Verileri ters bir dizin oluşturma şemasıyla dizine alır – sayfaları anahtar kelimelerle eşlemek yerine, anahtar kelimeleri kitabın sonundaki bir sözlük gibi sayfalara eşler.</span><span class="sxs-lookup"><span data-stu-id="74283-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="74283-113">Lucene güçlü sorgu sözdizimi yeteneklerine sahiptir ve verileri şu şekilde sorgulayabilir:</span><span class="sxs-lookup"><span data-stu-id="74283-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="74283-114">Terim (tam kelime)</span><span class="sxs-lookup"><span data-stu-id="74283-114">Term (a full word)</span></span>
- <span data-ttu-id="74283-115">Önek (sözcük ile başlar)</span><span class="sxs-lookup"><span data-stu-id="74283-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="74283-116">Joker karakter (" "\*veya "?" filtreleri kullanarak)</span><span class="sxs-lookup"><span data-stu-id="74283-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="74283-117">Tümcecik (belgedeki metin sırası)</span><span class="sxs-lookup"><span data-stu-id="74283-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="74283-118">Boolean değeri (sorguları birleştiren karmaşık aramalar)</span><span class="sxs-lookup"><span data-stu-id="74283-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="74283-119">Lucene arama için düşük seviyeli sıhhi tesisat sağlarken, Elasticsearch Lucene üstüne oturur sunucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="74283-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="74283-120">Elasticsearch, Lucene'nin dizin oluşturma ve arama işlevlerine erişmek için yeniden yapılan api de dahil olmak üzere, lucene'nin çalışmasını basitleştirmek için daha üst düzey işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="74283-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="74283-121">Ayrıca, büyük ölçeklenebilirlik, hata toleransı ve yüksek kullanılabilirlik yeteneğine sahip dağıtılmış bir altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="74283-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="74283-122">Karmaşık arama gereksinimlerine sahip daha büyük bulut yerel uygulamalar için Elasticsearch, Azure'da yönetilen hizmet olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74283-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="74283-123">Microsoft Azure Marketi, geliştiricilerin Azure'da Bir Elasticsearch kümesidağıtmak için kullanabilecekleri önceden yapılandırılmış şablonlar sunar.</span><span class="sxs-lookup"><span data-stu-id="74283-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="74283-124">Geliştiriciler, Microsoft Azure Marketi'nden, Azure'da Elasticsearch kümesini hızla dağıtmak için önceden yapılandırılmış şablonlar kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="74283-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="74283-125">Azure tarafından yönetilen teklifi kullanarak, en fazla 50 veri düğümü, 20 eşgüdüm düğümü ve üç özel ana düğüm dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74283-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="74283-126">Özet</span><span class="sxs-lookup"><span data-stu-id="74283-126">Summary</span></span>

<span data-ttu-id="74283-127">Bu bölümde bulut ayarı sistemlerdeki verilere ayrıntılı bir bakış sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="74283-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="74283-128">Bulut ait sistemlerdeki veri depolama desenleri ile yekpare uygulamalarda veri depolamayı karşılaştırarak başladık.</span><span class="sxs-lookup"><span data-stu-id="74283-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="74283-129">Yüksek hacimli sistemlerle başa çıkmak için çapraz hizmet sorguları, dağıtılmış işlemler ve desenler de dahil olmak üzere bulut ayarı sistemlerinde uygulanan veri kalıplarına baktık.</span><span class="sxs-lookup"><span data-stu-id="74283-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="74283-130">SQL ile NoSQL verileri arasında zıtlık yaptık.</span><span class="sxs-lookup"><span data-stu-id="74283-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="74283-131">Azure'da hem Microsoft merkezli hem de açık kaynak seçenekleri içeren veri depolama seçeneklerini inceledik.</span><span class="sxs-lookup"><span data-stu-id="74283-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="74283-132">Son olarak, bir bulut-yerel uygulamada önbelleğe alma ve Elasticsearch tartışıldı.</span><span class="sxs-lookup"><span data-stu-id="74283-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="74283-133">Başvurular</span><span class="sxs-lookup"><span data-stu-id="74283-133">References</span></span>

- [<span data-ttu-id="74283-134">Komut ve Sorgu Sorumluluğu Ayrımı (CQRS) deseni</span><span class="sxs-lookup"><span data-stu-id="74283-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="74283-135">Olay Kaynak deseni</span><span class="sxs-lookup"><span data-stu-id="74283-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="74283-136">NEDEN CAP Teoremi'nde RDBMS Bölüm toleranslı değildir ve neden kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="74283-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="74283-137">Materyalize Görünüm</span><span class="sxs-lookup"><span data-stu-id="74283-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="74283-138">Tüm gerçekten açık kaynak veritabanları hakkında bilmeniz gereken</span><span class="sxs-lookup"><span data-stu-id="74283-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="74283-139">Telafi İşlemi deseni</span><span class="sxs-lookup"><span data-stu-id="74283-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="74283-140">Destan Deseni</span><span class="sxs-lookup"><span data-stu-id="74283-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="74283-141">Destan Desenleri | Mikro hizmetleri kullanarak ticari işlemler nasıl uygulanır?</span><span class="sxs-lookup"><span data-stu-id="74283-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="74283-142">Telafi İşlemi deseni</span><span class="sxs-lookup"><span data-stu-id="74283-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="74283-143">9-Top Arkasında Başlarken: Cosmos DB Tutarlılık Düzeyleri Açıkladı</span><span class="sxs-lookup"><span data-stu-id="74283-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="74283-144">NoSQL Veritabanları Bölüm II farklı türde keşfetmek</span><span class="sxs-lookup"><span data-stu-id="74283-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="74283-145">RDBMS, NoSQL ve NewSQL veritabanlarında. John Ryan ile röportaj</span><span class="sxs-lookup"><span data-stu-id="74283-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="74283-146">SQL vs NoSQL vs NewSQL: Tam Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="74283-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="74283-147">DASH: Kubernetes-Native Veritabanları dört özellikleri</span><span class="sxs-lookup"><span data-stu-id="74283-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="74283-148">Hamamböceği</span><span class="sxs-lookup"><span data-stu-id="74283-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="74283-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="74283-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="74283-150">YugabyteDB</span><span class="sxs-lookup"><span data-stu-id="74283-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="74283-151">Vitess</span><span class="sxs-lookup"><span data-stu-id="74283-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="74283-152">Elasticsearch: Definitive Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="74283-152">Elasticsearch: The Definitive Guide</span></span>](http://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="74283-153">Apache Lucene'ye Giriş</span><span class="sxs-lookup"><span data-stu-id="74283-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="74283-154">[Önceki](azure-caching.md)
>[Sonraki](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="74283-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
