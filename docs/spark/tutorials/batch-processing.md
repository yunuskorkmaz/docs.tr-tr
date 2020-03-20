---
title: Apache Spark öğreticisi için .NET ile toplu işleme
description: Apache Spark için .NET'i kullanarak toplu işlemenin nasıl yapılacağını öğrenin.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: 460c37e66c2c0a8a9b197a9abaff9eead842bdeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187560"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile toplu işleme yapın

Bu eğitimde, Apache Spark için .NET'i kullanarak toplu işleme yapmayı öğrenirsiniz. Toplu işlem, veri lerin istirahat halindeki dönüşümüdür, yani kaynak veriler zaten veri depolamaya yüklenmiştir.

Toplu işlem genellikle daha fazla analiz için hazırlanması gereken büyük, düz veri kümeleri üzerinde gerçekleştirilir. Günlük işleme ve veri ambarı yaygın toplu işleme senaryolarıdır. Bu senaryoda, farklı projelerin çatallandığı süre veya projelerin ne kadar yakın zamanda güncelleştirilmiş olduğu gibi GitHub projeleri hakkındaki bilgileri çözümlersiniz.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> * Apache Spark uygulaması için bir .NET oluşturma ve çalıştırma
> * Verileri DataFrame'e okuyun ve analize hazırlayın
> * Spark SQL kullanarak verileri işleme

## <a name="prerequisites"></a>Önkoşullar

Apache Spark için .NET'i ilk kez kullanıyorsanız, ortamınızı nasıl hazırlayacağınızı öğrenmek ve Apache Spark uygulaması için ilk .NET'inizi çalıştırmak [için Apache Spark öğreticisi için .NET ile başlayın'a](../tutorials/get-started.md) göz atın.

## <a name="download-the-sample-data"></a>Örnek verileri indirme

[GHTorrent,](http://ghtorrent.org/) projeler, taahhütler ve izleyiciler hakkında bilgi gibi tüm herkese açık GitHub olaylarını izler ve olayları ve yapılarını veritabanlarında saklar. Farklı zaman dilimlerinde toplanan veriler indirilebilir arşivler olarak kullanılabilir. Döküm dosyaları çok büyük olduğundan, bu kılavuz, GitHub'dan indirilebilen [döküm dosyasının kesilmiş bir sürümünü](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) kullanır.

> [!NOTE]
> GHTorrent veri seti çift lisans programı[(Creative Commons + )](https://wiki.creativecommons.org/wiki/CCPlus)altında dağıtılır. Ticari olmayan kullanımlar için (eğitim, araştırma veya kişisel kullanımlar dahil ancak bunlarla sınırlı olmamak üzere), veri kümesi [CC-BY-SA lisansı](https://creativecommons.org/licenses/by-sa/4.0/)altında dağıtılır.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Komut isteminizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   Komut `dotnet` sizin için `new` bir `console` tür uygulaması oluşturur. Parametre, `-o` uygulamanızın depolandığı *mySparkBatchApp* adında bir dizin oluşturur ve gerekli dosyalarla doldurulur. Komut, `cd mySparkBatchApp` dizini yeni oluşturduğunuz uygulama dizinine değiştirir.

1. Bir uygulamada Apache Spark için .NET'i kullanmak için Microsoft.Spark paketini yükleyin. Konsolunuzda aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Bir SparkSession oluşturma

1. aşağıdaki ek `using` ifadeleri *mySparkBatchApp'taki* *Program.cs* dosyasının üst bölümüne ekleyin.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Proje ad alanınıza aşağıdaki kodu ekleyin. *s_referenceData* daha sonra programda tarihe göre filtrelemek için kullanılır.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Yeni bir SparkSession oluşturmak için Ana yönteminizin içine aşağıdaki kodu ekleyin. SparkSession, Dataset ve DataFrame API ile Spark programlamanın giriş noktasıdır. Nesneyi `spark` arayarak, programınız boyunca Spark ve DataFrame işlevlerine erişebilirsiniz.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Verileri hazırlama

1. Giriş `DataFrame`dosyasını, adlandırılmış sütunlara düzenlenen dağıtılmış veri koleksiyonu na göre okuyun. Verileriniz için sütunları <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>' dan ayarlayabilirsiniz. Verileri <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> DataFrame'inizde görüntülemek için yöntemi kullanın. CSV dosya yolunu indirdiğiniz GitHub verilerinin konumuna güncelleştirdiğinden emin olun.

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. NA <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> (null) değerleriyle satırları düşürmek için <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> yöntemi ve verilerinizden belirli sütunları kaldırma yöntemini kullanın. Bu, son çözümlemenizde alakalı olmayan boş verileri veya sütunları çözümlemeye çalışırsanız hataları önlemeye yardımcı olur.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Verileri analiz edin

Spark SQL, verilerinizde SQL aramaları yapmanızı sağlar. DataFrame'inizin tüm satırlarına kullanıcı tanımlı bir işlev uygulamak için kullanıcı tanımlı işlevleri ve Spark SQL'i birleştirmek yaygındır.

Özellikle diğer `spark.Sql` uygulama türlerinde görülen standart SQL çağrılarını taklit etmek için arayabilirsiniz. Ayrıca, verilerinizdeki <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> hesaplamaları birleştirmek, filtrelemek ve gerçekleştirmek gibi yöntemleri de çağırabilir ve <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> özel olarak arayabilirsiniz.

Bu uygulamanın amacı GitHub projeleri verileri hakkında bazı bilgiler elde etmektir. Verileri analiz etmek için programınıza aşağıdaki kod parçacıklarını ekleyin.

1. Aşağıdaki kod bloğunu ekleyin, her dilin çatallı sayısını bulur. İlk olarak, veriler dile göre gruplandırılır. Daha sonra, her dilden ortalama çatal sayısı alınır.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Hangi dillerin en çok çatallı olduğunu görmek için azalan sırada ortalama çatal sayısını sipariş etmek için aşağıdaki kod bloğunu ekleyin. Diğer bir tarihte, önce en fazla sayıda çatal görünür.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. Bir sonraki kod bloğu, projelerin ne kadar yakın zamanda güncelleştirildiğini gösterir. *MyUDF* adlı yeni bir kullanıcı tanımlı işlevi kaydeder ve öğreticinin başında bildirilen bir tarih, *s_referenceDate*ile karşılaştırın. Her projenin tarihi başvuru tarihiyle karşılaştırılır. Daha sonra, Spark SQL veri kümesindeki her projeyi çözümlemek için verilerin her satırında UDF çağırmak için kullanılır.

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. SparkSession'ı sona erdirmek için arayın. `spark.Stop()`

## <a name="use-spark-submit-to-run-your-app"></a>Uygulamanızı çalıştırmak için kıvılcım gönder'i kullanma

1. .NET uygulamanızı oluşturmak için aşağıdaki komutu kullanın:

   ```dotnetcli
   dotnet build
   ```

1. Uygulamanızı ' `spark-submit`ile çalıştırın. Microsoft Spark jar dosyanıza giden gerçek yollarla aşağıdaki komutu güncelleştirdiğinden emin olun.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Kodu alma

Tüm [çözümü](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) GitHub'da görebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Apache Spark için .NET ile akış verilerini nasıl işeceğinizi öğrenmek için bir sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici: Apache Spark için .NET ile Yapılandırılmış Akış](streaming.md)
