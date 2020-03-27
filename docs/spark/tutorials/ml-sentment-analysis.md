---
title: Apache Spark ve ML.NET öğretici için .NET ile duyarlılık analizi
description: Bu eğitimde, duygu analizi için Apache Spark için .NET ile ML.NET kullanmayı öğreneceksiniz.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345343"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Öğretici: Apache Spark ve ML.NET için .NET ile duyarlılık analizi

Bu öğretici, Apache Spark için ML.NET ve .NET kullanarak çevrimiçi değerlendirmelerin duyarlılık analizini nasıl yapacağınızı öğretir. [ML.NET](http://dot.net/ml) ücretsiz, çapraz platform, açık kaynak makine öğrenme çerçevesidir. Makine öğrenimi algoritmalarının eğitimini ve tahminini ölçeklendirmek için Apache Spark için .NET ile ML.NET kullanabilirsiniz.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> * Visual Studio'da model oluşturucu ML.NET kullanarak bir duygu analizi modeli oluşturun.
> * Apache Spark konsol uygulaması için bir .NET oluşturun.
> * Kullanıcı tanımlı bir işlev yazın ve uygulayın.
> * Apache Spark konsol uygulaması için bir .NET çalıştırın.

## <a name="prerequisites"></a>Ön koşullar

* Daha önce Apache Spark uygulaması için bir .NET geliştirmediyseniz, temel bilgileri tanımak için [Başlangıç öğreticisiyle](get-started.md) başlayın. Bu öğretici ile devam etmeden önce Başlarken öğretici için tüm ön koşulları tamamlayın.

* Bu öğretici, Visual Studio'da bulunan görsel bir arayüz olan ML.NET Model Builder (önizleme) kullanır. Visual Studio'nuz yoksa Visual [Studio'nun Topluluk sürümünü](https://visualstudio.microsoft.com/downloads/) ücretsiz olarak indirebilirsiniz.

* [İndirin ve yükle](https://marketplace.visualstudio.com/items?itemName=MLNET.07) model oluşturucu (önizleme) ML.NET.

* [Yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) ve [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp inceleme veri kümelerini indirin.

## <a name="review-the-data"></a>Verileri gözden geçirme

Yelp yorumları dataset çeşitli hizmetler hakkında çevrimiçi Yelp değerlendirmeleri içerir. [Yelptrain.csv'yi](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) açın ve verilerin yapısına dikkat edin. İlk sütun gözden geçirme metni, ikinci sütun ise duyarlılık puanları içerir. Duyarlılık puanı 1 ise, inceleme olumlu ve duygu puanı 0 ise, inceleme negatiftir.

Aşağıdaki tablo örnek verileri içerir:

|İnceleme Metni|Yaklaşım|
|-|-|
|Wow... Burayı çok severdim.|    1|
|Kabuk iyi değil.|    0|

## <a name="build-your-machine-learning-model"></a>Makine öğrenimi modelinizi oluşturun

1. Visual Studio'u açın ve yeni bir C# Console App (.NET Core) oluşturun. Proje *MLSparkModel*adı.

1. **Solution Explorer'da** *MLSparkModel* projesini sağ tıklatın. Sonra **> Makine Öğrenme ekle'yi**seçin.

1. model oluşturucuML.NET, **Duygu Analizi** senaryo döşemesini seçin.

1. Veri **ekle** sayfasında *yelptrain.csv* veri kümesini yükleyin.

1. Açılır düşüşü **tahmin etmek için Sütunlardan** *Duygu'yu* seçin.

1. **Tren** sayfasında, *60 saniyeye* kadar eğitim için zaman ayarlayın ve **eğitime başlat'ı**seçin. İlerleme altında eğitim durumunuza dikkat **edin.**

1. Model Oluşturucu eğitimini tamamladıktan sonra, eğitim sonuçlarını **değerlendirin.** Aşağıdaki metin kutusuna tümcecikler yazabilir ve **çıktıyı** görmek için **Tahmin** et'i seçebilirsiniz.

1. **Kod'u** seçin ve ardından çözüme ML modelini eklemek için **Projeler Ekle'yi** seçin.

1. Çözümlerinize iki proje eklendidikkat: **MLSparkModelML.ConsoleApp** ve **MLSparkModelML.Model**.

1. *MLSpark* C# projenize çift tıklayın ve aşağıdaki proje referansına eklendiğini unutmayın.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Konsol uygulaması oluşturma

Model Oluşturucu sizin için bir konsol uygulaması oluşturur.

1. Solution Explorer'da **MLSparkModelML.Console'a** sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.

1. **Microsoft.Spark'ı** arayın ve paketi yükleyin. **Microsoft.ML,** Model Builder tarafından sizin için otomatik olarak yüklenir.

### <a name="create-a-sparksession"></a>Bir SparkSession oluşturma

1. **MLSparkModelML.ConsoleApp**için *Program.cs* dosyasını açın. Bu dosya Model Oluşturucu tarafından otomatik olarak oluşturuldu. `using` İfadeleri, Main() yönteminin içeriğini ve `CreateSingleDataSample` bölgeyi silin.

1. Program.cs üst `using` kısmında aşağıdaki ek *Program.cs*ifadeler ekleyin:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. `DATA_FILEPATH` *Yelptest.csv'nizin*yolunu değiştirin.

1. `Main` Yeni `SparkSession`bir . Kıvılcım Oturumu, Dataset ve DataFrame API ile Spark programlamanın giriş noktasıdır.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   Yukarıda oluşturulan *kıvılcım* nesnesini aramak, programınız boyunca Spark ve DataFrame işlevlerine erişmenizi sağlar.

### <a name="create-a-dataframe-and-print-to-console"></a>Bir DataFrame oluşturma ve konsola yazdırma

*Yelptest.csv* dosyasından Yelp inceleme verilerini bir `DataFrame`olarak okuyun. Dahil `header` `inferSchema` et ve seçenekleri. Seçenek, `header` *yelptest.csv'nin* ilk satırını veri yerine sütun adları olarak okur. Seçenek, `inferSchema` verilere göre sütun türlerini çıkartıyor.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Kullanıcı tanımlı bir işlev kaydetme

Verilerinizde hesaplamalar ve analizler yapmak için Spark uygulamalarında UDF'leri, *kullanıcı tanımlı işlevleri*kullanabilirsiniz. Bu eğitimde, her Yelp incelemesini değerlendirmek için UDF ile ML.NET kullanırsınız.

Bir UDF'yi `Main` `MLudf`kaydetmek için yönteminize aşağıdaki kodu ekleyin.

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Bu UDF, giriş olarak yelp inceleme dizesi alır ve sırasıyla olumlu veya olumsuz duygular için doğru veya yanlış çıktıları alır. Daha sonraki bir adımda tanımladığınız *predict()* yöntemini kullanır.

### <a name="use-spark-sql-to-call-the-udf"></a>UDF'yi aramak için Spark SQL'i kullanın

Verilerinizde okuduğunuza ve ML'yi bünyesine kattığınızda, DataFrame'inizin her satırında duyarlılık analizi çalıştıracak UDF'yi aramak için Spark SQL'i kullanın. Yönteminize `Main` aşağıdaki kodu ekleyin:

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

### <a name="create-predict-method"></a>Predict() yöntemi oluşturma

Yöntemden `Main()` önce aşağıdaki kodu ekleyin. Bu *kod, model*oluşturucu tarafından ConsumeModel.cs'da üretilen ekine benzer. Bu yöntemi konsolunuza taşımak, uygulamanızı her çalıştırdığınızda model yüklemesini yükler.

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

## <a name="add-the-model-to-your-console-app"></a>Modeli konsol uygulamanıza ekleme

Solution Explorer'da **MLSparkModelML.Model** projesinden *MLModel.zip* dosyasını kopyalayın ve **MLSparkModelML.ConsoleApp** projesine yapıştırın. *MlSparkModelML.ConsoleApp.csproj'a*otomatik olarak bir başvuru eklenir.

## <a name="run-your-code"></a>Kodunuzu çalıştırın

Kodunuzu çalıştırmak için kullanın. `spark-submit` Komut istemini kullanarak konsol uygulamanızın kök klasörüne gidin ve aşağıdaki komutları çalıştırın.

İlk olarak, uygulamanızı temizleyin ve yayınlayın.

```dotnetcli
dotnet clean
dotnet publish
```

Ardından konsol uygulamasının yayımlama klasörüne gidin `spark-submit` ve aşağıdaki komutu çalıştırın. Komutu Microsoft Spark jar dosyanızın gerçek yolu ile güncelleştirmeyi unutmayın.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Kodu alma

Bu öğretici, Büyük Veri örneği [ile Duyarlılık Analizi](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) koduna benzer.

## <a name="next-steps"></a>Sonraki adımlar

Apache Spark için .NET ile Yapılandırılmış Akış'ın nasıl yapılacağını öğrenmek için bir sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici: Apache Spark için .NET ile Yapılandırılmış Akış](streaming.md)
