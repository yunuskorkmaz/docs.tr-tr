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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="a0533-103">Öğretici: Apache Spark için .NET ile toplu işleme yapın</span><span class="sxs-lookup"><span data-stu-id="a0533-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="a0533-104">Bu eğitimde, Apache Spark için .NET'i kullanarak toplu işleme yapmayı öğrenirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0533-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="a0533-105">Toplu işlem, veri lerin istirahat halindeki dönüşümüdür, yani kaynak veriler zaten veri depolamaya yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0533-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="a0533-106">Toplu işlem genellikle daha fazla analiz için hazırlanması gereken büyük, düz veri kümeleri üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a0533-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="a0533-107">Günlük işleme ve veri ambarı yaygın toplu işleme senaryolarıdır.</span><span class="sxs-lookup"><span data-stu-id="a0533-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="a0533-108">Bu senaryoda, farklı projelerin çatallandığı süre veya projelerin ne kadar yakın zamanda güncelleştirilmiş olduğu gibi GitHub projeleri hakkındaki bilgileri çözümlersiniz.</span><span class="sxs-lookup"><span data-stu-id="a0533-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="a0533-109">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0533-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a0533-110">Apache Spark uygulaması için bir .NET oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a0533-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="a0533-111">Verileri DataFrame'e okuyun ve analize hazırlayın</span><span class="sxs-lookup"><span data-stu-id="a0533-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="a0533-112">Spark SQL kullanarak verileri işleme</span><span class="sxs-lookup"><span data-stu-id="a0533-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0533-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a0533-113">Prerequisites</span></span>

<span data-ttu-id="a0533-114">Apache Spark için .NET'i ilk kez kullanıyorsanız, ortamınızı nasıl hazırlayacağınızı öğrenmek ve Apache Spark uygulaması için ilk .NET'inizi çalıştırmak [için Apache Spark öğreticisi için .NET ile başlayın'a](../tutorials/get-started.md) göz atın.</span><span class="sxs-lookup"><span data-stu-id="a0533-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="a0533-115">Örnek verileri indirme</span><span class="sxs-lookup"><span data-stu-id="a0533-115">Download the sample data</span></span>

<span data-ttu-id="a0533-116">[GHTorrent,](http://ghtorrent.org/) projeler, taahhütler ve izleyiciler hakkında bilgi gibi tüm herkese açık GitHub olaylarını izler ve olayları ve yapılarını veritabanlarında saklar.</span><span class="sxs-lookup"><span data-stu-id="a0533-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="a0533-117">Farklı zaman dilimlerinde toplanan veriler indirilebilir arşivler olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0533-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="a0533-118">Döküm dosyaları çok büyük olduğundan, bu kılavuz, GitHub'dan indirilebilen [döküm dosyasının kesilmiş bir sürümünü](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0533-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="a0533-119">GHTorrent veri seti çift lisans programı[(Creative Commons + )](https://wiki.creativecommons.org/wiki/CCPlus)altında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="a0533-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="a0533-120">Ticari olmayan kullanımlar için (eğitim, araştırma veya kişisel kullanımlar dahil ancak bunlarla sınırlı olmamak üzere), veri kümesi [CC-BY-SA lisansı](https://creativecommons.org/licenses/by-sa/4.0/)altında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="a0533-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a0533-121">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0533-121">Create a console application</span></span>

1. <span data-ttu-id="a0533-122">Komut isteminizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a0533-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="a0533-123">Komut `dotnet` sizin için `new` bir `console` tür uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0533-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="a0533-124">Parametre, `-o` uygulamanızın depolandığı *mySparkBatchApp* adında bir dizin oluşturur ve gerekli dosyalarla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a0533-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="a0533-125">Komut, `cd mySparkBatchApp` dizini yeni oluşturduğunuz uygulama dizinine değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a0533-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="a0533-126">Bir uygulamada Apache Spark için .NET'i kullanmak için Microsoft.Spark paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a0533-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="a0533-127">Konsolunuzda aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a0533-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="a0533-128">Bir SparkSession oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0533-128">Create a SparkSession</span></span>

1. <span data-ttu-id="a0533-129">aşağıdaki ek `using` ifadeleri *mySparkBatchApp'taki* *Program.cs* dosyasının üst bölümüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0533-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="a0533-130">Proje ad alanınıza aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0533-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="a0533-131">*s_referenceData* daha sonra programda tarihe göre filtrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0533-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="a0533-132">Yeni bir SparkSession oluşturmak için Ana yönteminizin içine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0533-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="a0533-133">SparkSession, Dataset ve DataFrame API ile Spark programlamanın giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="a0533-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="a0533-134">Nesneyi `spark` arayarak, programınız boyunca Spark ve DataFrame işlevlerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0533-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="a0533-135">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="a0533-135">Prepare the data</span></span>

1. <span data-ttu-id="a0533-136">Giriş `DataFrame`dosyasını, adlandırılmış sütunlara düzenlenen dağıtılmış veri koleksiyonu na göre okuyun.</span><span class="sxs-lookup"><span data-stu-id="a0533-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="a0533-137">Verileriniz için sütunları <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>' dan ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0533-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="a0533-138">Verileri <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> DataFrame'inizde görüntülemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0533-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="a0533-139">CSV dosya yolunu indirdiğiniz GitHub verilerinin konumuna güncelleştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a0533-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="a0533-140">NA <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> (null) değerleriyle satırları düşürmek için <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> yöntemi ve verilerinizden belirli sütunları kaldırma yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0533-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="a0533-141">Bu, son çözümlemenizde alakalı olmayan boş verileri veya sütunları çözümlemeye çalışırsanız hataları önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a0533-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="a0533-142">Verileri analiz edin</span><span class="sxs-lookup"><span data-stu-id="a0533-142">Analyze the data</span></span>

<span data-ttu-id="a0533-143">Spark SQL, verilerinizde SQL aramaları yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0533-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="a0533-144">DataFrame'inizin tüm satırlarına kullanıcı tanımlı bir işlev uygulamak için kullanıcı tanımlı işlevleri ve Spark SQL'i birleştirmek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="a0533-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="a0533-145">Özellikle diğer `spark.Sql` uygulama türlerinde görülen standart SQL çağrılarını taklit etmek için arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0533-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="a0533-146">Ayrıca, verilerinizdeki <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> hesaplamaları birleştirmek, filtrelemek ve gerçekleştirmek gibi yöntemleri de çağırabilir ve <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> özel olarak arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0533-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="a0533-147">Bu uygulamanın amacı GitHub projeleri verileri hakkında bazı bilgiler elde etmektir.</span><span class="sxs-lookup"><span data-stu-id="a0533-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="a0533-148">Verileri analiz etmek için programınıza aşağıdaki kod parçacıklarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0533-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="a0533-149">Aşağıdaki kod bloğunu ekleyin, her dilin çatallı sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="a0533-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="a0533-150">İlk olarak, veriler dile göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="a0533-150">First, the data is grouped by language.</span></span> <span data-ttu-id="a0533-151">Daha sonra, her dilden ortalama çatal sayısı alınır.</span><span class="sxs-lookup"><span data-stu-id="a0533-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="a0533-152">Hangi dillerin en çok çatallı olduğunu görmek için azalan sırada ortalama çatal sayısını sipariş etmek için aşağıdaki kod bloğunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a0533-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="a0533-153">Diğer bir tarihte, önce en fazla sayıda çatal görünür.</span><span class="sxs-lookup"><span data-stu-id="a0533-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="a0533-154">Bir sonraki kod bloğu, projelerin ne kadar yakın zamanda güncelleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0533-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="a0533-155">*MyUDF* adlı yeni bir kullanıcı tanımlı işlevi kaydeder ve öğreticinin başında bildirilen bir tarih, *s_referenceDate*ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="a0533-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="a0533-156">Her projenin tarihi başvuru tarihiyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="a0533-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="a0533-157">Daha sonra, Spark SQL veri kümesindeki her projeyi çözümlemek için verilerin her satırında UDF çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0533-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="a0533-158">SparkSession'ı sona erdirmek için arayın. `spark.Stop()`</span><span class="sxs-lookup"><span data-stu-id="a0533-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="a0533-159">Uygulamanızı çalıştırmak için kıvılcım gönder'i kullanma</span><span class="sxs-lookup"><span data-stu-id="a0533-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="a0533-160">.NET uygulamanızı oluşturmak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a0533-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="a0533-161">Uygulamanızı ' `spark-submit`ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a0533-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="a0533-162">Microsoft Spark jar dosyanıza giden gerçek yollarla aşağıdaki komutu güncelleştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a0533-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="a0533-163">Kodu alma</span><span class="sxs-lookup"><span data-stu-id="a0533-163">Get the code</span></span>

<span data-ttu-id="a0533-164">Tüm [çözümü](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) GitHub'da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0533-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a0533-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a0533-165">Next steps</span></span>

<span data-ttu-id="a0533-166">Apache Spark için .NET ile akış verilerini nasıl işeceğinizi öğrenmek için bir sonraki makaleye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="a0533-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a0533-167">Öğretici: Apache Spark için .NET ile Yapılandırılmış Akış</span><span class="sxs-lookup"><span data-stu-id="a0533-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
