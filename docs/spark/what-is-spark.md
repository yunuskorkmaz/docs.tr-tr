---
title: Apache Spark nedir?
description: Apache Spark ve büyük veri senaryoları hakkında bilgi edinin.
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 187a37897c23809d91820bd79b476e775fb5b99b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583482"
---
# <a name="what-is-apache-spark"></a>Apache Spark nedir?

[Apache Spark](https://spark.apache.org/) , büyük verileri çözümleyen uygulamaların performansını artırmak üzere bellek içi işlemeyi destekleyen açık kaynaklı bir paralel işleme çerçevesidir. Büyük veri çözümleri geleneksel veritabanları için çok büyük veya karmaşık olan verileri işleyecek şekilde tasarlanmıştır. Spark, disk tabanlı alternatiflerden çok daha hızlı olan bellekteki büyük miktarda veriyi işler. 

## <a name="common-big-data-scenarios"></a>Yaygın büyük veri senaryoları

Büyük hacimlerdeki verileri depolamanız ve işlemek, yapılandırılmamış verileri dönüştürmek veya akış verilerini işlemek için büyük bir veri mimarisini düşünebilirsiniz. Spark, çok büyük veri senaryolarında kullanılabilen, genel amaçlı bir dağıtılmış işleme altyapısıdır. 

### <a name="extract-transform-and-load-etl"></a>Ayıklama, dönüştürme ve yükleme (ETL)

[Ayıklama, dönüştürme ve yükleme (ETL)](/azure/architecture/data-guide/relational-data/etl) , bir veya birden çok kaynaktan veri toplama, verileri değiştirme ve verileri yeni bir veri deposuna taşıma işlemidir. Aşağıdakiler dahil olmak üzere çeşitli veri dönüştürme yolları vardır:

* Filtreleme
* Sıralama
* Larla
* Katılma
* Temizlemek
* Yinelenen
* Doğrulamada

### <a name="real-time-data-stream-processing"></a>Gerçek zamanlı veri akışı işleme

Akış veya gerçek zamanlı veriler hareket halinde veriler. IoT cihazlarındaki telemetri, Weblogs ve tıklama akışları, akış verilerine örnek olarak verilebilir. Gerçek zamanlı veriler, Jeo-uzamsal analiz, uzaktan izleme ve anomali algılama gibi yararlı bilgiler sağlamak için işlenebilir. İlişkisel veriler gibi, verileri bir çıkış havuzuna taşımadan önce, akış verilerini filtreleyebilir, toplayabilir ve hazırlayabilirsiniz. Apache Spark [Spark akışı](https://spark.apache.org/streaming/)aracılığıyla [gerçek zamanlı veri akışı işlemesini](/azure/architecture/data-guide/big-data/real-time-processing) destekler. 

### <a name="batch-processing"></a>Toplu işleme

[Toplu işleme](/azure/architecture/data-guide/big-data/batch-processing) , bekleyen büyük verilerin işlenmesiyle ilgilenir. Uzun süre çalışan işleri kullanarak çok büyük veri kümelerini, paralel olarak filtreleyebilir, toplayabilir ve hazırlayabilir.

### <a name="machine-learning-through-mllib"></a>MLlib aracılığıyla makine öğrenimi

Makine öğrenimi, gelişmiş analitik sorunlar için kullanılır. Bilgisayarınız, gelecekteki davranışları, sonuçları ve eğilimleri tahmin etmek veya tahmin etmek için mevcut verileri kullanabilir. Apache Spark Machine Learning kitaplığı, [Mllib](https://spark.apache.org/mllib/), çeşitli makine öğrenimi algoritmalarını ve yardımcı programlarını içerir.

### <a name="graph-processing-through-graphx"></a>GraphX aracılığıyla grafik işleme

Grafik, kenarlara göre bağlanmış düğümlerin bir koleksiyonudur. Bağlantılı ilişkilerle verileri veya verileri hiyerarşik olarak kullandıysanız grafik veritabanını kullanabilirsiniz. Apache Spark [GraphX](https://spark.apache.org/graphx/) API 'sini kullanarak bu verileri işleyebilirsiniz.

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>Spark SQL ile SQL ve yapılandırılmış veri işleme

Yapılandırılmış (biçimli) verilerle çalışıyorsanız [Spark SQL](https://spark.apache.org/sql/)kullanarak Spark uygulamanızda SQL sorguları kullanabilirsiniz.

## <a name="apache-spark-architecture"></a>Apache Spark mimarisi

Ana/çalışan mimarisini kullanan Apache Spark, üç ana bileşene sahiptir: sürücü, yürüticileri ve Küme Yöneticisi.

![Apache Spark mimarisi](media/spark-architecture.png)

### <a name="driver"></a>Sürücü

Sürücü, bir C# konsol uygulaması ve Spark oturumu gibi, programından oluşur. Spark oturumu programınızı alır ve yürüticileri tarafından işlenen daha küçük görevlere böler.

### <a name="executors"></a>Yürütücüler

Her yürütücü veya çalışan düğümü, sürücüden bir görevi alır ve bu görevi yürütür. Yürüticileri, küme olarak bilinen bir varlıkta bulunur.

### <a name="cluster-manager"></a>Küme Yöneticisi

Küme Yöneticisi, hem sürücü hem de yürüticileri ile iletişim kurar:

* Kaynak ayırmayı yönetme
* Program bölümünü Yönet
* Program yürütmeyi yönetme

## <a name="language-support"></a>Dil desteği

Apache Spark aşağıdaki programlama dillerini destekler:

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>Spark API 'Leri

Apache Spark aşağıdaki API 'Leri destekler:

* [Spark Scala API 'SI](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Spark Java API 'SI](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Spark Python API 'SI](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Spark R API 'SI](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), yerleşik işlevler

## <a name="next-steps"></a>Sonraki adımlar

.NET uygulamanızda Apache Spark nasıl kullanabileceğinizi öğrenin. Apache Spark için .NET ile, .NET deneyimi ve iş mantığı olan geliştiriciler, ve C# F#' de büyük veri sorguları yazabilir.
> [!div class="nextstepaction"]
> [Apache Spark için .NET nedir?](what-is-apache-spark-dotnet.md)
