---
title: Bulutta yerel uygulamalarda elaun arama
description: Bulutta yerel uygulamalara elastik arama özellikleri ekleme hakkında bilgi edinin.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 70d1925d6b8c7bbe515ee4f178513dc61212ebce
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271808"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a><span data-ttu-id="98d4d-103">Bulutta yerel bir uygulamada elaun arama</span><span class="sxs-lookup"><span data-stu-id="98d4d-103">Elasticsearch in a cloud-native app</span></span>

<span data-ttu-id="98d4d-104">Elaun Search, farklı türlerde veriler arasında karmaşık arama özellikleri sağlayan bir dağıtılmış arama ve analiz sistemidir.</span><span class="sxs-lookup"><span data-stu-id="98d4d-104">Elasticsearch is a distributed search and analytics system that enables complex search capabilities across diverse types of data.</span></span> <span data-ttu-id="98d4d-105">Açık kaynak ve yaygın popüler.</span><span class="sxs-lookup"><span data-stu-id="98d4d-105">It's open source and widely popular.</span></span> <span data-ttu-id="98d4d-106">Aşağıdaki şirketlerin, Elai aramasını kendi uygulamasına nasıl tümleştirtireceğini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="98d4d-106">Consider how the following companies integrate Elasticsearch into their application:</span></span>

- <span data-ttu-id="98d4d-107">Tam metin ve artımlı (yazarken ara) araması için [Vikipedi](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) .</span><span class="sxs-lookup"><span data-stu-id="98d4d-107">[Wikipedia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) for full-text and incremental (search as you type) searching.</span></span>
- <span data-ttu-id="98d4d-108">8.000.000 kod depolarında dizin oluşturmak ve kullanıma sunmak için [GitHub](https://www.elastic.co/customers/github) .</span><span class="sxs-lookup"><span data-stu-id="98d4d-108">[GitHub](https://www.elastic.co/customers/github) to index and expose over 8 million code repositories.</span></span>  
- <span data-ttu-id="98d4d-109">Kapsayıcı kitaplığını bulunabilir hale getirmek için [Docker](https://www.elastic.co/customers/docker) .</span><span class="sxs-lookup"><span data-stu-id="98d4d-109">[Docker](https://www.elastic.co/customers/docker) for making its container library discoverable.</span></span>

<span data-ttu-id="98d4d-110">Elaun Search, [Apache Lucene](https://lucene.apache.org/core/) tam metin arama altyapısının üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="98d4d-110">Elasticsearch is built on top of the [Apache Lucene](https://lucene.apache.org/core/) full-text search engine.</span></span> <span data-ttu-id="98d4d-111">Lucene yüksek performanslı belge dizini oluşturma ve sorgulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="98d4d-111">Lucene provides high-performance document indexing and querying.</span></span> <span data-ttu-id="98d4d-112">Ters erişimli bir dizin oluşturma düzeniyle verileri dizinlendirir; sayfaları anahtar sözcüklere eşlemek yerine, bir kitabın sonundaki bir sözlükte olduğu gibi, anahtar sözcükleri sayfalara eşler.</span><span class="sxs-lookup"><span data-stu-id="98d4d-112">It indexes data with an inverted indexing scheme – instead of mapping pages to keywords, it maps keywords to pages just like a glossary at the end of a book.</span></span> <span data-ttu-id="98d4d-113">Lucene güçlü sorgu sözdizimi özelliklerine sahiptir ve verileri şu şekilde sorgulayabilir:</span><span class="sxs-lookup"><span data-stu-id="98d4d-113">Lucene has powerful query syntax capabilities and can query data by:</span></span>

- <span data-ttu-id="98d4d-114">Terim (tam kelime)</span><span class="sxs-lookup"><span data-stu-id="98d4d-114">Term (a full word)</span></span>
- <span data-ttu-id="98d4d-115">Ön ek (Word ile başlar)</span><span class="sxs-lookup"><span data-stu-id="98d4d-115">Prefix (starts-with word)</span></span>
- <span data-ttu-id="98d4d-116">Joker karakter (" \* " veya "?" filtrelerini kullanarak)</span><span class="sxs-lookup"><span data-stu-id="98d4d-116">Wildcard (using "\*" or "?" filters)</span></span>
- <span data-ttu-id="98d4d-117">Tümcecik (bir belgedeki metin dizisi)</span><span class="sxs-lookup"><span data-stu-id="98d4d-117">Phrase (a sequence of text in a document)</span></span>
- <span data-ttu-id="98d4d-118">Boole değeri (sorguları birleştiren karmaşık aramalar)</span><span class="sxs-lookup"><span data-stu-id="98d4d-118">Boolean value (complex searches combining queries)</span></span>

<span data-ttu-id="98d4d-119">Lucene arama için düşük düzey bir sıhhi tesisat sağlarken, Elaun Search, Lucene üzerinde bulunan sunucuyu sağlar.</span><span class="sxs-lookup"><span data-stu-id="98d4d-119">While Lucene provides low-level plumbing for searching, Elasticsearch provides the server that sits on top of Lucene.</span></span> <span data-ttu-id="98d4d-120">Elaun Search, Lucene 'in dizin oluşturma ve arama işlevselliğine erişme için yeniden bir API de dahil olmak üzere, çalışma Lucene 'i basitleştirmek için daha yüksek düzeyde işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="98d4d-120">Elasticsearch adds higher-level functionality to simplify working Lucene, including a RESTful API to access Lucene's indexing and searching functionality.</span></span> <span data-ttu-id="98d4d-121">Ayrıca, büyük ölçeklenebilirlik, hataya dayanıklılık ve yüksek kullanılabilirliğe sahip dağıtılmış bir altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="98d4d-121">It also provides a distributed infrastructure capable of massive scalability, fault tolerance, and high availability.</span></span>

<span data-ttu-id="98d4d-122">Karmaşık arama gereksinimlerine sahip daha büyük bulut yerel uygulamalar için, Azure 'da yönetilen hizmet olarak Elaun Search kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98d4d-122">For larger cloud-native applications with complex search requirements, Elasticsearch is available as managed service in Azure.</span></span> <span data-ttu-id="98d4d-123">Microsoft Azure Market, geliştiricilerin Azure 'da bir elaya arama kümesi dağıtmak için kullanabileceği önceden yapılandırılmış Şablonlar sunar.</span><span class="sxs-lookup"><span data-stu-id="98d4d-123">The Microsoft Azure Marketplace features preconfigured templates which developers can use to deploy an Elasticsearch cluster on Azure.</span></span>

<span data-ttu-id="98d4d-124">Microsoft Azure Market, geliştiriciler Azure 'da bir elaa arama kümesini hızlı bir şekilde dağıtmak için oluşturulmuş önceden yapılandırılmış şablonları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="98d4d-124">From the Microsoft Azure Marketplace, developers can use preconfigured templates built to quickly deploy an Elasticsearch cluster on Azure.</span></span> <span data-ttu-id="98d4d-125">Azure tarafından yönetilen teklifi kullanarak en çok 50 veri düğümü, 20 koordinasyon düğümü ve üç adanmış ana düğüm dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98d4d-125">Using the Azure-managed offering, you can deploy up to 50 data nodes, 20 coordinating nodes, and three dedicated master nodes.</span></span>

## <a name="summary"></a><span data-ttu-id="98d4d-126">Özet</span><span class="sxs-lookup"><span data-stu-id="98d4d-126">Summary</span></span>

<span data-ttu-id="98d4d-127">Bu bölümde, bulutta yerel sistemlerdeki verilere ayrıntılı bir bakış sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="98d4d-127">This chapter presented a detailed look at data in cloud-native systems.</span></span> <span data-ttu-id="98d4d-128">Bulut Yerel sistemlerdeki veri depolama desenleriyle tek parçalı uygulamalarda veri depolama alanı ile çalışmaya başladık.</span><span class="sxs-lookup"><span data-stu-id="98d4d-128">We started by contrasting data storage in monolithic applications with data storage patterns in cloud-native systems.</span></span> <span data-ttu-id="98d4d-129">Platformlar arası, dağıtılmış işlemler ve yüksek hacimli sistemlerle başa çıkmak üzere desenler de dahil olmak üzere, bulutta yerel sistemlerde uygulanan veri desenlerine baktık.</span><span class="sxs-lookup"><span data-stu-id="98d4d-129">We looked at data patterns implemented in cloud-native systems, including cross-service queries, distributed transactions, and patterns to deal with high-volume systems.</span></span> <span data-ttu-id="98d4d-130">NoSQL verileriyle SQL 'in maliyetli olduğunu belirledik.</span><span class="sxs-lookup"><span data-stu-id="98d4d-130">We contrasted SQL with NoSQL data.</span></span> <span data-ttu-id="98d4d-131">Azure 'da bulunan ve hem Microsoft merkezli hem de açık kaynaklı seçenekleri içeren veri depolama seçeneklerine baktık.</span><span class="sxs-lookup"><span data-stu-id="98d4d-131">We looked at data storage options available in Azure that include both Microsoft-centric and open-source options.</span></span> <span data-ttu-id="98d4d-132">Son olarak, önbelleğe alma ve elak aramasını bulutta yerel bir uygulamada ele aldık.</span><span class="sxs-lookup"><span data-stu-id="98d4d-132">Finally, we discussed caching and Elasticsearch in a cloud-native application.</span></span>

### <a name="references"></a><span data-ttu-id="98d4d-133">Başvurular</span><span class="sxs-lookup"><span data-stu-id="98d4d-133">References</span></span>

- [<span data-ttu-id="98d4d-134">Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS) deseninin</span><span class="sxs-lookup"><span data-stu-id="98d4d-134">Command and Query Responsibility Segregation (CQRS) pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [<span data-ttu-id="98d4d-135">Olay kaynağını belirleme kalıbı</span><span class="sxs-lookup"><span data-stu-id="98d4d-135">Event Sourcing pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [<span data-ttu-id="98d4d-136">Neden RDBMS bölümü dayanıklı değildir ve neden kullanılabilir?</span><span class="sxs-lookup"><span data-stu-id="98d4d-136">Why isn't RDBMS Partition Tolerant in CAP Theorem and why is it Available?</span></span>](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [<span data-ttu-id="98d4d-137">Gerçekleştirilmiş Görünüm</span><span class="sxs-lookup"><span data-stu-id="98d4d-137">Materialized View</span></span>](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [<span data-ttu-id="98d4d-138">Açık kaynak veritabanları hakkında bilmeniz gerekenler</span><span class="sxs-lookup"><span data-stu-id="98d4d-138">All you really need to know about open source databases</span></span>](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [<span data-ttu-id="98d4d-139">Telafi Işlem kriteri</span><span class="sxs-lookup"><span data-stu-id="98d4d-139">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="98d4d-140">Saga kalıbı</span><span class="sxs-lookup"><span data-stu-id="98d4d-140">Saga Pattern</span></span>](https://microservices.io/patterns/data/saga.html)

- [<span data-ttu-id="98d4d-141">Saga desenleri | Mikro hizmetleri kullanarak iş işlemlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="98d4d-141">Saga Patterns | How to implement business transactions using microservices</span></span>](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [<span data-ttu-id="98d4d-142">Telafi Işlem kriteri</span><span class="sxs-lookup"><span data-stu-id="98d4d-142">Compensating Transaction pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [<span data-ttu-id="98d4d-143">9-Ball ' ın arkasında alma: Cosmos DB tutarlılık düzeyleri açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="98d4d-143">Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained</span></span>](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [<span data-ttu-id="98d4d-144">Farklı NoSQL veritabanlarının Bölüm II türlerini keşfetme</span><span class="sxs-lookup"><span data-stu-id="98d4d-144">Exploring the different types of NoSQL Databases Part II</span></span>](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [<span data-ttu-id="98d4d-145">RDBMS 'de NoSQL ve NewSQL veritabanları. John Ryan ile görüşme</span><span class="sxs-lookup"><span data-stu-id="98d4d-145">On RDBMS, NoSQL and NewSQL databases. Interview with John Ryan</span></span>](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [<span data-ttu-id="98d4d-146">SQL vs NoSQL vs NewSQL: tam karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="98d4d-146">SQL vs NoSQL vs NewSQL: The Full Comparison</span></span>](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [<span data-ttu-id="98d4d-147">TIRE: Kubernetes-Native veritabanlarının dört özelliği</span><span class="sxs-lookup"><span data-stu-id="98d4d-147">DASH: Four Properties of Kubernetes-Native Databases</span></span>](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [<span data-ttu-id="98d4d-148">CockroachDB</span><span class="sxs-lookup"><span data-stu-id="98d4d-148">CockroachDB</span></span>](https://www.cockroachlabs.com/)

- [<span data-ttu-id="98d4d-149">TiDB</span><span class="sxs-lookup"><span data-stu-id="98d4d-149">TiDB</span></span>](https://pingcap.com/en/)

- [<span data-ttu-id="98d4d-150">Yugabrivtedb</span><span class="sxs-lookup"><span data-stu-id="98d4d-150">YugabyteDB</span></span>](https://www.yugabyte.com/)

- [<span data-ttu-id="98d4d-151">Vitess</span><span class="sxs-lookup"><span data-stu-id="98d4d-151">Vitess</span></span>](https://vitess.io/)

- [<span data-ttu-id="98d4d-152">Elana Search: kesin kılavuz</span><span class="sxs-lookup"><span data-stu-id="98d4d-152">Elasticsearch: The Definitive Guide</span></span>](https://shop.oreilly.com/product/0636920028505.do)
  
- [<span data-ttu-id="98d4d-153">Apache Lucene 'e giriş</span><span class="sxs-lookup"><span data-stu-id="98d4d-153">Introduction to Apache Lucene</span></span>](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
><span data-ttu-id="98d4d-154">[Önceki](azure-caching.md) 
> [Sonraki](resiliency.md)</span><span class="sxs-lookup"><span data-stu-id="98d4d-154">[Previous](azure-caching.md)
[Next](resiliency.md)</span></span> <!-- Next Chapter -->
