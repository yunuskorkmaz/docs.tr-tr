---
title: Apache Spark için .NET nedir?
description: .NET kodu yazdığınız her yerde Spark alan ücretsiz, açık kaynaklı ve platformlar arası büyük veri analizi çerçevesi Apache Spark için .NET hakkında bilgi edinin.
author: mamccrea
ms.topic: overview
ms.date: 06/25/2020
ms.openlocfilehash: 2c04861dabe604b52df583cd5a7eecc5ff8e5481
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621866"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="918ff-103">Apache Spark için .NET nedir?</span><span class="sxs-lookup"><span data-stu-id="918ff-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="918ff-104">[Apache Spark](what-is-spark.md) , büyük veri kümeleri üzerinde analizler için genel amaçlı bir dağıtılmış işleme altyapısıdır. genellikle terabayt veya petabaytlarca veri.</span><span class="sxs-lookup"><span data-stu-id="918ff-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="918ff-105">Popüler açık kaynaklı büyük veri analizi çerçevesi için Apache Spark, ücretsiz, açık kaynaklı ve platformlar arası .NET desteği için .NET ile, zaten bildiğiniz dilleri kullanarak Apache Spark gücünü büyük veri uygulamalarınıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="918ff-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

[!INCLUDE [spark-preview-note](../../includes/spark-preview-note.md)]

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="918ff-106">Apache Spark için .NET neden seçmelisiniz?</span><span class="sxs-lookup"><span data-stu-id="918ff-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="918ff-107">.NET Apache Spark, büyük veri analizinin dünyasına katılmak üzere .NET deneyimi veya kod esaslarını içeren geliştiricilere güç sağlar.</span><span class="sxs-lookup"><span data-stu-id="918ff-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="918ff-108">Apache Spark için .NET, C# ve F # ' dan Spark kullanmaya yönelik yüksek performanslı API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="918ff-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="918ff-109">C# ve F # ile erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="918ff-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="918ff-110">Yapılandırılmış verilerle çalışmaya yönelik DataFrame ve parlak SQL.</span><span class="sxs-lookup"><span data-stu-id="918ff-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="918ff-111">Akış verileriyle çalışmak için Spark yapılandırılmış akışı.</span><span class="sxs-lookup"><span data-stu-id="918ff-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="918ff-112">SQL söz dizimi ile sorgu yazmak için Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="918ff-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="918ff-113">Daha hızlı eğitim ve tahmin için makine öğrenimi tümleştirmesi (yani, [ml.net](https://dot.net/ml)ile birlikte Apache Spark için .NET kullanın).</span><span class="sxs-lookup"><span data-stu-id="918ff-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="918ff-114">Apache Spark .net, .NET uygulamaları genelinde ortak olan bir .NET API 'si belirtimi olan .NET Standard uyumludur.</span><span class="sxs-lookup"><span data-stu-id="918ff-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="918ff-115">Bu, .NET kodu yazdığınız her yerde Apache Spark için .NET kullanabilmeniz anlamına gelir. Bu durumda, .net geliştiricisi olarak sahip olduğunuz tüm bilgi, beceriler, kod ve kitaplıkları yeniden kullanmanıza olanak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="918ff-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="918ff-116">.NET Core kullanan Windows, Linux ve macOS 'ta Apache Spark için .NET.</span><span class="sxs-lookup"><span data-stu-id="918ff-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="918ff-117">Ayrıca, .NET Framework kullanarak Windows üzerinde de çalışır.</span><span class="sxs-lookup"><span data-stu-id="918ff-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="918ff-118">Uygulamalarınızı, AWS 'de Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks ve Databricks dahil olmak üzere tüm önemli bulut sağlayıcılarına dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="918ff-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="918ff-119">Apache Spark mimarisi için .NET</span><span class="sxs-lookup"><span data-stu-id="918ff-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="918ff-120">Spark 'a C#/F # dili bağlama, daha kolay genişletilebilirlik sunan yeni bir Spark birlikte çalışma katmanında yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="918ff-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="918ff-121">Spark Interop 'in bu yeni katmanı, dil uzantısı için en iyi yöntemler kullanılarak yazılmıştır ve birlikte çalışma ve performans için optimize edildi.</span><span class="sxs-lookup"><span data-stu-id="918ff-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="918ff-122">Bu genişletilebilirlik, Spark 'daki diğer dillere yönelik destek eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="918ff-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="918ff-123">![Apache Spark mimarisi için .NET](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="918ff-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="918ff-124">[Önerinin](https://issues.apache.org/jira/browse/SPARK-26257)Spark dil uzantıları için birlikte çalışma desteği hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="918ff-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="918ff-125">Apache Spark performans için .NET</span><span class="sxs-lookup"><span data-stu-id="918ff-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="918ff-126">[TPC-H kıyaslaması](http://www.tpc.org/tpch/)kullanılarak Python ve Scala karşılaştırıldığında, Apache Spark için .net çoğu durumda en iyi şekilde çalışır ve Kullanıcı tanımlı işlev performansı önemli olduğunda Python 'dan daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="918ff-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="918ff-127">Geliştirme ve kıyaslama performansı için devam eden bir çaba vardır.</span><span class="sxs-lookup"><span data-stu-id="918ff-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="918ff-128">Kendi benchişaretlemesini yapmak için, bkz. [Apache Spark GitHub için .net](https://github.com/dotnet/spark/tree/master/benchmark)üzerinde bulunan kıyaslamalar.</span><span class="sxs-lookup"><span data-stu-id="918ff-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="918ff-129">Apache Spark yol haritası için .NET</span><span class="sxs-lookup"><span data-stu-id="918ff-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="918ff-130">[Apache Spark yol haritası için resmi .net](https://github.com/dotnet/spark/blob/master/ROADMAP.md)'ten kısa süreli ve uzun süreli planlar hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="918ff-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="918ff-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="918ff-131">.NET Foundation</span></span>

<span data-ttu-id="918ff-132">Apache Spark projesi .net [Foundation](https://www.dotnetfoundation.org/)'ın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="918ff-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="918ff-133">Katkılar</span><span class="sxs-lookup"><span data-stu-id="918ff-133">Contributions</span></span>

<span data-ttu-id="918ff-134">Apache Spark ekibi için .NET, hem GitHub sorunları hem de çekme istekleri katkılarını teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="918ff-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="918ff-135">İlk olarak, mevcut bir [sorunu](https://github.com/dotnet/spark/issues)arayın.</span><span class="sxs-lookup"><span data-stu-id="918ff-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="918ff-136">Mevcut bir sorunu bulamazsanız [Yeni bir sorun açın](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span><span class="sxs-lookup"><span data-stu-id="918ff-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="918ff-137">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="918ff-137">Next steps</span></span>

<span data-ttu-id="918ff-138">Apache Spark için .NET 'i deneyin.</span><span class="sxs-lookup"><span data-stu-id="918ff-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="918ff-139">Öğretici: Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="918ff-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
