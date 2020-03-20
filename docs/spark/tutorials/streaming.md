---
title: Apache Spark öğretici için .NET ile Yapılandırılmış Akış
description: Bu eğitimde, Spark Structured Streaming için Apache Spark için .NET'i nasıl kullanacağınızı öğreneceksiniz.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186507"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="01a5f-103">Öğretici: Apache Spark için .NET ile Yapılandırılmış Akış</span><span class="sxs-lookup"><span data-stu-id="01a5f-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="01a5f-104">Bu öğretici, Apache Spark için .NET kullanarak Spark Yapılandırılmış Akışı nasıl çağıracağınız öğretilir.</span><span class="sxs-lookup"><span data-stu-id="01a5f-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="01a5f-105">Spark Structured Streaming, Apache Spark'ın gerçek zamanlı veri akışlarını işlemek için verdiği destektir.</span><span class="sxs-lookup"><span data-stu-id="01a5f-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="01a5f-106">Akış işleme, canlı verilerin üretilirken analiz edilmesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="01a5f-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="01a5f-107">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="01a5f-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="01a5f-108">Apache Spark uygulaması için bir .NET oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="01a5f-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="01a5f-109">Veri akışı oluşturmak için netcat'i kullanma</span><span class="sxs-lookup"><span data-stu-id="01a5f-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="01a5f-110">Akış verilerini analiz etmek için kullanıcı tanımlı işlevleri ve SparkSQL'i kullanma</span><span class="sxs-lookup"><span data-stu-id="01a5f-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="01a5f-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="01a5f-111">Prerequisites</span></span>

<span data-ttu-id="01a5f-112">Apache Spark uygulaması için ilk .NET uygulamanızsa, temel bilgileri tanımak için [Başlangıç eğitimiyle](get-started.md) başlayın.</span><span class="sxs-lookup"><span data-stu-id="01a5f-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="01a5f-113">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a5f-113">Create a console application</span></span>

1. <span data-ttu-id="01a5f-114">Komut isteminizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="01a5f-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="01a5f-115">Komut `dotnet` sizin için `new` bir `console` tür uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01a5f-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="01a5f-116">Parametre, `-o` uygulamanızın depolandığı *mySparkStreamingApp* adında bir dizin oluşturur ve gerekli dosyalarla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="01a5f-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="01a5f-117">Komut, `cd mySparkStreamingApp` dizini yeni oluşturduğunuz uygulama dizinine değiştirir.</span><span class="sxs-lookup"><span data-stu-id="01a5f-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="01a5f-118">Bir uygulamada Apache Spark için .NET'i kullanmak için Microsoft.Spark paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="01a5f-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="01a5f-119">Konsolunuzda aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="01a5f-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="01a5f-120">Veri akışı oluşturma ve bağlanma</span><span class="sxs-lookup"><span data-stu-id="01a5f-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="01a5f-121">Akış işlemetest etmek için bir popüler yolu **netcat**geçer.</span><span class="sxs-lookup"><span data-stu-id="01a5f-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="01a5f-122">netcat *(nc*olarak da bilinir) ağ bağlantılarından okumanızı ve yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a5f-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="01a5f-123">Terminal penceresinden netcat ile ağ bağlantısı kurarsınız.</span><span class="sxs-lookup"><span data-stu-id="01a5f-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="01a5f-124">netcat ile veri akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a5f-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="01a5f-125">[Netcat'i indirin.](https://sourceforge.net/projects/nc110/files/)</span><span class="sxs-lookup"><span data-stu-id="01a5f-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="01a5f-126">Ardından, dosyayı zip indirmeden ayıklayın ve çıkardığınız dizin "PATH" ortam değişkenine ekleyip.</span><span class="sxs-lookup"><span data-stu-id="01a5f-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="01a5f-127">Yeni bir bağlantı başlatmak için yeni bir konsol açın ve 9999 portundaki localhost'a bağlanan aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="01a5f-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="01a5f-128">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="01a5f-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="01a5f-129">Linux üzerinde:</span><span class="sxs-lookup"><span data-stu-id="01a5f-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="01a5f-130">Spark programınız bu komut istemine yazdığınız girişi dinler.</span><span class="sxs-lookup"><span data-stu-id="01a5f-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="01a5f-131">Bir SparkSession oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a5f-131">Create a SparkSession</span></span>

1. <span data-ttu-id="01a5f-132">`using` *mySparkStreamingApp'taki* *Program.cs* dosyasının üst bölümüne aşağıdaki ek ifadeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01a5f-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="01a5f-133">`Main` Yeni `SparkSession`bir .</span><span class="sxs-lookup"><span data-stu-id="01a5f-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="01a5f-134">Kıvılcım Oturumu, Dataset ve DataFrame API ile Spark programlamanın giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="01a5f-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="01a5f-135">Yukarıda oluşturulan *kıvılcım* nesnesini aramak, programınız boyunca Spark ve DataFrame işlevlerine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a5f-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="01a5f-136">ReadStream ile bir akışa bağlanın()</span><span class="sxs-lookup"><span data-stu-id="01a5f-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="01a5f-137">Yöntem, `ReadStream()` akış `DataStreamReader` verilerini bir ' de okumak `DataFrame`için kullanılabilecek bir yöntem döndürür.</span><span class="sxs-lookup"><span data-stu-id="01a5f-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="01a5f-138">Spark uygulamanıza akış verilerini nerede beklediğini söylemek için ana bilgisayar ve bağlantı noktası bilgilerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="01a5f-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="01a5f-139">Kullanıcı tanımlı bir işlev kaydetme</span><span class="sxs-lookup"><span data-stu-id="01a5f-139">Register a user-defined function</span></span>

<span data-ttu-id="01a5f-140">Verilerinizde hesaplamalar ve analizler gerçekleştirmek için Spark uygulamalarında *kullanıcı tanımlı işlevler*olan UDF'leri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01a5f-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="01a5f-141">Bir UDF'yi `Main` `udfArray`kaydetmek için yönteminize aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="01a5f-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="01a5f-142">Bu UDF, netcat terminalinden aldığı her dizeyi, özgün dizeyi *(str'de*bulunan) içeren bir dizi oluşturmak için işler ve ardından özgün dize uzunluğuyla birlikte eklenen özgün dizeyi işler.</span><span class="sxs-lookup"><span data-stu-id="01a5f-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="01a5f-143">Örneğin, netcat terminalinde *Hello dünyasına* girmek aşağıdakileri yaptığı bir dizi üretir:</span><span class="sxs-lookup"><span data-stu-id="01a5f-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="01a5f-144">dizi\[0] = Merhaba dünya</span><span class="sxs-lookup"><span data-stu-id="01a5f-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="01a5f-145">dizi\[1] = Merhaba dünya 11</span><span class="sxs-lookup"><span data-stu-id="01a5f-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="01a5f-146">SparkSQL kullanın</span><span class="sxs-lookup"><span data-stu-id="01a5f-146">Use SparkSQL</span></span>

<span data-ttu-id="01a5f-147">DataFrame'inizde depolanan verilerüzerinde çeşitli işlevleri gerçekleştirmek için SparkSQL'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="01a5f-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="01a5f-148">Bir DataFrame'in her satırına UDF uygulamak için UDF'leri ve SparkSQL'i birleştirmek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="01a5f-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="01a5f-149">Bu kod snippet, netcat terminalinizden okunan her dizeyi temsil eden DataFrame'inizdeki her değere *udfArray* uygular.</span><span class="sxs-lookup"><span data-stu-id="01a5f-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="01a5f-150">Dizinizin her <xref:Microsoft.Spark.Sql.Functions.Explode%2A> girişini kendi satırına koymak için SparkSQL yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="01a5f-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="01a5f-151">Son olarak, yeni DataFrame <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> *arrayDF'de* ürettiğiniz sütunları yerleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="01a5f-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="01a5f-152">Akışınızı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="01a5f-152">Display your stream</span></span>

<span data-ttu-id="01a5f-153">Sonuçları <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> konsola yazdırmak ve yalnızca en son çıktıyı görüntülemek gibi çıktınızın özelliklerini oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="01a5f-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="01a5f-154">Kodunuzu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="01a5f-154">Run your code</span></span>

<span data-ttu-id="01a5f-155">Spark'taki yapılandırılmış akış, verileri bir dizi küçük **toplu işlem**le işler.</span><span class="sxs-lookup"><span data-stu-id="01a5f-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="01a5f-156">Programınızı çalıştırdığınızda, netcat bağlantısını kurduğunuz komut istemi yazmaya başlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="01a5f-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="01a5f-157">Bu komut istemine veri yazdıktan sonra Enter tuşuna her bastığınızda, Spark girişinizi bir toplu iş olarak kabul eder ve UDF'yi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="01a5f-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="01a5f-158">Uygulamanızı çalıştırmak için kıvılcım gönder'i kullanma</span><span class="sxs-lookup"><span data-stu-id="01a5f-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="01a5f-159">Yeni bir netcat oturumuna başladıktan sonra, `spark-submit` yeni bir terminal açın ve aşağıdaki komuta benzer şekilde komutunuzu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="01a5f-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="01a5f-160">Yukarıdaki komutu Microsoft Spark jar dosyanıza giden gerçek yol ile güncelleştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="01a5f-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="01a5f-161">Yukarıdaki komut, netcat sunucunuzun localhost port 9999'da çalıştığını da varsayar.</span><span class="sxs-lookup"><span data-stu-id="01a5f-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="01a5f-162">Kodu alma</span><span class="sxs-lookup"><span data-stu-id="01a5f-162">Get the code</span></span>

<span data-ttu-id="01a5f-163">Bu öğretici [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) örneğini kullanır, ancak GitHub'da üç tam akış işleme örneği daha vardır:</span><span class="sxs-lookup"><span data-stu-id="01a5f-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="01a5f-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): herhangi bir kaynaktan aktarılan verilere ilişkin sözcük sayısı</span><span class="sxs-lookup"><span data-stu-id="01a5f-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="01a5f-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): pencereleme mantığı ile verilere kelime sayısı</span><span class="sxs-lookup"><span data-stu-id="01a5f-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="01a5f-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): Kafka'dan aktarılan verilere ilişkin kelime sayısı</span><span class="sxs-lookup"><span data-stu-id="01a5f-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="01a5f-167">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="01a5f-167">Next steps</span></span>

<span data-ttu-id="01a5f-168">Apache Spark uygulamanızı Databricks'e nasıl dağıtacağınız hakkında bilgi edinmek için bir sonraki makaleye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="01a5f-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="01a5f-169">Öğretici: Databricks'e Apache Spark uygulaması için bir .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="01a5f-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
