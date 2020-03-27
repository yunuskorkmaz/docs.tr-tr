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
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="f6324-103">Öğretici: Apache Spark ve ML.NET için .NET ile duyarlılık analizi</span><span class="sxs-lookup"><span data-stu-id="f6324-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="f6324-104">Bu öğretici, Apache Spark için ML.NET ve .NET kullanarak çevrimiçi değerlendirmelerin duyarlılık analizini nasıl yapacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="f6324-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="f6324-105">[ML.NET](http://dot.net/ml) ücretsiz, çapraz platform, açık kaynak makine öğrenme çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="f6324-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="f6324-106">Makine öğrenimi algoritmalarının eğitimini ve tahminini ölçeklendirmek için Apache Spark için .NET ile ML.NET kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6324-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="f6324-107">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f6324-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="f6324-108">Visual Studio'da model oluşturucu ML.NET kullanarak bir duygu analizi modeli oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6324-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="f6324-109">Apache Spark konsol uygulaması için bir .NET oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6324-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="f6324-110">Kullanıcı tanımlı bir işlev yazın ve uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f6324-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="f6324-111">Apache Spark konsol uygulaması için bir .NET çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f6324-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6324-112">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="f6324-112">Prerequisites</span></span>

* <span data-ttu-id="f6324-113">Daha önce Apache Spark uygulaması için bir .NET geliştirmediyseniz, temel bilgileri tanımak için [Başlangıç öğreticisiyle](get-started.md) başlayın.</span><span class="sxs-lookup"><span data-stu-id="f6324-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="f6324-114">Bu öğretici ile devam etmeden önce Başlarken öğretici için tüm ön koşulları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="f6324-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="f6324-115">Bu öğretici, Visual Studio'da bulunan görsel bir arayüz olan ML.NET Model Builder (önizleme) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6324-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="f6324-116">Visual Studio'nuz yoksa Visual [Studio'nun Topluluk sürümünü](https://visualstudio.microsoft.com/downloads/) ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6324-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="f6324-117">[İndirin ve yükle](https://marketplace.visualstudio.com/items?itemName=MLNET.07) model oluşturucu (önizleme) ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f6324-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="f6324-118">[Yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) ve [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp inceleme veri kümelerini indirin.</span><span class="sxs-lookup"><span data-stu-id="f6324-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="f6324-119">Verileri gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="f6324-119">Review the data</span></span>

<span data-ttu-id="f6324-120">Yelp yorumları dataset çeşitli hizmetler hakkında çevrimiçi Yelp değerlendirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f6324-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="f6324-121">[Yelptrain.csv'yi](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) açın ve verilerin yapısına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f6324-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="f6324-122">İlk sütun gözden geçirme metni, ikinci sütun ise duyarlılık puanları içerir.</span><span class="sxs-lookup"><span data-stu-id="f6324-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="f6324-123">Duyarlılık puanı 1 ise, inceleme olumlu ve duygu puanı 0 ise, inceleme negatiftir.</span><span class="sxs-lookup"><span data-stu-id="f6324-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="f6324-124">Aşağıdaki tablo örnek verileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f6324-124">The following table contains sample data:</span></span>

|<span data-ttu-id="f6324-125">İnceleme Metni</span><span class="sxs-lookup"><span data-stu-id="f6324-125">ReviewText</span></span>|<span data-ttu-id="f6324-126">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="f6324-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="f6324-127">Wow... Burayı çok severdim.</span><span class="sxs-lookup"><span data-stu-id="f6324-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="f6324-128">1</span><span class="sxs-lookup"><span data-stu-id="f6324-128">1</span></span>|
|<span data-ttu-id="f6324-129">Kabuk iyi değil.</span><span class="sxs-lookup"><span data-stu-id="f6324-129">Crust is not good.</span></span>|    <span data-ttu-id="f6324-130">0</span><span class="sxs-lookup"><span data-stu-id="f6324-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="f6324-131">Makine öğrenimi modelinizi oluşturun</span><span class="sxs-lookup"><span data-stu-id="f6324-131">Build your machine learning model</span></span>

1. <span data-ttu-id="f6324-132">Visual Studio'u açın ve yeni bir C# Console App (.NET Core) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6324-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="f6324-133">Proje *MLSparkModel*adı.</span><span class="sxs-lookup"><span data-stu-id="f6324-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="f6324-134">**Solution Explorer'da** *MLSparkModel* projesini sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f6324-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="f6324-135">Sonra **> Makine Öğrenme ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="f6324-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="f6324-136">model oluşturucuML.NET, **Duygu Analizi** senaryo döşemesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f6324-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="f6324-137">Veri **ekle** sayfasında *yelptrain.csv* veri kümesini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f6324-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="f6324-138">Açılır düşüşü **tahmin etmek için Sütunlardan** *Duygu'yu* seçin.</span><span class="sxs-lookup"><span data-stu-id="f6324-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="f6324-139">**Tren** sayfasında, *60 saniyeye* kadar eğitim için zaman ayarlayın ve **eğitime başlat'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="f6324-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="f6324-140">İlerleme altında eğitim durumunuza dikkat **edin.**</span><span class="sxs-lookup"><span data-stu-id="f6324-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="f6324-141">Model Oluşturucu eğitimini tamamladıktan sonra, eğitim sonuçlarını **değerlendirin.**</span><span class="sxs-lookup"><span data-stu-id="f6324-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="f6324-142">Aşağıdaki metin kutusuna tümcecikler yazabilir ve **çıktıyı** görmek için **Tahmin** et'i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6324-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="f6324-143">**Kod'u** seçin ve ardından çözüme ML modelini eklemek için **Projeler Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="f6324-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="f6324-144">Çözümlerinize iki proje eklendidikkat: **MLSparkModelML.ConsoleApp** ve **MLSparkModelML.Model**.</span><span class="sxs-lookup"><span data-stu-id="f6324-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="f6324-145">*MLSpark* C# projenize çift tıklayın ve aşağıdaki proje referansına eklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f6324-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="f6324-146">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6324-146">Create a console app</span></span>

<span data-ttu-id="f6324-147">Model Oluşturucu sizin için bir konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f6324-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="f6324-148">Solution Explorer'da **MLSparkModelML.Console'a** sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="f6324-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="f6324-149">**Microsoft.Spark'ı** arayın ve paketi yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f6324-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="f6324-150">**Microsoft.ML,** Model Builder tarafından sizin için otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f6324-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="f6324-151">Bir SparkSession oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6324-151">Create a SparkSession</span></span>

1. <span data-ttu-id="f6324-152">**MLSparkModelML.ConsoleApp**için *Program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f6324-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="f6324-153">Bu dosya Model Oluşturucu tarafından otomatik olarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="f6324-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="f6324-154">`using` İfadeleri, Main() yönteminin içeriğini ve `CreateSingleDataSample` bölgeyi silin.</span><span class="sxs-lookup"><span data-stu-id="f6324-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="f6324-155">Program.cs üst `using` kısmında aşağıdaki ek *Program.cs*ifadeler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6324-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="f6324-156">`DATA_FILEPATH` *Yelptest.csv'nizin*yolunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f6324-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="f6324-157">`Main` Yeni `SparkSession`bir .</span><span class="sxs-lookup"><span data-stu-id="f6324-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="f6324-158">Kıvılcım Oturumu, Dataset ve DataFrame API ile Spark programlamanın giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="f6324-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="f6324-159">Yukarıda oluşturulan *kıvılcım* nesnesini aramak, programınız boyunca Spark ve DataFrame işlevlerine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6324-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="f6324-160">Bir DataFrame oluşturma ve konsola yazdırma</span><span class="sxs-lookup"><span data-stu-id="f6324-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="f6324-161">*Yelptest.csv* dosyasından Yelp inceleme verilerini bir `DataFrame`olarak okuyun.</span><span class="sxs-lookup"><span data-stu-id="f6324-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="f6324-162">Dahil `header` `inferSchema` et ve seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="f6324-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="f6324-163">Seçenek, `header` *yelptest.csv'nin* ilk satırını veri yerine sütun adları olarak okur.</span><span class="sxs-lookup"><span data-stu-id="f6324-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="f6324-164">Seçenek, `inferSchema` verilere göre sütun türlerini çıkartıyor.</span><span class="sxs-lookup"><span data-stu-id="f6324-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="f6324-165">Kullanıcı tanımlı bir işlev kaydetme</span><span class="sxs-lookup"><span data-stu-id="f6324-165">Register a user-defined function</span></span>

<span data-ttu-id="f6324-166">Verilerinizde hesaplamalar ve analizler yapmak için Spark uygulamalarında UDF'leri, *kullanıcı tanımlı işlevleri*kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6324-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="f6324-167">Bu eğitimde, her Yelp incelemesini değerlendirmek için UDF ile ML.NET kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f6324-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="f6324-168">Bir UDF'yi `Main` `MLudf`kaydetmek için yönteminize aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6324-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="f6324-169">Bu UDF, giriş olarak yelp inceleme dizesi alır ve sırasıyla olumlu veya olumsuz duygular için doğru veya yanlış çıktıları alır.</span><span class="sxs-lookup"><span data-stu-id="f6324-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="f6324-170">Daha sonraki bir adımda tanımladığınız *predict()* yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6324-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="f6324-171">UDF'yi aramak için Spark SQL'i kullanın</span><span class="sxs-lookup"><span data-stu-id="f6324-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="f6324-172">Verilerinizde okuduğunuza ve ML'yi bünyesine kattığınızda, DataFrame'inizin her satırında duyarlılık analizi çalıştıracak UDF'yi aramak için Spark SQL'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="f6324-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="f6324-173">Yönteminize `Main` aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f6324-173">Add the following code to your `Main` method:</span></span>

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

### <a name="create-predict-method"></a><span data-ttu-id="f6324-174">Predict() yöntemi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6324-174">Create predict() method</span></span>

<span data-ttu-id="f6324-175">Yöntemden `Main()` önce aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6324-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="f6324-176">Bu *kod, model*oluşturucu tarafından ConsumeModel.cs'da üretilen ekine benzer.</span><span class="sxs-lookup"><span data-stu-id="f6324-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="f6324-177">Bu yöntemi konsolunuza taşımak, uygulamanızı her çalıştırdığınızda model yüklemesini yükler.</span><span class="sxs-lookup"><span data-stu-id="f6324-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

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

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="f6324-178">Modeli konsol uygulamanıza ekleme</span><span class="sxs-lookup"><span data-stu-id="f6324-178">Add the model to your console app</span></span>

<span data-ttu-id="f6324-179">Solution Explorer'da **MLSparkModelML.Model** projesinden *MLModel.zip* dosyasını kopyalayın ve **MLSparkModelML.ConsoleApp** projesine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="f6324-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="f6324-180">*MlSparkModelML.ConsoleApp.csproj'a*otomatik olarak bir başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="f6324-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="f6324-181">Kodunuzu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f6324-181">Run your code</span></span>

<span data-ttu-id="f6324-182">Kodunuzu çalıştırmak için kullanın. `spark-submit`</span><span class="sxs-lookup"><span data-stu-id="f6324-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="f6324-183">Komut istemini kullanarak konsol uygulamanızın kök klasörüne gidin ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f6324-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="f6324-184">İlk olarak, uygulamanızı temizleyin ve yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="f6324-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="f6324-185">Ardından konsol uygulamasının yayımlama klasörüne gidin `spark-submit` ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f6324-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="f6324-186">Komutu Microsoft Spark jar dosyanızın gerçek yolu ile güncelleştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f6324-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="f6324-187">Kodu alma</span><span class="sxs-lookup"><span data-stu-id="f6324-187">Get the code</span></span>

<span data-ttu-id="f6324-188">Bu öğretici, Büyük Veri örneği [ile Duyarlılık Analizi](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) koduna benzer.</span><span class="sxs-lookup"><span data-stu-id="f6324-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f6324-189">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f6324-189">Next steps</span></span>

<span data-ttu-id="f6324-190">Apache Spark için .NET ile Yapılandırılmış Akış'ın nasıl yapılacağını öğrenmek için bir sonraki makaleye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="f6324-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f6324-191">Öğretici: Apache Spark için .NET ile Yapılandırılmış Akış</span><span class="sxs-lookup"><span data-stu-id="f6324-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
