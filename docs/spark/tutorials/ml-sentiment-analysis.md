---
title: Apache Spark ve ML.NET öğreticisi için .NET ile yaklaşım Analizi
description: Bu öğreticide, yaklaşım analizi için Apache Spark .NET ile ML.NET kullanmayı öğreneceksiniz.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 69deb30419b98536fa309547d94f59bb266e413c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617592"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Öğretici: Apache Spark ve ML.NET için .NET ile yaklaşım Analizi

Bu öğretici, Apache Spark için ML.NET ve .NET kullanarak çevrimiçi incelemelere ilişkin yaklaşım analizinin nasıl yapılacağını öğretir. [Ml.net](http://dot.net/ml) , ücretsiz, platformlar arası, açık kaynaklı bir makine öğrenimi çerçevesidir. Makine öğrenimi algoritmalarının eğitimini ve tahminini ölçeklendirmek için Apache Spark .NET ile ML.NET kullanabilirsiniz.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Visual Studio 'da ML.NET model Oluşturucu kullanarak bir yaklaşım analiz modeli oluşturun.
> * Apache Spark konsol uygulaması için bir .NET oluşturun.
> * Kullanıcı tanımlı bir işlevi yazın ve uygulayın.
> * Apache Spark konsol uygulaması için bir .NET çalıştırın.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Ön koşullar

* Daha önce Apache Spark uygulama için bir .NET geliştirmediyse, temel bilgileri öğrenecek başlangıç [öğreticisiyle](get-started.md) başlayın. Bu öğreticiye devam etmeden önce başlangıç öğreticisine yönelik tüm önkoşulları doldurun.

* Bu öğretici, Visual Studio 'da kullanılabilen bir görsel arabirim olan ML.NET model oluşturucusunu (Önizleme) kullanır. Zaten Visual Studio yoksa, [Visual Studio 'Nun topluluk sürümünü](https://visualstudio.microsoft.com/downloads/) ücretsiz olarak indirebilirsiniz.

* [İndir ve yükle](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET model Oluşturucu (Önizleme).

* [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) indirin ve sarıp İnceleme veri kümelerini [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) .

## <a name="review-the-data"></a>Verileri gözden geçirin

Yelp İnceleme veri kümesi çeşitli hizmetlerle ilgili çevrimiçi sarık İncelemeleri içerir. [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) açın ve verilerin yapısına dikkat edin. İlk sütunda İnceleme metni bulunur ve ikinci sütun, yaklaşım puanlarını içerir. Yaklaşım puanı 1 ise, gözden geçirme pozitif olur ve yaklaşım puanı 0 ise, gözden geçirme negatif olur.

Aşağıdaki tabloda örnek veriler yer almaktadır:

|Belgemetinmetni|Yaklaşım|
|-|-|
|Wow... Bu yere iner.|    1|
|Crust iyi değil.|    0|

## <a name="build-your-machine-learning-model"></a>Machine Learning modelinizi oluşturma

1. Visual Studio 'Yu açın ve yeni bir C# konsol uygulaması (.NET Core) oluşturun. Projeyi *Mlmini model*olarak adlandırın.

1. **Çözüm Gezgini**, *mlmini model* projesine sağ tıklayın. **> Machine Learning Ekle**' yi seçin.

1. ML.NET model Oluşturucu ' dan **yaklaşım Analizi** senaryo kutucuğunu seçin.

1. **Veri Ekle** sayfasında *yelptrain.csv* veri kümesini karşıya yükleyin.

1. Açılır menüyü **tahmin etmek Için sütunlarda** yaklaşım ' *ı seçin.*

1. **Eğitme** sayfasında, *60 saniyeye* eğitme süresini ayarlayın ve **eğitimi Başlat**' ı seçin. **Ilerlemeniz**durumunda eğitimin durumunu fark edin.

1. Model Oluşturucu tamamlandıktan sonra eğitim sonuçlarını **değerlendirin** . Aşağıdaki metin kutusuna bir tümcecik yazarak **modelinizi deneyebilirsiniz** ve çıktıyı görmek için **tahmin** ' i seçin.

1. Çözüme ML modeli eklemek için **kodu** seçin ve **Proje Ekle** ' yi seçin.

1. Çözümlerinizi iki projenin eklendiğinden emin olun: **Mlmini Modelml. ConsoleApp** ve **Mlmini Modelml. model**.

1. *Mlspark* C# projenize çift tıklayın ve aşağıdaki proje başvurusunun eklendiğinden emin olun.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Konsol uygulaması oluşturma

Model Oluşturucu sizin için bir konsol uygulaması oluşturur.

1. Çözüm Gezgini 'de **Mlmini Modelml. Console** ' a sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.

1. **Microsoft. Spark** araması yapın ve paketini yükledikten sonra. **Microsoft.ml** , model Oluşturucu tarafından sizin için otomatik olarak yüklenir.

### <a name="create-a-sparksession"></a>Mini oturum oluşturma

1. **Mlmini Modelml. ConsoleApp**için *program.cs* dosyasını açın. Bu dosya model Oluşturucu tarafından otomatik olarak oluşturuldu. `using`Deyimlerini, Main () yönteminin içeriğini ve `CreateSingleDataSample` bölgesini silin.

1. Aşağıdaki ek `using` deyimlerini *program.cs*üst kısmına ekleyin:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Öğesini `DATA_FILEPATH` *yelptest.csv*yolu olarak değiştirin.

1. `Main`Yeni bir oluşturma yöntemine aşağıdaki kodu ekleyin `SparkSession` . Spark oturumu, veri kümesi ve DataFrame API 'SI ile Spark programlamanın giriş noktasıdır.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Yukarıda oluşturulan *Spark* nesnesini çağırmak, programınızın tamamında Spark ve dataframe işlevlerine erişmenize olanak tanır.

### <a name="create-a-dataframe-and-print-to-console"></a>Veri çerçevesi oluşturma ve konsola yazdırma

*yelptest.csv* dosyasındaki sarıp İnceleme verilerini bir olarak okuyun `DataFrame` . Dahil etme `header` ve `inferSchema` seçenekleri. `header`Seçeneği, *yelptest.csv* ilk satırını veri yerine sütun adı olarak okur. Bu `inferSchema` seçenek, verileri temel alan sütun türlerini anlar.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Kullanıcı tanımlı bir işlevi kaydetme

Verileriniz üzerinde hesaplamalar ve analiz yapmak için Spark uygulamalarında Kullanıcı tanımlı UDF 'ler, *Kullanıcı tanımlı işlevler*' i kullanabilirsiniz. Bu öğreticide, her bir Yelp incelemesini değerlendirmek için ML.NET ile bir UDF kullanırsınız.

`Main`Adlı BIR UDF 'yi kaydetmek için aşağıdaki kodu yöntemine ekleyin `MLudf` .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Bu UDF, giriş olarak bir sarıp İnceleme dizesi alır ve sırasıyla pozitif veya olumsuz yaklaşım için doğru ya da yanlış çıkışları olur. Daha sonraki bir adımda tanımladığınız *tahmin ()* yöntemini kullanır.

### <a name="use-spark-sql-to-call-the-udf"></a>UDF 'yi çağırmak için Spark SQL kullanma

Verileriniz ve birleştirilmiş ML 'yi okudığınıza göre, veri Çerçevinizdeki her bir satırda yaklaşım analizini çalıştıracak UDF 'yi çağırmak için Spark SQL kullanın. Aşağıdaki kodu yönteminizin içine ekleyin `Main` :

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a>Tahmin () yöntemi oluştur

Aşağıdaki kodu yönteminizin önüne ekleyin `Main()` . Bu kod, *ConsumeModel.cs*Içinde model Oluşturucu tarafından üretilme benzer. Bu yöntemin konsoluna taşınması, uygulamanızı her çalıştırışınızda model yüklemeyi yükler.

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a>Modeli konsol uygulamanıza ekleyin

Çözüm Gezgini, *MLModel.zip* dosyasını **mlmini Modelml. model** projesinden kopyalayın ve **Mlmini modelml. consoleapp** projesine yapıştırın. *Mlmini Modelml. ConsoleApp. csproj*öğesine bir başvuru otomatik olarak eklenir.

## <a name="run-your-code"></a>Kodunuzu çalıştırın

`spark-submit`Kodunuzu çalıştırmak için kullanın. Komut istemi 'ni kullanarak konsol uygulamanızın kök klasörüne gidin ve aşağıdaki komutları çalıştırın.

İlk olarak, uygulamanızı temizleyin ve yayımlayın.

```dotnetcli
dotnet clean
dotnet publish
```

Ardından konsol uygulamasının Yayımla klasörüne gidin ve aşağıdaki `spark-submit` komutu çalıştırın. Komutu, Microsoft Spark jar dosyanızın gerçek yoluyla güncelleştirmeyi unutmayın.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Kodu alma

Bu öğretici, [büyük veri örneği ile yaklaşım Analizi](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) kodla benzerdir.

## <a name="next-steps"></a>Sonraki adımlar

Apache Spark için .NET ile yapısal akış yapmayı öğrenmek için sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici: Apache Spark için .NET ile yapılandırılmış akış](streaming.md)
