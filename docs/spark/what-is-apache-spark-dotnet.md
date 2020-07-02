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
# <a name="what-is-net-for-apache-spark"></a>Apache Spark için .NET nedir?

[Apache Spark](what-is-spark.md) , büyük veri kümeleri üzerinde analizler için genel amaçlı bir dağıtılmış işleme altyapısıdır. genellikle terabayt veya petabaytlarca veri. Popüler açık kaynaklı büyük veri analizi çerçevesi için Apache Spark, ücretsiz, açık kaynaklı ve platformlar arası .NET desteği için .NET ile, zaten bildiğiniz dilleri kullanarak Apache Spark gücünü büyük veri uygulamalarınıza ekleyebilirsiniz.

[!INCLUDE [spark-preview-note](../../includes/spark-preview-note.md)]

## <a name="why-choose-net-for-apache-spark"></a>Apache Spark için .NET neden seçmelisiniz?

.NET Apache Spark, büyük veri analizinin dünyasına katılmak üzere .NET deneyimi veya kod esaslarını içeren geliştiricilere güç sağlar. Apache Spark için .NET, C# ve F # ' dan Spark kullanmaya yönelik yüksek performanslı API 'Ler sağlar. C# ve F # ile erişebilirsiniz:

* Yapılandırılmış verilerle çalışmaya yönelik DataFrame ve parlak SQL.
* Akış verileriyle çalışmak için Spark yapılandırılmış akışı.
* SQL söz dizimi ile sorgu yazmak için Spark SQL.
* Daha hızlı eğitim ve tahmin için makine öğrenimi tümleştirmesi (yani, [ml.net](https://dot.net/ml)ile birlikte Apache Spark için .NET kullanın).

Apache Spark .net, .NET uygulamaları genelinde ortak olan bir .NET API 'si belirtimi olan .NET Standard uyumludur. Bu, .NET kodu yazdığınız her yerde Apache Spark için .NET kullanabilmeniz anlamına gelir. Bu durumda, .net geliştiricisi olarak sahip olduğunuz tüm bilgi, beceriler, kod ve kitaplıkları yeniden kullanmanıza olanak sağlanır.

.NET Core kullanan Windows, Linux ve macOS 'ta Apache Spark için .NET. Ayrıca, .NET Framework kullanarak Windows üzerinde de çalışır. Uygulamalarınızı, AWS 'de Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks ve Databricks dahil olmak üzere tüm önemli bulut sağlayıcılarına dağıtabilirsiniz.

## <a name="net-for-apache-spark-architecture"></a>Apache Spark mimarisi için .NET

Spark 'a C#/F # dili bağlama, daha kolay genişletilebilirlik sunan yeni bir Spark birlikte çalışma katmanında yazılmıştır. Spark Interop 'in bu yeni katmanı, dil uzantısı için en iyi yöntemler kullanılarak yazılmıştır ve birlikte çalışma ve performans için optimize edildi. Bu genişletilebilirlik, Spark 'daki diğer dillere yönelik destek eklemek için kullanılabilir.

> [!div class="mx-imgBorder"]
> ![Apache Spark mimarisi için .NET](media/dotnet-spark-architecture.png)

[Önerinin](https://issues.apache.org/jira/browse/SPARK-26257)Spark dil uzantıları için birlikte çalışma desteği hakkında bilgi edinebilirsiniz.

## <a name="net-for-apache-spark-performance"></a>Apache Spark performans için .NET

[TPC-H kıyaslaması](http://www.tpc.org/tpch/)kullanılarak Python ve Scala karşılaştırıldığında, Apache Spark için .net çoğu durumda en iyi şekilde çalışır ve Kullanıcı tanımlı işlev performansı önemli olduğunda Python 'dan daha hızlıdır. Geliştirme ve kıyaslama performansı için devam eden bir çaba vardır.

Kendi benchişaretlemesini yapmak için, bkz. [Apache Spark GitHub için .net](https://github.com/dotnet/spark/tree/master/benchmark)üzerinde bulunan kıyaslamalar.

## <a name="net-for-apache-spark-roadmap"></a>Apache Spark yol haritası için .NET

[Apache Spark yol haritası için resmi .net](https://github.com/dotnet/spark/blob/master/ROADMAP.md)'ten kısa süreli ve uzun süreli planlar hakkında bilgi edinin.

## <a name="net-foundation"></a>.NET Foundation

Apache Spark projesi .net [Foundation](https://www.dotnetfoundation.org/)'ın bir parçasıdır.

## <a name="contributions"></a>Katkılar

Apache Spark ekibi için .NET, hem GitHub sorunları hem de çekme istekleri katkılarını teşvik eder. İlk olarak, mevcut bir [sorunu](https://github.com/dotnet/spark/issues)arayın. Mevcut bir sorunu bulamazsanız [Yeni bir sorun açın](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).

## <a name="next-steps"></a>Sonraki adımlar

Apache Spark için .NET 'i deneyin.
> [!div class="nextstepaction"]
> [Öğretici: Apache Spark için .NET ile çalışmaya başlama](./tutorials/get-started.md)
