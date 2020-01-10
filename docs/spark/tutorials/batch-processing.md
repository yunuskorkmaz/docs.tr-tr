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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="488e2-103">Öğretici: Apache Spark için .NET ile Batch işleme</span><span class="sxs-lookup"><span data-stu-id="488e2-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="488e2-104">Bu öğreticide, Apache Spark için .NET kullanarak toplu işleme yapmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="488e2-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="488e2-105">Toplu işlem, kaynak verilerin daha önce veri depolamaya yüklenmiş olduğu anlamına gelen verilerin bekleyen dönüşümdedir.</span><span class="sxs-lookup"><span data-stu-id="488e2-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span> 

<span data-ttu-id="488e2-106">Toplu işleme genellikle daha fazla analiz için hazırlanması gereken büyük ve düz veri kümelerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="488e2-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="488e2-107">Günlük işleme ve veri ambarı, yaygın toplu işleme senaryolardır.</span><span class="sxs-lookup"><span data-stu-id="488e2-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="488e2-108">Bu senaryoda, farklı projelerin kullanıldığı zaman sayısı veya son projelerin güncelleştirildiği süre gibi GitHub projeleri hakkındaki bilgileri analiz edersiniz.</span><span class="sxs-lookup"><span data-stu-id="488e2-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span> 

<span data-ttu-id="488e2-109">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="488e2-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="488e2-110">Apache Spark uygulaması için .NET oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="488e2-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="488e2-111">Verileri bir veri çerçevesine okuyun ve analiz için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="488e2-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="488e2-112">Spark SQL kullanarak verileri işleme</span><span class="sxs-lookup"><span data-stu-id="488e2-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="488e2-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="488e2-113">Prerequisites</span></span> 

<span data-ttu-id="488e2-114">Apache Spark için .NET 'i ilk kez kullanıyorsanız, ortamınızı nasıl hazırlayacağınızı ve Apache Spark uygulama için ilk .NET uygulamanızı nasıl çalıştıracağınızı öğrenmek için [.NET ile çalışmaya başlama](../tutorials/get-started.md) hakkında bilgi edinmek için Apache Spark öğreticisine göz atın.</span><span class="sxs-lookup"><span data-stu-id="488e2-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="488e2-115">Örnek verileri indirme</span><span class="sxs-lookup"><span data-stu-id="488e2-115">Download the sample data</span></span>

<span data-ttu-id="488e2-116">[Ghtorkiralık](http://ghtorrent.org/) , projeler, işlemeler ve izleyicileri hakkında bilgi gibi tüm genel GitHub olaylarını izler ve olayları ve bunların yapısını veritabanlarında depolar.</span><span class="sxs-lookup"><span data-stu-id="488e2-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="488e2-117">Farklı zaman dilimlerinde toplanan veriler indirilebilir Arşivler olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="488e2-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="488e2-118">Döküm dosyaları çok büyük olduğundan, bu kılavuz GitHub 'dan indirilebilen [döküm dosyasının kesilmiş bir sürümünü](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) kullanır.</span><span class="sxs-lookup"><span data-stu-id="488e2-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="488e2-119">Ghtorıo veri kümesi, bir çift lisanslama şeması ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)) altında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="488e2-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="488e2-120">Ticari olmayan kullanımlar için (eğitim, araştırma veya kişisel kullanımları dahil, ancak bunlarla sınırlı olmamak üzere), veri kümesi, [bilgi-SA lisansı](https://creativecommons.org/licenses/by-sa/4.0/)altında dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="488e2-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="488e2-121">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="488e2-121">Create a console application</span></span>

1. <span data-ttu-id="488e2-122">Komut istemindeki yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="488e2-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="488e2-123">`dotnet` komutu sizin için `console` türünde bir `new` uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="488e2-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="488e2-124">`-o` parametresi, uygulamanızın depolandığı *Mymini Batchapp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="488e2-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="488e2-125">`cd mySparkBatchApp` komutu, dizini yeni oluşturduğunuz uygulama diziniyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="488e2-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="488e2-126">.NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="488e2-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="488e2-127">Konsolunuza aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="488e2-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="488e2-128">Mini oturum oluşturma</span><span class="sxs-lookup"><span data-stu-id="488e2-128">Create a SparkSession</span></span>

1. <span data-ttu-id="488e2-129">Aşağıdaki ek `using` deyimlerini *Mymini Batchapp*'teki *program.cs* dosyasının en üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="488e2-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="488e2-130">Aşağıdaki kodu proje ad alanına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="488e2-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="488e2-131">*s_referenceData* , programın daha sonra tarihe göre filtrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="488e2-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="488e2-132">Yeni bir mini oturum oluşturmak için aşağıdaki kodu Main yönteminizin içine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="488e2-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="488e2-133">Mini veri kümesi ve DataFrame API 'SI ile Spark programlama için mini oturum giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="488e2-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="488e2-134">`spark` nesnesini çağırarak, program genelinde Spark ve DataFrame işlevlerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488e2-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="488e2-135">Verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="488e2-135">Prepare the data</span></span>

1. <span data-ttu-id="488e2-136">Giriş dosyasını, adlandırılmış sütunlara düzenlenmiş bir veri koleksiyonu olan bir `DataFrame`okuyun.</span><span class="sxs-lookup"><span data-stu-id="488e2-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="488e2-137">Verilerinize ait sütunları <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>aracılığıyla ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488e2-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="488e2-138">Veri Çerçevinizdeki verileri göstermek için <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="488e2-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="488e2-139">CSV dosya yolunu indirdiğiniz GitHub verilerinin konumuyla güncelleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="488e2-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="488e2-140">Verileri boş (null) değerleri ile bırakmak için <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> yöntemini ve verilerden belirli sütunları kaldırmak için <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="488e2-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="488e2-141">Bu, son analiziyle ilgili olmayan null verileri veya sütunları çözümlemeyi denerseniz hataları önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="488e2-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="488e2-142">Verileri analiz etme</span><span class="sxs-lookup"><span data-stu-id="488e2-142">Analyze the data</span></span>

<span data-ttu-id="488e2-143">Spark SQL, verileriniz üzerinde SQL çağrıları yapmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="488e2-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="488e2-144">Veri Çerçevinizdeki tüm satırlara Kullanıcı tanımlı bir işlev uygulamak için Kullanıcı tanımlı işlevleri ve Spark SQL 'i birleştirmek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="488e2-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="488e2-145">Diğer tür uygulamalarda görülen standart SQL çağrılarını taklit etmek için `spark.Sql` özel olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488e2-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="488e2-146">Ayrıca, <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> ve <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> gibi yöntemleri çağırıp verilerinize özel olarak birleştirme, filtre uygulama ve hesaplamalar yapma işlemleri yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488e2-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="488e2-147">Bu uygulamanın hedefi, GitHub projeleri verileri hakkında bazı öngörülere sahip olmaktır.</span><span class="sxs-lookup"><span data-stu-id="488e2-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="488e2-148">Verileri çözümlemek için programınıza aşağıdaki kod parçacıklarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="488e2-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="488e2-149">Aşağıdaki kod bloğunu eklemek, her dilin ne kadar ele geçirilmiş olduğunu bulur.</span><span class="sxs-lookup"><span data-stu-id="488e2-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="488e2-150">İlk olarak, veriler dile göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="488e2-150">First, the data is grouped by language.</span></span> <span data-ttu-id="488e2-151">Ardından, her dilden ortalama çatalların sayısı alınır.</span><span class="sxs-lookup"><span data-stu-id="488e2-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="488e2-152">En çok kullanılan dilleri görmek için Ortalama çatalların sayısını azalan sırada sıralamak üzere aşağıdaki kod bloğunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="488e2-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="488e2-153">Yani, en fazla çatallar ilk olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="488e2-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show(); 
   ```

1. <span data-ttu-id="488e2-154">Sonraki kod bloğu, son projelerin güncelleştirilme şeklini gösterir.</span><span class="sxs-lookup"><span data-stu-id="488e2-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="488e2-155">*MyUDF* adlı yeni bir Kullanıcı tanımlı işlevi kaydeder ve öğreticinin başlangıcında bildirildiği bir tarih, *s_referenceDate*ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="488e2-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="488e2-156">Her projenin tarihi başvuru tarihine göre karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="488e2-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="488e2-157">Daha sonra Spark SQL, veri kümesindeki her bir projeyi analiz etmek üzere verilerin her satırında UDF 'yi çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="488e2-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="488e2-158">Parlak oturumu sonlandırmak için `spark.Stop()` çağırın.</span><span class="sxs-lookup"><span data-stu-id="488e2-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="488e2-159">Uygulamanızı çalıştırmak için Spark-Gönder kullanın</span><span class="sxs-lookup"><span data-stu-id="488e2-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="488e2-160">.NET uygulamanızı derlemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="488e2-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="488e2-161">Uygulamanızı `spark-submit`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="488e2-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="488e2-162">Aşağıdaki komutu Microsoft Spark jar dosyanıza yönelik gerçek yollarla güncelleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="488e2-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="488e2-163">Kodu edinin</span><span class="sxs-lookup"><span data-stu-id="488e2-163">Get the code</span></span>

<span data-ttu-id="488e2-164">[Tam çözümü](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) GitHub ' da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488e2-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="488e2-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="488e2-165">Next steps</span></span>

<span data-ttu-id="488e2-166">Apache Spark için .NET ile akış verilerini nasıl işleyebileceğinizi öğrenmek için sonraki makaleye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="488e2-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="488e2-167">Öğretici: Apache Spark için .NET ile yapılandırılmış akış</span><span class="sxs-lookup"><span data-stu-id="488e2-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
