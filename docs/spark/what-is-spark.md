---
title: Apache Spark nedir?
description: Apache Spark ve büyük veri senaryoları hakkında bilgi edinin.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458167"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="c7650-103">Apache Spark nedir?</span><span class="sxs-lookup"><span data-stu-id="c7650-103">What is Apache Spark?</span></span>

<span data-ttu-id="c7650-104">[Apache Spark,](https://spark.apache.org/) büyük verileri çözümleyen uygulamaların performansını artırmak için bellek içi işlemeyi destekleyen açık kaynaklı paralel bir işlem çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="c7650-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="c7650-105">Büyük veri çözümleri, geleneksel veritabanları için çok büyük veya karmaşık verileri işlemek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7650-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="c7650-106">Spark bellekte büyük miktarda veri işler, bu da disk tabanlı alternatiflerden çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7650-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="c7650-107">Ortak büyük veri senaryoları</span><span class="sxs-lookup"><span data-stu-id="c7650-107">Common big data scenarios</span></span>

<span data-ttu-id="c7650-108">Büyük hacimli verileri depolamanız ve işlemeniz, yapılandırılmamış verileri dönüştürmeniz veya akış verilerini işlemeniz gerekiyorsa büyük bir veri mimarisi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7650-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="c7650-109">Spark, birkaç büyük veri senaryosu için kullanılabilecek genel amaçlı dağıtılmış işleme altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="c7650-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="c7650-110">Ayıklama, dönüştürme ve yükleme (ETL)</span><span class="sxs-lookup"><span data-stu-id="c7650-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="c7650-111">[Ayıklama, dönüştürme ve yükleme (ETL),](/azure/architecture/data-guide/relational-data/etl) bir veya birden çok kaynaktan veri toplama, verileri değiştirme ve verileri yeni bir veri deposuna taşıma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="c7650-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="c7650-112">Verileri dönüştürmenin çeşitli yolları vardır:</span><span class="sxs-lookup"><span data-stu-id="c7650-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="c7650-113">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="c7650-113">Filtering</span></span>
* <span data-ttu-id="c7650-114">Sıralama</span><span class="sxs-lookup"><span data-stu-id="c7650-114">Sorting</span></span>
* <span data-ttu-id="c7650-115">Top -layarak</span><span class="sxs-lookup"><span data-stu-id="c7650-115">Aggregating</span></span>
* <span data-ttu-id="c7650-116">Katma</span><span class="sxs-lookup"><span data-stu-id="c7650-116">Joining</span></span>
* <span data-ttu-id="c7650-117">Temizleme</span><span class="sxs-lookup"><span data-stu-id="c7650-117">Cleaning</span></span>
* <span data-ttu-id="c7650-118">Deduplicating</span><span class="sxs-lookup"><span data-stu-id="c7650-118">Deduplicating</span></span>
* <span data-ttu-id="c7650-119">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="c7650-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="c7650-120">Gerçek zamanlı veri akışı işleme</span><span class="sxs-lookup"><span data-stu-id="c7650-120">Real-time data stream processing</span></span>

<span data-ttu-id="c7650-121">Akış veya gerçek zamanlı, veri hareket halindeki verilerdir.</span><span class="sxs-lookup"><span data-stu-id="c7650-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="c7650-122">IoT aygıtlarından, web günlüklerinden ve tıklama akışlarından telemetri, veri akışına örnektir.</span><span class="sxs-lookup"><span data-stu-id="c7650-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="c7650-123">Jeouzamsal analiz, uzaktan izleme ve anomali algılama gibi yararlı bilgiler sağlamak için gerçek zamanlı veriler işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7650-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="c7650-124">İlişkisel veriler gibi, verileri bir çıktı lavabosuna taşımadan önce akış verilerini filtreleyebilir, toplayabilir ve hazırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7650-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="c7650-125">Apache Spark, [Spark Streaming](https://spark.apache.org/streaming/)aracılığıyla [gerçek zamanlı veri akışı işlemeyi](/azure/architecture/data-guide/big-data/real-time-processing) destekler.</span><span class="sxs-lookup"><span data-stu-id="c7650-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="c7650-126">Toplu işlem</span><span class="sxs-lookup"><span data-stu-id="c7650-126">Batch processing</span></span>

<span data-ttu-id="c7650-127">[Toplu işlem,](/azure/architecture/data-guide/big-data/batch-processing) büyük verilerin istirahathalinde işlenmesidir.</span><span class="sxs-lookup"><span data-stu-id="c7650-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="c7650-128">Paralel olarak uzun süren işleri kullanarak çok büyük veri kümelerini filtreleyebilir, toplayabilir ve hazırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7650-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="c7650-129">MLlib ile makine öğrenimi</span><span class="sxs-lookup"><span data-stu-id="c7650-129">Machine learning through MLlib</span></span>

<span data-ttu-id="c7650-130">Makine öğrenimi ileri analitik problemler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7650-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="c7650-131">Bilgisayarınız, gelecekteki davranışları, sonuçları ve eğilimleri tahmin etmek veya tahmin etmek için varolan verileri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7650-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="c7650-132">Apache Spark makine öğrenme kütüphanesi, [MLlib,](https://spark.apache.org/mllib/)çeşitli makine öğrenme algoritmaları ve yardımcı programları içerir.</span><span class="sxs-lookup"><span data-stu-id="c7650-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="c7650-133">GraphX ile grafik işleme</span><span class="sxs-lookup"><span data-stu-id="c7650-133">Graph processing through GraphX</span></span>

<span data-ttu-id="c7650-134">Grafik, kenarlarla birbirine bağlı düğümler topluluğudur.</span><span class="sxs-lookup"><span data-stu-id="c7650-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="c7650-135">Hiyerarşik verileriniz veya birbirine bağlı ilişkileri olan verileriniz varsa bir grafik veritabanı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7650-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="c7650-136">Bu verileri Apache Spark'ın [GraphX](https://spark.apache.org/graphx/) API'sini kullanarak işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7650-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="c7650-137">Spark SQL ile SQL ve yapılandırılmış veri işleme</span><span class="sxs-lookup"><span data-stu-id="c7650-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="c7650-138">Yapılandırılmış (biçimlendirilmiş) verilerle çalışıyorsanız, [Spark SQL'i](https://spark.apache.org/sql/)kullanarak Spark uygulamanızda SQL sorgularını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7650-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="c7650-139">Apache Spark mimarisi</span><span class="sxs-lookup"><span data-stu-id="c7650-139">Apache Spark architecture</span></span>

<span data-ttu-id="c7650-140">Ana/işçi mimarisini kullanan Apache Spark'ın üç ana bileşeni vardır: sürücü, uygulayıcılar ve küme yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="c7650-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Apache Spark mimarisi](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="c7650-142">Sürücü</span><span class="sxs-lookup"><span data-stu-id="c7650-142">Driver</span></span>

<span data-ttu-id="c7650-143">Sürücü, C# konsolu uygulaması ve Bir Kıvılcım oturumu gibi programınızdan oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7650-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="c7650-144">Kıvılcım oturumu programınızı alır ve uygulayıcılar tarafından işlenen daha küçük görevlere böler.</span><span class="sxs-lookup"><span data-stu-id="c7650-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="c7650-145">Executors</span><span class="sxs-lookup"><span data-stu-id="c7650-145">Executors</span></span>

<span data-ttu-id="c7650-146">Her uygulayıcı veya alt düğüm, sürücüden bir görev alır ve bu görevi yürütür.</span><span class="sxs-lookup"><span data-stu-id="c7650-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="c7650-147">Uygulayıcılar küme olarak bilinen bir varlıkta ikamet eder.</span><span class="sxs-lookup"><span data-stu-id="c7650-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="c7650-148">Küme yöneticisi</span><span class="sxs-lookup"><span data-stu-id="c7650-148">Cluster manager</span></span>

<span data-ttu-id="c7650-149">Küme yöneticisi hem sürücü hem de uygulayıcılarla aşağıdakiiletişim kurar:</span><span class="sxs-lookup"><span data-stu-id="c7650-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="c7650-150">Kaynak tahsisini yönetme</span><span class="sxs-lookup"><span data-stu-id="c7650-150">Manage resource allocation</span></span>
* <span data-ttu-id="c7650-151">Program bölümünü yönetme</span><span class="sxs-lookup"><span data-stu-id="c7650-151">Manage program division</span></span>
* <span data-ttu-id="c7650-152">Program yürütmeyi yönetme</span><span class="sxs-lookup"><span data-stu-id="c7650-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="c7650-153">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="c7650-153">Language support</span></span>

<span data-ttu-id="c7650-154">Apache Spark aşağıdaki programlama dillerini destekler:</span><span class="sxs-lookup"><span data-stu-id="c7650-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="c7650-155">Scala</span><span class="sxs-lookup"><span data-stu-id="c7650-155">Scala</span></span>
* <span data-ttu-id="c7650-156">Python</span><span class="sxs-lookup"><span data-stu-id="c7650-156">Python</span></span>
* <span data-ttu-id="c7650-157">Java</span><span class="sxs-lookup"><span data-stu-id="c7650-157">Java</span></span>
* <span data-ttu-id="c7650-158">SQL</span><span class="sxs-lookup"><span data-stu-id="c7650-158">SQL</span></span>
* <span data-ttu-id="c7650-159">R</span><span class="sxs-lookup"><span data-stu-id="c7650-159">R</span></span>
* <span data-ttu-id="c7650-160">.NET</span><span class="sxs-lookup"><span data-stu-id="c7650-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="c7650-161">Kıvılcım API'leri</span><span class="sxs-lookup"><span data-stu-id="c7650-161">Spark APIs</span></span>

<span data-ttu-id="c7650-162">Apache Spark aşağıdaki API'leri destekler:</span><span class="sxs-lookup"><span data-stu-id="c7650-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="c7650-163">Kıvılcım Scala API</span><span class="sxs-lookup"><span data-stu-id="c7650-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="c7650-164">Kıvılcım Java API</span><span class="sxs-lookup"><span data-stu-id="c7650-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="c7650-165">Kıvılcım Python API</span><span class="sxs-lookup"><span data-stu-id="c7650-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="c7650-166">Kıvılcım R API</span><span class="sxs-lookup"><span data-stu-id="c7650-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="c7650-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), yerleşik işlevler</span><span class="sxs-lookup"><span data-stu-id="c7650-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="c7650-168">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c7650-168">Next steps</span></span>

<span data-ttu-id="c7650-169">.NET uygulamanızda Apache Spark'ı nasıl kullanabileceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="c7650-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="c7650-170">Apache Spark için .NET ile .NET deneyimi ve iş mantığına sahip geliştiriciler C# ve F# ile büyük veri sorguları yazabilirler.</span><span class="sxs-lookup"><span data-stu-id="c7650-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c7650-171">Apache Spark için .NET nedir</span><span class="sxs-lookup"><span data-stu-id="c7650-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
