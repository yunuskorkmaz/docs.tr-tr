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
# <a name="what-is-apache-spark"></a>Apache Spark nedir?

[Apache Spark,](https://spark.apache.org/) büyük verileri çözümleyen uygulamaların performansını artırmak için bellek içi işlemeyi destekleyen açık kaynaklı paralel bir işlem çerçevesidir. Büyük veri çözümleri, geleneksel veritabanları için çok büyük veya karmaşık verileri işlemek üzere tasarlanmıştır. Spark bellekte büyük miktarda veri işler, bu da disk tabanlı alternatiflerden çok daha hızlıdır.

## <a name="common-big-data-scenarios"></a>Ortak büyük veri senaryoları

Büyük hacimli verileri depolamanız ve işlemeniz, yapılandırılmamış verileri dönüştürmeniz veya akış verilerini işlemeniz gerekiyorsa büyük bir veri mimarisi düşünebilirsiniz. Spark, birkaç büyük veri senaryosu için kullanılabilecek genel amaçlı dağıtılmış işleme altyapısıdır.

### <a name="extract-transform-and-load-etl"></a>Ayıklama, dönüştürme ve yükleme (ETL)

[Ayıklama, dönüştürme ve yükleme (ETL),](/azure/architecture/data-guide/relational-data/etl) bir veya birden çok kaynaktan veri toplama, verileri değiştirme ve verileri yeni bir veri deposuna taşıma işlemidir. Verileri dönüştürmenin çeşitli yolları vardır:

* Filtreleme
* Sıralama
* Top -layarak
* Katma
* Temizleme
* Deduplicating
* Doğrulama

### <a name="real-time-data-stream-processing"></a>Gerçek zamanlı veri akışı işleme

Akış veya gerçek zamanlı, veri hareket halindeki verilerdir. IoT aygıtlarından, web günlüklerinden ve tıklama akışlarından telemetri, veri akışına örnektir. Jeouzamsal analiz, uzaktan izleme ve anomali algılama gibi yararlı bilgiler sağlamak için gerçek zamanlı veriler işlenebilir. İlişkisel veriler gibi, verileri bir çıktı lavabosuna taşımadan önce akış verilerini filtreleyebilir, toplayabilir ve hazırlayabilirsiniz. Apache Spark, [Spark Streaming](https://spark.apache.org/streaming/)aracılığıyla [gerçek zamanlı veri akışı işlemeyi](/azure/architecture/data-guide/big-data/real-time-processing) destekler.

### <a name="batch-processing"></a>Toplu işlem

[Toplu işlem,](/azure/architecture/data-guide/big-data/batch-processing) büyük verilerin istirahathalinde işlenmesidir. Paralel olarak uzun süren işleri kullanarak çok büyük veri kümelerini filtreleyebilir, toplayabilir ve hazırlayabilirsiniz.

### <a name="machine-learning-through-mllib"></a>MLlib ile makine öğrenimi

Makine öğrenimi ileri analitik problemler için kullanılır. Bilgisayarınız, gelecekteki davranışları, sonuçları ve eğilimleri tahmin etmek veya tahmin etmek için varolan verileri kullanabilir. Apache Spark makine öğrenme kütüphanesi, [MLlib,](https://spark.apache.org/mllib/)çeşitli makine öğrenme algoritmaları ve yardımcı programları içerir.

### <a name="graph-processing-through-graphx"></a>GraphX ile grafik işleme

Grafik, kenarlarla birbirine bağlı düğümler topluluğudur. Hiyerarşik verileriniz veya birbirine bağlı ilişkileri olan verileriniz varsa bir grafik veritabanı kullanabilirsiniz. Bu verileri Apache Spark'ın [GraphX](https://spark.apache.org/graphx/) API'sini kullanarak işleyebilirsiniz.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>Spark SQL ile SQL ve yapılandırılmış veri işleme

Yapılandırılmış (biçimlendirilmiş) verilerle çalışıyorsanız, [Spark SQL'i](https://spark.apache.org/sql/)kullanarak Spark uygulamanızda SQL sorgularını kullanabilirsiniz.

## <a name="apache-spark-architecture"></a>Apache Spark mimarisi

Ana/işçi mimarisini kullanan Apache Spark'ın üç ana bileşeni vardır: sürücü, uygulayıcılar ve küme yöneticisi.

![Apache Spark mimarisi](media/spark-architecture.png)

### <a name="driver"></a>Sürücü

Sürücü, C# konsolu uygulaması ve Bir Kıvılcım oturumu gibi programınızdan oluşur. Kıvılcım oturumu programınızı alır ve uygulayıcılar tarafından işlenen daha küçük görevlere böler.

### <a name="executors"></a>Executors

Her uygulayıcı veya alt düğüm, sürücüden bir görev alır ve bu görevi yürütür. Uygulayıcılar küme olarak bilinen bir varlıkta ikamet eder.

### <a name="cluster-manager"></a>Küme yöneticisi

Küme yöneticisi hem sürücü hem de uygulayıcılarla aşağıdakiiletişim kurar:

* Kaynak tahsisini yönetme
* Program bölümünü yönetme
* Program yürütmeyi yönetme

## <a name="language-support"></a>Dil desteği

Apache Spark aşağıdaki programlama dillerini destekler:

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>Kıvılcım API'leri

Apache Spark aşağıdaki API'leri destekler:

* [Kıvılcım Scala API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Kıvılcım Java API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Kıvılcım Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Kıvılcım R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), yerleşik işlevler

## <a name="next-steps"></a>Sonraki adımlar

.NET uygulamanızda Apache Spark'ı nasıl kullanabileceğinizi öğrenin. Apache Spark için .NET ile .NET deneyimi ve iş mantığına sahip geliştiriciler C# ve F# ile büyük veri sorguları yazabilirler.
> [!div class="nextstepaction"]
> [Apache Spark için .NET nedir](what-is-apache-spark-dotnet.md)
