---
title: Apache Spark öğreticisi için .NET ile Batch işleme
description: Apache Spark için .NET kullanarak toplu işleme yapmayı öğrenin.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: bd91fb401b9beb6ae74c4599b25e43284473f8b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75466415"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile Batch işleme

Bu öğreticide, Apache Spark için .NET kullanarak toplu işleme yapmayı öğreneceksiniz. Toplu işlem, kaynak verilerin daha önce veri depolamaya yüklenmiş olduğu anlamına gelen verilerin bekleyen dönüşümdedir. 

Toplu işleme genellikle daha fazla analiz için hazırlanması gereken büyük ve düz veri kümelerinde gerçekleştirilir. Günlük işleme ve veri ambarı, yaygın toplu işleme senaryolardır. Bu senaryoda, farklı projelerin kullanıldığı zaman sayısı veya son projelerin güncelleştirildiği süre gibi GitHub projeleri hakkındaki bilgileri analiz edersiniz. 

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Apache Spark uygulaması için .NET oluşturma ve çalıştırma
> * Verileri bir veri çerçevesine okuyun ve analiz için hazırlayın
> * Spark SQL kullanarak verileri işleme

## <a name="prerequisites"></a>Prerequisites 

Apache Spark için .NET 'i ilk kez kullanıyorsanız, ortamınızı nasıl hazırlayacağınızı ve Apache Spark uygulama için ilk .NET uygulamanızı nasıl çalıştıracağınızı öğrenmek için [.NET ile çalışmaya başlama](../tutorials/get-started.md) hakkında bilgi edinmek için Apache Spark öğreticisine göz atın.

## <a name="download-the-sample-data"></a>Örnek verileri indirme

[Ghtorkiralık](http://ghtorrent.org/) , projeler, işlemeler ve izleyicileri hakkında bilgi gibi tüm genel GitHub olaylarını izler ve olayları ve bunların yapısını veritabanlarında depolar. Farklı zaman dilimlerinde toplanan veriler indirilebilir Arşivler olarak kullanılabilir. Döküm dosyaları çok büyük olduğundan, bu kılavuz GitHub 'dan indirilebilen [döküm dosyasının kesilmiş bir sürümünü](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) kullanır.

> [!NOTE]
> Ghtorıo veri kümesi, bir çift lisanslama şeması ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)) altında dağıtılır. Ticari olmayan kullanımlar için (eğitim, araştırma veya kişisel kullanımları dahil, ancak bunlarla sınırlı olmamak üzere), veri kümesi, [bilgi-SA lisansı](https://creativecommons.org/licenses/by-sa/4.0/)altında dağıtılır.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Komut istemindeki yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   `dotnet` komutu sizin için `console` türünde bir `new` uygulaması oluşturur. `-o` parametresi, uygulamanızın depolandığı *Mymini Batchapp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur. `cd mySparkBatchApp` komutu, dizini yeni oluşturduğunuz uygulama diziniyle değiştirir.

1. .NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için. Konsolunuza aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Mini oturum oluşturma

1. Aşağıdaki ek `using` deyimlerini *Mymini Batchapp*'teki *program.cs* dosyasının en üstüne ekleyin.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Aşağıdaki kodu proje ad alanına ekleyin. *s_referenceData* , programın daha sonra tarihe göre filtrelemek için kullanılır.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Yeni bir mini oturum oluşturmak için aşağıdaki kodu Main yönteminizin içine ekleyin. Mini veri kümesi ve DataFrame API 'SI ile Spark programlama için mini oturum giriş noktasıdır. `spark` nesnesini çağırarak, program genelinde Spark ve DataFrame işlevlerine erişebilirsiniz.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Verileri hazırlama

1. Giriş dosyasını, adlandırılmış sütunlara düzenlenmiş bir veri koleksiyonu olan bir `DataFrame`okuyun. Verilerinize ait sütunları <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>aracılığıyla ayarlayabilirsiniz. Veri Çerçevinizdeki verileri göstermek için <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> yöntemini kullanın. CSV dosya yolunu indirdiğiniz GitHub verilerinin konumuyla güncelleştirdiğinizden emin olun.

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

1. Verileri boş (null) değerleri ile bırakmak için <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> yöntemini ve verilerden belirli sütunları kaldırmak için <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> yöntemini kullanın. Bu, son analiziyle ilgili olmayan null verileri veya sütunları çözümlemeyi denerseniz hataları önlemeye yardımcı olur.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Verileri analiz etme

Spark SQL, verileriniz üzerinde SQL çağrıları yapmanıza olanak tanır. Veri Çerçevinizdeki tüm satırlara Kullanıcı tanımlı bir işlev uygulamak için Kullanıcı tanımlı işlevleri ve Spark SQL 'i birleştirmek yaygındır.

Diğer tür uygulamalarda görülen standart SQL çağrılarını taklit etmek için `spark.Sql` özel olarak çağırabilirsiniz. Ayrıca, <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> ve <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> gibi yöntemleri çağırıp verilerinize özel olarak birleştirme, filtre uygulama ve hesaplamalar yapma işlemleri yapabilirsiniz.

Bu uygulamanın hedefi, GitHub projeleri verileri hakkında bazı öngörülere sahip olmaktır. Verileri çözümlemek için programınıza aşağıdaki kod parçacıklarını ekleyin.

1. Aşağıdaki kod bloğunu eklemek, her dilin ne kadar ele geçirilmiş olduğunu bulur. İlk olarak, veriler dile göre gruplandırılır. Ardından, her dilden ortalama çatalların sayısı alınır.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. En çok kullanılan dilleri görmek için Ortalama çatalların sayısını azalan sırada sıralamak üzere aşağıdaki kod bloğunu ekleyin. Yani, en fazla çatallar ilk olarak görünür.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show(); 
   ```

1. Sonraki kod bloğu, son projelerin güncelleştirilme şeklini gösterir. *MyUDF* adlı yeni bir Kullanıcı tanımlı işlevi kaydeder ve öğreticinin başlangıcında bildirildiği bir tarih, *s_referenceDate*ile karşılaştırın. Her projenin tarihi başvuru tarihine göre karşılaştırılır. Daha sonra Spark SQL, veri kümesindeki her bir projeyi analiz etmek üzere verilerin her satırında UDF 'yi çağırmak için kullanılır.

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

1. Parlak oturumu sonlandırmak için `spark.Stop()` çağırın.

## <a name="use-spark-submit-to-run-your-app"></a>Uygulamanızı çalıştırmak için Spark-Gönder kullanın

1. .NET uygulamanızı derlemek için aşağıdaki komutu kullanın:

   ```dotnetcli
   dotnet build
   ```

1. Uygulamanızı `spark-submit`çalıştırın. Aşağıdaki komutu Microsoft Spark jar dosyanıza yönelik gerçek yollarla güncelleştirdiğinizden emin olun.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Kodu edinin

[Tam çözümü](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) GitHub ' da görebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Apache Spark için .NET ile akış verilerini nasıl işleyebileceğinizi öğrenmek için sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici: Apache Spark için .NET ile yapılandırılmış akış](streaming.md)
