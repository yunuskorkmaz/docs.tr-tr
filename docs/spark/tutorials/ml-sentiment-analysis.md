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
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="9d2b2-103">Öğretici: Apache Spark ve ML.NET için .NET ile yaklaşım Analizi</span><span class="sxs-lookup"><span data-stu-id="9d2b2-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="9d2b2-104">Bu öğretici, Apache Spark için ML.NET ve .NET kullanarak çevrimiçi incelemelere ilişkin yaklaşım analizinin nasıl yapılacağını öğretir.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="9d2b2-105">[Ml.net](http://dot.net/ml) , ücretsiz, platformlar arası, açık kaynaklı bir makine öğrenimi çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="9d2b2-106">Makine öğrenimi algoritmalarının eğitimini ve tahminini ölçeklendirmek için Apache Spark .NET ile ML.NET kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="9d2b2-107">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="9d2b2-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="9d2b2-108">Visual Studio 'da ML.NET model Oluşturucu kullanarak bir yaklaşım analiz modeli oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="9d2b2-109">Apache Spark konsol uygulaması için bir .NET oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="9d2b2-110">Kullanıcı tanımlı bir işlevi yazın ve uygulayın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="9d2b2-111">Apache Spark konsol uygulaması için bir .NET çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-111">Run a .NET for Apache Spark console app.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="9d2b2-112">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="9d2b2-112">Prerequisites</span></span>

* <span data-ttu-id="9d2b2-113">Daha önce Apache Spark uygulama için bir .NET geliştirmediyse, temel bilgileri öğrenecek başlangıç [öğreticisiyle](get-started.md) başlayın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="9d2b2-114">Bu öğreticiye devam etmeden önce başlangıç öğreticisine yönelik tüm önkoşulları doldurun.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="9d2b2-115">Bu öğretici, Visual Studio 'da kullanılabilen bir görsel arabirim olan ML.NET model oluşturucusunu (Önizleme) kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="9d2b2-116">Zaten Visual Studio yoksa, [Visual Studio 'Nun topluluk sürümünü](https://visualstudio.microsoft.com/downloads/) ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="9d2b2-117">[İndir ve yükle](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET model Oluşturucu (Önizleme).</span><span class="sxs-lookup"><span data-stu-id="9d2b2-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="9d2b2-118">[yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) indirin ve sarıp İnceleme veri kümelerini [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) .</span><span class="sxs-lookup"><span data-stu-id="9d2b2-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="9d2b2-119">Verileri gözden geçirin</span><span class="sxs-lookup"><span data-stu-id="9d2b2-119">Review the data</span></span>

<span data-ttu-id="9d2b2-120">Yelp İnceleme veri kümesi çeşitli hizmetlerle ilgili çevrimiçi sarık İncelemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="9d2b2-121">[yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) açın ve verilerin yapısına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="9d2b2-122">İlk sütunda İnceleme metni bulunur ve ikinci sütun, yaklaşım puanlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="9d2b2-123">Yaklaşım puanı 1 ise, gözden geçirme pozitif olur ve yaklaşım puanı 0 ise, gözden geçirme negatif olur.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="9d2b2-124">Aşağıdaki tabloda örnek veriler yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="9d2b2-124">The following table contains sample data:</span></span>

|<span data-ttu-id="9d2b2-125">Belgemetinmetni</span><span class="sxs-lookup"><span data-stu-id="9d2b2-125">ReviewText</span></span>|<span data-ttu-id="9d2b2-126">Yaklaşım</span><span class="sxs-lookup"><span data-stu-id="9d2b2-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="9d2b2-127">Wow... Bu yere iner.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="9d2b2-128">1</span><span class="sxs-lookup"><span data-stu-id="9d2b2-128">1</span></span>|
|<span data-ttu-id="9d2b2-129">Crust iyi değil.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-129">Crust is not good.</span></span>|    <span data-ttu-id="9d2b2-130">0</span><span class="sxs-lookup"><span data-stu-id="9d2b2-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="9d2b2-131">Machine Learning modelinizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d2b2-131">Build your machine learning model</span></span>

1. <span data-ttu-id="9d2b2-132">Visual Studio 'Yu açın ve yeni bir C# konsol uygulaması (.NET Core) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="9d2b2-133">Projeyi *Mlmini model*olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="9d2b2-134">**Çözüm Gezgini**, *mlmini model* projesine sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="9d2b2-135">**> Machine Learning Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="9d2b2-136">ML.NET model Oluşturucu ' dan **yaklaşım Analizi** senaryo kutucuğunu seçin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="9d2b2-137">**Veri Ekle** sayfasında *yelptrain.csv* veri kümesini karşıya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="9d2b2-138">Açılır menüyü **tahmin etmek Için sütunlarda** yaklaşım ' *ı seçin.*</span><span class="sxs-lookup"><span data-stu-id="9d2b2-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="9d2b2-139">**Eğitme** sayfasında, *60 saniyeye* eğitme süresini ayarlayın ve **eğitimi Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="9d2b2-140">**Ilerlemeniz**durumunda eğitimin durumunu fark edin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="9d2b2-141">Model Oluşturucu tamamlandıktan sonra eğitim sonuçlarını **değerlendirin** .</span><span class="sxs-lookup"><span data-stu-id="9d2b2-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="9d2b2-142">Aşağıdaki metin kutusuna bir tümcecik yazarak **modelinizi deneyebilirsiniz** ve çıktıyı görmek için **tahmin** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="9d2b2-143">Çözüme ML modeli eklemek için **kodu** seçin ve **Proje Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="9d2b2-144">Çözümlerinizi iki projenin eklendiğinden emin olun: **Mlmini Modelml. ConsoleApp** ve **Mlmini Modelml. model**.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="9d2b2-145">*Mlspark* C# projenize çift tıklayın ve aşağıdaki proje başvurusunun eklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="9d2b2-146">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d2b2-146">Create a console app</span></span>

<span data-ttu-id="9d2b2-147">Model Oluşturucu sizin için bir konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="9d2b2-148">Çözüm Gezgini 'de **Mlmini Modelml. Console** ' a sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="9d2b2-149">**Microsoft. Spark** araması yapın ve paketini yükledikten sonra.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="9d2b2-150">**Microsoft.ml** , model Oluşturucu tarafından sizin için otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="9d2b2-151">Mini oturum oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d2b2-151">Create a SparkSession</span></span>

1. <span data-ttu-id="9d2b2-152">**Mlmini Modelml. ConsoleApp**için *program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="9d2b2-153">Bu dosya model Oluşturucu tarafından otomatik olarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="9d2b2-154">`using`Deyimlerini, Main () yönteminin içeriğini ve `CreateSingleDataSample` bölgesini silin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="9d2b2-155">Aşağıdaki ek `using` deyimlerini *program.cs*üst kısmına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9d2b2-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="9d2b2-156">Öğesini `DATA_FILEPATH` *yelptest.csv*yolu olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="9d2b2-157">`Main`Yeni bir oluşturma yöntemine aşağıdaki kodu ekleyin `SparkSession` .</span><span class="sxs-lookup"><span data-stu-id="9d2b2-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="9d2b2-158">Spark oturumu, veri kümesi ve DataFrame API 'SI ile Spark programlamanın giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="9d2b2-159">Yukarıda oluşturulan *Spark* nesnesini çağırmak, programınızın tamamında Spark ve dataframe işlevlerine erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="9d2b2-160">Veri çerçevesi oluşturma ve konsola yazdırma</span><span class="sxs-lookup"><span data-stu-id="9d2b2-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="9d2b2-161">*yelptest.csv* dosyasındaki sarıp İnceleme verilerini bir olarak okuyun `DataFrame` .</span><span class="sxs-lookup"><span data-stu-id="9d2b2-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="9d2b2-162">Dahil etme `header` ve `inferSchema` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="9d2b2-163">`header`Seçeneği, *yelptest.csv* ilk satırını veri yerine sütun adı olarak okur.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="9d2b2-164">Bu `inferSchema` seçenek, verileri temel alan sütun türlerini anlar.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="9d2b2-165">Kullanıcı tanımlı bir işlevi kaydetme</span><span class="sxs-lookup"><span data-stu-id="9d2b2-165">Register a user-defined function</span></span>

<span data-ttu-id="9d2b2-166">Verileriniz üzerinde hesaplamalar ve analiz yapmak için Spark uygulamalarında Kullanıcı tanımlı UDF 'ler, *Kullanıcı tanımlı işlevler*' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="9d2b2-167">Bu öğreticide, her bir Yelp incelemesini değerlendirmek için ML.NET ile bir UDF kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="9d2b2-168">`Main`Adlı BIR UDF 'yi kaydetmek için aşağıdaki kodu yöntemine ekleyin `MLudf` .</span><span class="sxs-lookup"><span data-stu-id="9d2b2-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="9d2b2-169">Bu UDF, giriş olarak bir sarıp İnceleme dizesi alır ve sırasıyla pozitif veya olumsuz yaklaşım için doğru ya da yanlış çıkışları olur.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="9d2b2-170">Daha sonraki bir adımda tanımladığınız *tahmin ()* yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="9d2b2-171">UDF 'yi çağırmak için Spark SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="9d2b2-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="9d2b2-172">Verileriniz ve birleştirilmiş ML 'yi okudığınıza göre, veri Çerçevinizdeki her bir satırda yaklaşım analizini çalıştıracak UDF 'yi çağırmak için Spark SQL kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="9d2b2-173">Aşağıdaki kodu yönteminizin içine ekleyin `Main` :</span><span class="sxs-lookup"><span data-stu-id="9d2b2-173">Add the following code to your `Main` method:</span></span>

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

### <a name="create-predict-method"></a><span data-ttu-id="9d2b2-174">Tahmin () yöntemi oluştur</span><span class="sxs-lookup"><span data-stu-id="9d2b2-174">Create predict() method</span></span>

<span data-ttu-id="9d2b2-175">Aşağıdaki kodu yönteminizin önüne ekleyin `Main()` .</span><span class="sxs-lookup"><span data-stu-id="9d2b2-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="9d2b2-176">Bu kod, *ConsumeModel.cs*Içinde model Oluşturucu tarafından üretilme benzer.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="9d2b2-177">Bu yöntemin konsoluna taşınması, uygulamanızı her çalıştırışınızda model yüklemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

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

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="9d2b2-178">Modeli konsol uygulamanıza ekleyin</span><span class="sxs-lookup"><span data-stu-id="9d2b2-178">Add the model to your console app</span></span>

<span data-ttu-id="9d2b2-179">Çözüm Gezgini, *MLModel.zip* dosyasını **mlmini Modelml. model** projesinden kopyalayın ve **Mlmini modelml. consoleapp** projesine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="9d2b2-180">*Mlmini Modelml. ConsoleApp. csproj*öğesine bir başvuru otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="9d2b2-181">Kodunuzu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="9d2b2-181">Run your code</span></span>

<span data-ttu-id="9d2b2-182">`spark-submit`Kodunuzu çalıştırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="9d2b2-183">Komut istemi 'ni kullanarak konsol uygulamanızın kök klasörüne gidin ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="9d2b2-184">İlk olarak, uygulamanızı temizleyin ve yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="9d2b2-185">Ardından konsol uygulamasının Yayımla klasörüne gidin ve aşağıdaki `spark-submit` komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="9d2b2-186">Komutu, Microsoft Spark jar dosyanızın gerçek yoluyla güncelleştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="9d2b2-187">Kodu alma</span><span class="sxs-lookup"><span data-stu-id="9d2b2-187">Get the code</span></span>

<span data-ttu-id="9d2b2-188">Bu öğretici, [büyük veri örneği ile yaklaşım Analizi](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) kodla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9d2b2-189">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9d2b2-189">Next steps</span></span>

<span data-ttu-id="9d2b2-190">Apache Spark için .NET ile yapısal akış yapmayı öğrenmek için sonraki makaleye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9d2b2-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9d2b2-191">Öğretici: Apache Spark için .NET ile yapılandırılmış akış</span><span class="sxs-lookup"><span data-stu-id="9d2b2-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
