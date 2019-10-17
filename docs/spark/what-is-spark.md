---
title: Apache Spark nedir?
description: Apache Spark ve büyük veri senaryoları hakkında bilgi edinin.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: ccf41f08df3c68a039210320f14219e6b6229a64
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396238"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="25083-103">Apache Spark nedir?</span><span class="sxs-lookup"><span data-stu-id="25083-103">What is Apache Spark?</span></span>

<span data-ttu-id="25083-104">[Apache Spark](https://spark.apache.org/) , büyük verileri çözümleyen uygulamaların performansını artırmak üzere bellek içi işlemeyi destekleyen açık kaynaklı bir paralel işleme çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="25083-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="25083-105">Büyük veri çözümleri geleneksel veritabanları için çok büyük veya karmaşık olan verileri işleyecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="25083-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="25083-106">Spark, disk tabanlı alternatiflerden çok daha hızlı olan bellekteki büyük miktarda veriyi işler.</span><span class="sxs-lookup"><span data-stu-id="25083-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span> 

## <a name="common-big-data-scenarios"></a><span data-ttu-id="25083-107">Yaygın büyük veri senaryoları</span><span class="sxs-lookup"><span data-stu-id="25083-107">Common big data scenarios</span></span>

<span data-ttu-id="25083-108">Büyük hacimlerdeki verileri depolamanız ve işlemek, yapılandırılmamış verileri dönüştürmek veya akış verilerini işlemek için büyük bir veri mimarisini düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25083-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="25083-109">Spark, çok büyük veri senaryolarında kullanılabilen, genel amaçlı bir dağıtılmış işleme altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="25083-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span> 

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="25083-110">Ayıklama, dönüştürme ve yükleme (ETL)</span><span class="sxs-lookup"><span data-stu-id="25083-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="25083-111">[Ayıklama, dönüştürme ve yükleme (ETL)](/azure/architecture/data-guide/relational-data/etl) , bir veya birden çok kaynaktan veri toplama, verileri değiştirme ve verileri yeni bir veri deposuna taşıma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="25083-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="25083-112">Aşağıdakiler dahil olmak üzere çeşitli veri dönüştürme yolları vardır:</span><span class="sxs-lookup"><span data-stu-id="25083-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="25083-113">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="25083-113">Filtering</span></span>
* <span data-ttu-id="25083-114">Sıralama</span><span class="sxs-lookup"><span data-stu-id="25083-114">Sorting</span></span>
* <span data-ttu-id="25083-115">Larla</span><span class="sxs-lookup"><span data-stu-id="25083-115">Aggregating</span></span>
* <span data-ttu-id="25083-116">Katılma</span><span class="sxs-lookup"><span data-stu-id="25083-116">Joining</span></span>
* <span data-ttu-id="25083-117">Temizlemek</span><span class="sxs-lookup"><span data-stu-id="25083-117">Cleaning</span></span>
* <span data-ttu-id="25083-118">Yinelenen</span><span class="sxs-lookup"><span data-stu-id="25083-118">Deduplicating</span></span>
* <span data-ttu-id="25083-119">Doğrulamada</span><span class="sxs-lookup"><span data-stu-id="25083-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="25083-120">Gerçek zamanlı veri akışı işleme</span><span class="sxs-lookup"><span data-stu-id="25083-120">Real-time data stream processing</span></span>

<span data-ttu-id="25083-121">Akış veya gerçek zamanlı veriler hareket halinde veriler.</span><span class="sxs-lookup"><span data-stu-id="25083-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="25083-122">IoT cihazlarındaki telemetri, Weblogs ve tıklama akışları, akış verilerine örnek olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="25083-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="25083-123">Gerçek zamanlı veriler, Jeo-uzamsal analiz, uzaktan izleme ve anomali algılama gibi yararlı bilgiler sağlamak için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="25083-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="25083-124">İlişkisel veriler gibi, verileri bir çıkış havuzuna taşımadan önce, akış verilerini filtreleyebilir, toplayabilir ve hazırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25083-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="25083-125">Apache Spark [Spark akışı](https://spark.apache.org/streaming/)aracılığıyla [gerçek zamanlı veri akışı işlemesini](/azure/architecture/data-guide/big-data/real-time-processing) destekler.</span><span class="sxs-lookup"><span data-stu-id="25083-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span> 

### <a name="batch-processing"></a><span data-ttu-id="25083-126">Toplu işleme</span><span class="sxs-lookup"><span data-stu-id="25083-126">Batch processing</span></span>

<span data-ttu-id="25083-127">[Toplu işleme](/azure/architecture/data-guide/big-data/batch-processing) , bekleyen büyük verilerin işlenmesiyle ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="25083-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="25083-128">Uzun süre çalışan işleri kullanarak çok büyük veri kümelerini, paralel olarak filtreleyebilir, toplayabilir ve hazırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="25083-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="25083-129">MLlib aracılığıyla makine öğrenimi</span><span class="sxs-lookup"><span data-stu-id="25083-129">Machine learning through MLlib</span></span>

<span data-ttu-id="25083-130">Makine öğrenimi, gelişmiş analitik sorunlar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25083-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="25083-131">Bilgisayarınız, gelecekteki davranışları, sonuçları ve eğilimleri tahmin etmek veya tahmin etmek için mevcut verileri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="25083-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="25083-132">Apache Spark Machine Learning kitaplığı, [Mllib](https://spark.apache.org/mllib/), çeşitli makine öğrenimi algoritmalarını ve yardımcı programlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="25083-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="25083-133">GraphX aracılığıyla grafik işleme</span><span class="sxs-lookup"><span data-stu-id="25083-133">Graph processing through GraphX</span></span>

<span data-ttu-id="25083-134">Grafik, kenarlara göre bağlanmış düğümlerin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="25083-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="25083-135">Bağlantılı ilişkilerle verileri veya verileri hiyerarşik olarak kullandıysanız grafik veritabanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25083-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="25083-136">Apache Spark [GraphX](https://spark.apache.org/graphx/) API 'sini kullanarak bu verileri işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25083-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="25083-137">Spark SQL ile SQL ve yapılandırılmış veri işleme</span><span class="sxs-lookup"><span data-stu-id="25083-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="25083-138">Yapılandırılmış (biçimli) verilerle çalışıyorsanız [Spark SQL](https://spark.apache.org/sql/)kullanarak Spark uygulamanızda SQL sorguları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25083-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="25083-139">Apache Spark mimarisi</span><span class="sxs-lookup"><span data-stu-id="25083-139">Apache Spark architecture</span></span>

<span data-ttu-id="25083-140">Ana/çalışan mimarisini kullanan Apache Spark, üç ana bileşene sahiptir: sürücü, yürüticileri ve Küme Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="25083-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Apache Spark mimarisi](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="25083-142">Sürücü</span><span class="sxs-lookup"><span data-stu-id="25083-142">Driver</span></span>

<span data-ttu-id="25083-143">Sürücü, bir C# konsol uygulaması ve Spark oturumu gibi, programından oluşur.</span><span class="sxs-lookup"><span data-stu-id="25083-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="25083-144">Spark oturumu programınızı alır ve yürüticileri tarafından işlenen daha küçük görevlere böler.</span><span class="sxs-lookup"><span data-stu-id="25083-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="25083-145">Yürütücüler</span><span class="sxs-lookup"><span data-stu-id="25083-145">Executors</span></span>

<span data-ttu-id="25083-146">Her yürütücü veya çalışan düğümü, sürücüden bir görevi alır ve bu görevi yürütür.</span><span class="sxs-lookup"><span data-stu-id="25083-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="25083-147">Yürüticileri, küme olarak bilinen bir varlıkta bulunur.</span><span class="sxs-lookup"><span data-stu-id="25083-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="25083-148">Küme Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="25083-148">Cluster manager</span></span>

<span data-ttu-id="25083-149">Küme Yöneticisi, hem sürücü hem de yürüticileri ile iletişim kurar:</span><span class="sxs-lookup"><span data-stu-id="25083-149">The cluster manager communicates with both the driver and the executors to:</span></span>

- <span data-ttu-id="25083-150">Kaynak ayırmayı yönetme</span><span class="sxs-lookup"><span data-stu-id="25083-150">Manage resource allocation</span></span>
- <span data-ttu-id="25083-151">Program bölümünü Yönet</span><span class="sxs-lookup"><span data-stu-id="25083-151">Manage program division</span></span>
- <span data-ttu-id="25083-152">Program yürütmeyi yönetme</span><span class="sxs-lookup"><span data-stu-id="25083-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="25083-153">Dil desteği</span><span class="sxs-lookup"><span data-stu-id="25083-153">Language support</span></span>

<span data-ttu-id="25083-154">Apache Spark aşağıdaki programlama dillerini destekler:</span><span class="sxs-lookup"><span data-stu-id="25083-154">Apache Spark supports the following programming languages:</span></span>

- <span data-ttu-id="25083-155">Scala</span><span class="sxs-lookup"><span data-stu-id="25083-155">Scala</span></span>
- <span data-ttu-id="25083-156">Python</span><span class="sxs-lookup"><span data-stu-id="25083-156">Python</span></span>
- <span data-ttu-id="25083-157">Java</span><span class="sxs-lookup"><span data-stu-id="25083-157">Java</span></span>
- <span data-ttu-id="25083-158">SQL</span><span class="sxs-lookup"><span data-stu-id="25083-158">SQL</span></span>
- <span data-ttu-id="25083-159">R</span><span class="sxs-lookup"><span data-stu-id="25083-159">R</span></span>
- <span data-ttu-id="25083-160">.NET</span><span class="sxs-lookup"><span data-stu-id="25083-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="25083-161">Spark API 'Leri</span><span class="sxs-lookup"><span data-stu-id="25083-161">Spark APIs</span></span>

<span data-ttu-id="25083-162">Apache Spark aşağıdaki API 'Leri destekler:</span><span class="sxs-lookup"><span data-stu-id="25083-162">Apache Spark supports the following APIs:</span></span>

- [<span data-ttu-id="25083-163">Spark Scala API 'SI</span><span class="sxs-lookup"><span data-stu-id="25083-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
- [<span data-ttu-id="25083-164">Spark Java API 'SI</span><span class="sxs-lookup"><span data-stu-id="25083-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
- [<span data-ttu-id="25083-165">Spark Python API 'SI</span><span class="sxs-lookup"><span data-stu-id="25083-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
- [<span data-ttu-id="25083-166">Spark R API 'SI</span><span class="sxs-lookup"><span data-stu-id="25083-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
- <span data-ttu-id="25083-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), yerleşik işlevler</span><span class="sxs-lookup"><span data-stu-id="25083-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="25083-168">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="25083-168">Next steps</span></span>

<span data-ttu-id="25083-169">.NET uygulamanızda Apache Spark nasıl kullanabileceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="25083-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="25083-170">Apache Spark için .NET ile, .NET deneyimi ve iş mantığı olan geliştiriciler, ve C# F#' de büyük veri sorguları yazabilir.</span><span class="sxs-lookup"><span data-stu-id="25083-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="25083-171">Apache Spark için .NET nedir?</span><span class="sxs-lookup"><span data-stu-id="25083-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
