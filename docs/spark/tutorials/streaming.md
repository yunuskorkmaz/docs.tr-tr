---
title: Apache Spark öğreticisi için .NET ile yapılandırılmış akış
description: Bu öğreticide, Spark yapılandırılmış akış için Apache Spark .NET kullanmayı öğreneceksiniz.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 83d44af080d95ab6f9311ddd3ca4860806757436
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504036"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="58b09-103">Öğretici: Apache Spark için .NET ile yapılandırılmış akış</span><span class="sxs-lookup"><span data-stu-id="58b09-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span> 

<span data-ttu-id="58b09-104">Bu öğreticide, Apache Spark için .NET kullanarak Spark yapılandırılmış akış çağırma öğretilir.</span><span class="sxs-lookup"><span data-stu-id="58b09-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="58b09-105">Spark yapısal akışı, gerçek zamanlı veri akışlarını işleme Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="58b09-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="58b09-106">Akış işleme, canlı verileri üretildiğinde analiz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="58b09-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="58b09-107">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58b09-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="58b09-108">Apache Spark uygulaması için .NET oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="58b09-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="58b09-109">Netcat kullanarak bir veri akışı oluşturun</span><span class="sxs-lookup"><span data-stu-id="58b09-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="58b09-110">Akış verilerini çözümlemek için Kullanıcı tanımlı işlevler ve parlak SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="58b09-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58b09-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="58b09-111">Prerequisites</span></span>

<span data-ttu-id="58b09-112">Apache Spark uygulama için ilk .NET ise, temel bilgileri öğrenecek başlangıç [öğreticisiyle](get-started.md) başlayın.</span><span class="sxs-lookup"><span data-stu-id="58b09-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="58b09-113">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="58b09-113">Create a console application</span></span>

1. <span data-ttu-id="58b09-114">Komut istemindeki yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="58b09-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="58b09-115">`dotnet` komutu sizin için `console` türünde bir `new` uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58b09-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="58b09-116">`-o` parametresi, uygulamanızın depolandığı *Mymini Streamingapp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="58b09-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="58b09-117">`cd mySparkStreamingApp` komutu, dizini yeni oluşturduğunuz uygulama diziniyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="58b09-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="58b09-118">.NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="58b09-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="58b09-119">Konsolunuza aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="58b09-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="58b09-120">Bir veri akışı oluşturun ve bu akışa bağlanın</span><span class="sxs-lookup"><span data-stu-id="58b09-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="58b09-121">Akış işlemeyi test etmenin popüler bir yolu **netcat**kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="58b09-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="58b09-122">netcat ( *NC*olarak da bilinir) ağ bağlantılarından okuyup yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="58b09-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="58b09-123">Bir Terminal penceresi aracılığıyla netcat ile bir ağ bağlantısı kurarsınız.</span><span class="sxs-lookup"><span data-stu-id="58b09-123">You establish a network connection with netcat through a terminal window.</span></span> 

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="58b09-124">Netcat ile veri akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="58b09-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="58b09-125">[Netcat 'ı indirin](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="58b09-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="58b09-126">Sonra, dosyayı ZIP indirsitesinden ayıklayın ve "PATH" ortam değişkeninizden ayıkladığınız dizini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58b09-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="58b09-127">Yeni bir bağlantı başlatmak için yeni bir konsol açın ve 9999 numaralı bağlantı noktasında localhost 'a bağlanan aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58b09-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="58b09-128">Windows'da:</span><span class="sxs-lookup"><span data-stu-id="58b09-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="58b09-129">Linux üzerinde:</span><span class="sxs-lookup"><span data-stu-id="58b09-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="58b09-130">Spark programınız, bu komut istemine yazdığınız girişi dinler.</span><span class="sxs-lookup"><span data-stu-id="58b09-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="58b09-131">Mini oturum oluşturma</span><span class="sxs-lookup"><span data-stu-id="58b09-131">Create a SparkSession</span></span>

1. <span data-ttu-id="58b09-132">Aşağıdaki ek `using` deyimlerini *Mymini Streamingapp*içindeki *program.cs* dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="58b09-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="58b09-133">Yeni bir `SparkSession`oluşturmak için `Main` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58b09-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="58b09-134">Spark oturumu, veri kümesi ve DataFrame API 'SI ile Spark programlamanın giriş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="58b09-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="58b09-135">Yukarıda oluşturulan *Spark* nesnesini çağırmak, programınızın tamamında Spark ve dataframe işlevlerine erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="58b09-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="58b09-136">ReadStream () ile bir akışa bağlanma</span><span class="sxs-lookup"><span data-stu-id="58b09-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="58b09-137">`ReadStream()` yöntemi, içindeki akış verilerini `DataFrame`olarak okumak için kullanılabilecek bir `DataStreamReader` döndürür.</span><span class="sxs-lookup"><span data-stu-id="58b09-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="58b09-138">Spark uygulamanıza akış verilerinin nerede beklendiğini bildirmek için konak ve bağlantı noktası bilgilerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58b09-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="58b09-139">Kullanıcı tanımlı bir işlevi kaydetme</span><span class="sxs-lookup"><span data-stu-id="58b09-139">Register a user-defined function</span></span>

<span data-ttu-id="58b09-140">Verilerinizde hesaplamalar ve analiz yapmak için Spark uygulamalarında Kullanıcı tanımlı UDF 'ler, *Kullanıcı tanımlı işlevler*' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58b09-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="58b09-141">`udfArray`adlı bir UDF kaydetmek için `Main` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58b09-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span> 

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="58b09-142">Bu UDF, özgün dizeyi ( *Str*içinde bulunur) içeren bir dizi oluşturmak için netcat terminalinden aldığı her dizeyi işler ve özgün dizenin uzunluğu ile birleştirilmiş özgün dizenin önüne gelir.</span><span class="sxs-lookup"><span data-stu-id="58b09-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span> 

<span data-ttu-id="58b09-143">Örneğin, Netcat terminalinde *Hello World* girilmesi, şu durumlarda bir dizi üretir:</span><span class="sxs-lookup"><span data-stu-id="58b09-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="58b09-144">dizi\[0] = Merhaba Dünya</span><span class="sxs-lookup"><span data-stu-id="58b09-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="58b09-145">dizi\[1] = Merhaba Dünya 11</span><span class="sxs-lookup"><span data-stu-id="58b09-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="58b09-146">Mini kullanılan SQL kullan</span><span class="sxs-lookup"><span data-stu-id="58b09-146">Use SparkSQL</span></span>

<span data-ttu-id="58b09-147">Veri Çerçeverinizdeki depolanan veriler üzerinde çeşitli işlevler gerçekleştirmek için, parlak SQL kullanın.</span><span class="sxs-lookup"><span data-stu-id="58b09-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="58b09-148">Veri çerçevesinin her satırına bir UDF uygulamak için UDF 'Leri ve parlak SQL 'i birleştirmek yaygındır.</span><span class="sxs-lookup"><span data-stu-id="58b09-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="58b09-149">Bu kod parçacığı, Netcat terminalinizden okunan her dizeyi temsil eden veri Çerçevenizle her bir değere *Udfarray* uygular.</span><span class="sxs-lookup"><span data-stu-id="58b09-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="58b09-150">Dizinizin her girdisini kendi satırına yerleştirmek için <xref:Microsoft.Spark.Sql.Functions.Explode%2A>, Mini SQL metodunu uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58b09-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="58b09-151">Son olarak, yeni DataFrame *Arraydf* içinde üretilebilen sütunları yerleştirmek için <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="58b09-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="58b09-152">Akışınızı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="58b09-152">Display your stream</span></span>

<span data-ttu-id="58b09-153">Sonuçları konsola yazdırma ve yalnızca en son çıktıyı görüntüleme gibi, çıktlarınızın özelliklerini oluşturmak için <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> kullanın.</span><span class="sxs-lookup"><span data-stu-id="58b09-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="58b09-154">Kodunuzu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="58b09-154">Run your code</span></span>

<span data-ttu-id="58b09-155">Spark 'ta yapılandırılmış akış, bir dizi küçük **toplu iş**aracılığıyla verileri işler.</span><span class="sxs-lookup"><span data-stu-id="58b09-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="58b09-156">Programınızı çalıştırdığınızda, Netcat bağlantısını oluşturduğunuz komut istemi yazmaya başlayabilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="58b09-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="58b09-157">Bu komut istemine veri yazdıktan sonra ENTER tuşuna her bastığınızda, Spark girişi bir toplu iş olarak değerlendirir ve UDF 'yi çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="58b09-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="58b09-158">Uygulamanızı çalıştırmak için Spark-Gönder kullanın</span><span class="sxs-lookup"><span data-stu-id="58b09-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="58b09-159">Yeni bir netcat oturumu başlattıktan sonra, yeni bir Terminal açın ve aşağıdaki komuta benzer şekilde `spark-submit` komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="58b09-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="58b09-160">Yukarıdaki komutu, Microsoft Spark jar dosyanızın gerçek yoluyla güncelleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="58b09-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="58b09-161">Yukarıdaki komut Ayrıca, Netcat sunucunuzun localhost bağlantı noktası 9999 üzerinde çalıştığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="58b09-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="58b09-162">Kodu alma</span><span class="sxs-lookup"><span data-stu-id="58b09-162">Get the code</span></span>

<span data-ttu-id="58b09-163">Bu öğretici [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) örneğini kullanır, ancak GitHub 'da üç farklı tam akış işleme örneği vardır:</span><span class="sxs-lookup"><span data-stu-id="58b09-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="58b09-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): herhangi bir kaynaktan akan verilerdeki sözcük sayısı</span><span class="sxs-lookup"><span data-stu-id="58b09-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="58b09-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): Pencereleme mantığı ile veri üzerinde sözcük sayısı</span><span class="sxs-lookup"><span data-stu-id="58b09-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="58b09-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): Kafka 'den akan verilerdeki sözcük sayısı</span><span class="sxs-lookup"><span data-stu-id="58b09-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="58b09-167">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="58b09-167">Next steps</span></span>

<span data-ttu-id="58b09-168">.NET Apache Spark uygulamanızı Databricks 'e dağıtmayı öğrenmek için sonraki makaleye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="58b09-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="58b09-169">Öğretici: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı</span><span class="sxs-lookup"><span data-stu-id="58b09-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
