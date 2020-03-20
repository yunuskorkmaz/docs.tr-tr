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
# <a name="what-is-net-for-apache-spark"></a>Apache Spark için .NET nedir?

[Apache Spark,](what-is-spark.md) genellikle terabaytlar veya petabaytlar kadar veri kümesi üzerinden analitik için genel amaçlı dağıtılmış bir işleme motorudur. Popüler açık kaynak büyük veri analizi çerçevesi için ücretsiz, açık kaynak ve çapraz platform .NET Desteği olan Apache Spark için .NET ile artık bildiğiniz dilleri kullanarak büyük veri uygulamalarınıza Apache Spark'ın gücünü ekleyebilirsiniz.

## <a name="why-choose-net-for-apache-spark"></a>Apache Spark için neden .NET'i seçmelisiniz?

.NET for Apache Spark, geliştiricileri .NET deneyimi veya kod tabanlarıyla büyük veri analitiği dünyasına katılmaları için güçlendirir. .NET for Apache Spark, C# ve F#'dan Spark'ı kullanmak için yüksek performanslı API'ler sağlar. C# ve F# ile şu hizmetlere erişebilirsiniz:

* Yapılandırılmış verilerle çalışmak için DataFrame ve SparkSQL.
* Veri akışıyla çalışmak için Yapılandırılmış Akış'ı kıvılcımlandırın.
* SQL sözdizimi ile sorgu yazmak için SQL'i spark.
* Daha hızlı eğitim ve tahmin için makine öğrenimi entegrasyonu (diğer bir süre [ML.NET](https://dot.net/ml)yanında Apache Spark için .NET kullanın).

.NET for Apache Spark, .NET uygulamaları arasında yaygın olan .NET API'lerinin resmi bir belirtimi olan .NET Standard ile uyumludur. Bu, .NET kodunu yazdığınız her yerde .NET için .NET'i kullanabilirsiniz ve bu sayede bir .NET geliştiricisi olarak sahip olduğunuz tüm bilgi, beceri, kod ve kitaplıkları yeniden kullanabilirsiniz.

.NET for Apache Spark , .NET Core kullanarak Windows, Linux ve macOS'ta çalışır. Ayrıca .NET Framework kullanarak Windows üzerinde çalışır. Uygulamalarınızı Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks ve Databricks gibi tüm büyük bulut sağlayıcılarına AWS'de dağıtabilirsiniz.

## <a name="net-for-apache-spark-architecture"></a>.NET Apache Spark mimarisi için

Kıvılcım'a bağlanan C#/ F# dili, daha kolay genişletilebilirlik sunan yeni bir Spark interop katmanı üzerine yazılmıştır. Spark interop bu yeni katman dil uzantısı için en iyi uygulamalar kullanılarak yazılmış ve interop ve performans için optimize eder. Uzun vadede, bu genişletilebilirlik Spark diğer diller için destek eklemek için kullanılabilir.

> [!div class="mx-imgBorder"]
> ![.NET Apache Spark mimarisi için](media/dotnet-spark-architecture.png)

Spark dil uzantıları için interop desteği hakkında tekliften bilgi [edinebilirsiniz.](https://issues.apache.org/jira/browse/SPARK-26257)

## <a name="net-for-apache-spark-performance"></a>.NET Apache Spark performansı için

[TPC-H kıyaslama](http://www.tpc.org/tpch/)kullanarak Python ve Scala ile karşılaştırıldığında, Apache Spark için .NET çoğu durumda iyi performans gösterir ve kullanıcı tanımlı işlev performansı kritik olduğunda Python'dan 2 kat daha hızlıdır. Performansı artırmak ve kıyaslamak için devam eden bir çaba vardır.

Kendi kıyaslama yapmak [için, Apache Spark GitHub için .NET'te](https://github.com/dotnet/spark/tree/master/benchmark)bulunan kriterlere bakın.

## <a name="net-for-apache-spark-roadmap"></a>.NET için Apache Spark yol haritası

[Apache Spark yol haritası için](https://github.com/dotnet/spark/blob/master/ROADMAP.md)resmi .NET'ten kısa ve uzun vadeli planlar hakkında bilgi edinin.

## <a name="net-foundation"></a>.NET Vakfı

Apache Spark projesinin .NET projesi [.NET Foundation'ın](https://www.dotnetfoundation.org/)bir parçasıdır.

## <a name="contributions"></a>Contributions

Apache Spark ekibinin .NET ekibi, hem GitHub sorunları hem de çekme istekleri ni, katkıları teşvik eder. İlk olarak, [varolan](https://github.com/dotnet/spark/issues)bir sorunu arayın. Varolan bir sorunu bulamıyorsanız, [yeni bir sorun açın.](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)

## <a name="next-steps"></a>Sonraki adımlar

Apache Spark için .NET'i deneyin.
> [!div class="nextstepaction"]
> [Öğretici: Apache Spark için .NET ile başlayın](./tutorials/get-started.md)
