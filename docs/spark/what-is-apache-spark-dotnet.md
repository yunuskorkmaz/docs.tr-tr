---
title: Apache Spark için .NET nedir?
description: Spark'ı .NET kodunu yazdığınız her yere götüren ücretsiz, açık kaynak kodlu ve çapraz platform lu büyük veri analizi çerçevesi apache Spark için .NET hakkında bilgi edinin.
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458193"
---
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="e80da-103">Apache Spark için .NET nedir?</span><span class="sxs-lookup"><span data-stu-id="e80da-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="e80da-104">[Apache Spark,](what-is-spark.md) genellikle terabaytlar veya petabaytlar kadar veri kümesi üzerinden analitik için genel amaçlı dağıtılmış bir işleme motorudur.</span><span class="sxs-lookup"><span data-stu-id="e80da-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="e80da-105">Popüler açık kaynak büyük veri analizi çerçevesi için ücretsiz, açık kaynak ve çapraz platform .NET Desteği olan Apache Spark için .NET ile artık bildiğiniz dilleri kullanarak büyük veri uygulamalarınıza Apache Spark'ın gücünü ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e80da-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="e80da-106">Apache Spark için neden .NET'i seçmelisiniz?</span><span class="sxs-lookup"><span data-stu-id="e80da-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="e80da-107">.NET for Apache Spark, geliştiricileri .NET deneyimi veya kod tabanlarıyla büyük veri analitiği dünyasına katılmaları için güçlendirir.</span><span class="sxs-lookup"><span data-stu-id="e80da-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="e80da-108">.NET for Apache Spark, C# ve F#'dan Spark'ı kullanmak için yüksek performanslı API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e80da-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="e80da-109">C# ve F# ile şu hizmetlere erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e80da-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="e80da-110">Yapılandırılmış verilerle çalışmak için DataFrame ve SparkSQL.</span><span class="sxs-lookup"><span data-stu-id="e80da-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="e80da-111">Veri akışıyla çalışmak için Yapılandırılmış Akış'ı kıvılcımlandırın.</span><span class="sxs-lookup"><span data-stu-id="e80da-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="e80da-112">SQL sözdizimi ile sorgu yazmak için SQL'i spark.</span><span class="sxs-lookup"><span data-stu-id="e80da-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="e80da-113">Daha hızlı eğitim ve tahmin için makine öğrenimi entegrasyonu (diğer bir süre [ML.NET](https://dot.net/ml)yanında Apache Spark için .NET kullanın).</span><span class="sxs-lookup"><span data-stu-id="e80da-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="e80da-114">.NET for Apache Spark, .NET uygulamaları arasında yaygın olan .NET API'lerinin resmi bir belirtimi olan .NET Standard ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e80da-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="e80da-115">Bu, .NET kodunu yazdığınız her yerde .NET için .NET'i kullanabilirsiniz ve bu sayede bir .NET geliştiricisi olarak sahip olduğunuz tüm bilgi, beceri, kod ve kitaplıkları yeniden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e80da-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="e80da-116">.NET for Apache Spark , .NET Core kullanarak Windows, Linux ve macOS'ta çalışır.</span><span class="sxs-lookup"><span data-stu-id="e80da-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="e80da-117">Ayrıca .NET Framework kullanarak Windows üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e80da-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="e80da-118">Uygulamalarınızı Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks ve Databricks gibi tüm büyük bulut sağlayıcılarına AWS'de dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e80da-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="e80da-119">.NET Apache Spark mimarisi için</span><span class="sxs-lookup"><span data-stu-id="e80da-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="e80da-120">Kıvılcım'a bağlanan C#/ F# dili, daha kolay genişletilebilirlik sunan yeni bir Spark interop katmanı üzerine yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e80da-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="e80da-121">Spark interop bu yeni katman dil uzantısı için en iyi uygulamalar kullanılarak yazılmış ve interop ve performans için optimize eder.</span><span class="sxs-lookup"><span data-stu-id="e80da-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="e80da-122">Uzun vadede, bu genişletilebilirlik Spark diğer diller için destek eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e80da-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="e80da-123">![.NET Apache Spark mimarisi için](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="e80da-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="e80da-124">Spark dil uzantıları için interop desteği hakkında tekliften bilgi [edinebilirsiniz.](https://issues.apache.org/jira/browse/SPARK-26257)</span><span class="sxs-lookup"><span data-stu-id="e80da-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="e80da-125">.NET Apache Spark performansı için</span><span class="sxs-lookup"><span data-stu-id="e80da-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="e80da-126">[TPC-H kıyaslama](http://www.tpc.org/tpch/)kullanarak Python ve Scala ile karşılaştırıldığında, Apache Spark için .NET çoğu durumda iyi performans gösterir ve kullanıcı tanımlı işlev performansı kritik olduğunda Python'dan 2 kat daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="e80da-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="e80da-127">Performansı artırmak ve kıyaslamak için devam eden bir çaba vardır.</span><span class="sxs-lookup"><span data-stu-id="e80da-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="e80da-128">Kendi kıyaslama yapmak [için, Apache Spark GitHub için .NET'te](https://github.com/dotnet/spark/tree/master/benchmark)bulunan kriterlere bakın.</span><span class="sxs-lookup"><span data-stu-id="e80da-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="e80da-129">.NET için Apache Spark yol haritası</span><span class="sxs-lookup"><span data-stu-id="e80da-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="e80da-130">[Apache Spark yol haritası için](https://github.com/dotnet/spark/blob/master/ROADMAP.md)resmi .NET'ten kısa ve uzun vadeli planlar hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="e80da-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="e80da-131">.NET Vakfı</span><span class="sxs-lookup"><span data-stu-id="e80da-131">.NET Foundation</span></span>

<span data-ttu-id="e80da-132">Apache Spark projesinin .NET projesi [.NET Foundation'ın](https://www.dotnetfoundation.org/)bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e80da-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="e80da-133">Contributions</span><span class="sxs-lookup"><span data-stu-id="e80da-133">Contributions</span></span>

<span data-ttu-id="e80da-134">Apache Spark ekibinin .NET ekibi, hem GitHub sorunları hem de çekme istekleri ni, katkıları teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="e80da-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="e80da-135">İlk olarak, [varolan](https://github.com/dotnet/spark/issues)bir sorunu arayın.</span><span class="sxs-lookup"><span data-stu-id="e80da-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="e80da-136">Varolan bir sorunu bulamıyorsanız, [yeni bir sorun açın.](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)</span><span class="sxs-lookup"><span data-stu-id="e80da-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e80da-137">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e80da-137">Next steps</span></span>

<span data-ttu-id="e80da-138">Apache Spark için .NET'i deneyin.</span><span class="sxs-lookup"><span data-stu-id="e80da-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e80da-139">Öğretici: Apache Spark için .NET ile başlayın</span><span class="sxs-lookup"><span data-stu-id="e80da-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
