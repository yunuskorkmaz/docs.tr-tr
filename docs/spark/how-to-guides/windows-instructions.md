---
title: Windows'da Apache Spark uygulaması için bir .NET oluşturma
description: Windows'da Apache Spark uygulaması için .NET'inizi nasıl oluşturacağınızı öğrenin.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185753"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="29c17-103">Windows'da Apache Spark uygulaması için .NET uygulamanızı nasıl oluşturacağınızı öğrenin</span><span class="sxs-lookup"><span data-stu-id="29c17-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="29c17-104">Bu makalede, Windows'da Apache Spark uygulamaları için .NET'inizi nasıl oluşturabileceğinizöğretilir.</span><span class="sxs-lookup"><span data-stu-id="29c17-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="29c17-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="29c17-105">Prerequisites</span></span>

<span data-ttu-id="29c17-106">Aşağıdaki ön koşulların tümüne zaten sahipseniz, [yapı](#build) adımlarına atlayın.</span><span class="sxs-lookup"><span data-stu-id="29c17-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="29c17-107">.NET **[Core SDK'yı](https://dotnet.microsoft.com/download/dotnet-core/2.1)** indirin ve kurun `dotnet` - SDK'yı yüklemek araç zincirini yolunuza ekleyecek.</span><span class="sxs-lookup"><span data-stu-id="29c17-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="29c17-108">.NET Core 2.1, 2.2 ve 3.1 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="29c17-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="29c17-109">**[Visual Studio 2019'u](https://www.visualstudio.com/downloads/)** yükleyin (Sürüm 16.3 veya sonrası).</span><span class="sxs-lookup"><span data-stu-id="29c17-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="29c17-110">Topluluk sürümü tamamen ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="29c17-110">The Community version is completely free.</span></span> <span data-ttu-id="29c17-111">Yüklemenizi yapılandırırken, bu bileşenleri en az olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="29c17-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="29c17-112">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="29c17-112">.NET desktop development</span></span>
       * <span data-ttu-id="29c17-113">Gerekli Tüm Bileşenler</span><span class="sxs-lookup"><span data-stu-id="29c17-113">All Required Components</span></span>
         * <span data-ttu-id="29c17-114">.NET Framework 4.6.1 Geliştirme Araçları</span><span class="sxs-lookup"><span data-stu-id="29c17-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="29c17-115">.NET Core çoklu platform geliştirme</span><span class="sxs-lookup"><span data-stu-id="29c17-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="29c17-116">Gerekli Tüm Bileşenler</span><span class="sxs-lookup"><span data-stu-id="29c17-116">All Required Components</span></span>
  3. <span data-ttu-id="29c17-117">**[Java 1.8'i yükleyin.](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**</span><span class="sxs-lookup"><span data-stu-id="29c17-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span>
     - <span data-ttu-id="29c17-118">İşletim sisteminiz için uygun sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="29c17-118">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="29c17-119">Örneğin, Windows x64 makine için *jdk-8u201-windows-x64.exe.*</span><span class="sxs-lookup"><span data-stu-id="29c17-119">For example, *jdk-8u201-windows-x64.exe* for Windows x64 machine.</span></span>
     - <span data-ttu-id="29c17-120">Yükleyiciyi kullanarak yükleyin ve komut `java` satırınızdan çalıştırabileceğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="29c17-120">Install using the installer and verify you are able to run `java` from your command line.</span></span>
  4. <span data-ttu-id="29c17-121">**[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)** yükleyin.</span><span class="sxs-lookup"><span data-stu-id="29c17-121">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="29c17-122">Karşıdan yükleme [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="29c17-122">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).</span></span>
     - <span data-ttu-id="29c17-123">Yerel bir dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="29c17-123">Extract to a local directory.</span></span> <span data-ttu-id="29c17-124">Örneğin, \*C:\bin\apache-maven-3.6.0\*.</span><span class="sxs-lookup"><span data-stu-id="29c17-124">For example, \*C:\bin\apache-maven-3.6.0\*.</span></span>
     - <span data-ttu-id="29c17-125">Apache Maven'i [PATH ortamı değişkenine](https://www.java.com/en/download/help/path.xml)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29c17-125">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="29c17-126">Örneğin, *C:\bin\apache-maven-3.6.0\bin*.</span><span class="sxs-lookup"><span data-stu-id="29c17-126">For example, *C:\bin\apache-maven-3.6.0\bin*.</span></span>
     - <span data-ttu-id="29c17-127">Komut satırınızdan çalıştırabileceğinizi `mvn` doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="29c17-127">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="29c17-128">**[Apache Spark 2.3+ yükleyin.](https://spark.apache.org/downloads.html)**</span><span class="sxs-lookup"><span data-stu-id="29c17-128">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="29c17-129">[Apache Spark 2.3+](https://spark.apache.org/downloads.html) indirin ve 7 zip kullanarak yerel bir klasöre (örneğin, *C:\bin\spark-2.3.2-bin-hadoop2.7)\*ayıklayın. [7-zip](https://www.7-zip.org/) (Desteklenen kıvılcım versiyonları 2.3.*, 2.4.0, 2.4.1, 2.4.3 ve 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="29c17-129">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (for example, *C:\bin\spark-2.3.2-bin-hadoop2.7\*) using [7-zip](https://www.7-zip.org/). (The supported spark versions are 2.3.*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="29c17-130">Yeni bir [ortam değişkeni](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29c17-130">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`.</span></span> <span data-ttu-id="29c17-131">Örneğin, \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span><span class="sxs-lookup"><span data-stu-id="29c17-131">For example, \*C:\bin\spark-2.3.2-bin-hadoop2.7\*.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - <span data-ttu-id="29c17-132">[PATH ortamı değişkeninize](https://www.java.com/en/download/help/path.xml)Apache Spark ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29c17-132">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="29c17-133">Örneğin, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span><span class="sxs-lookup"><span data-stu-id="29c17-133">For example, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.</span></span>

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - <span data-ttu-id="29c17-134">Komut satırınızdan çalıştırabileceğinizi `spark-shell` doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="29c17-134">Verify you are able to run `spark-shell` from your command-line.</span></span>
        <span data-ttu-id="29c17-135">Örnek konsol çıkışı:</span><span class="sxs-lookup"><span data-stu-id="29c17-135">Sample console output:</span></span>

        ```
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. <span data-ttu-id="29c17-136">**[WinUtils'i](https://github.com/steveloughran/winutils)** yükleyin.</span><span class="sxs-lookup"><span data-stu-id="29c17-136">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="29c17-137">`winutils.exe` [WinUtils deposundan ikili indirin.](https://github.com/steveloughran/winutils)</span><span class="sxs-lookup"><span data-stu-id="29c17-137">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="29c17-138">Spark dağıtımının derlenmiş olduğu Hadoop sürümünü seçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="29c17-138">You should select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="29c17-139">Exammple için, Spark 2.3.2 için hadoop-2.7.1 kullanın.</span><span class="sxs-lookup"><span data-stu-id="29c17-139">For exammple, use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="29c17-140">İkiliyi seçtiğiniz bir dizine kaydedin. `winutils.exe`</span><span class="sxs-lookup"><span data-stu-id="29c17-140">Save `winutils.exe` binary to a directory of your choice.</span></span> <span data-ttu-id="29c17-141">Örneğin, *C:\hadoop\bin*.</span><span class="sxs-lookup"><span data-stu-id="29c17-141">For example, *C:\hadoop\bin*.</span></span>
     - <span data-ttu-id="29c17-142">Winutils.exe (çöp kutusu olmadan) ile dizin yansıtacak şekilde ayarlayın. `HADOOP_HOME`</span><span class="sxs-lookup"><span data-stu-id="29c17-142">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="29c17-143">Örneğin, komut satırı kullanarak:</span><span class="sxs-lookup"><span data-stu-id="29c17-143">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="29c17-144">PATH ortamı değişkenini ' eklenecek `%HADOOP_HOME%\bin`şekilde ayarlayın</span><span class="sxs-lookup"><span data-stu-id="29c17-144">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="29c17-145">Örneğin, komut satırLarını kullanarak:</span><span class="sxs-lookup"><span data-stu-id="29c17-145">For instance, using command line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="29c17-146">Bir sonraki bölüme `dotnet`geçmeden `java` `mvn`önce `spark-shell` komut satırınızdan , , , çalıştırabildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="29c17-146">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span> <span data-ttu-id="29c17-147">Daha iyi bir yol olduğunu mu düşünüyorsun?</span><span class="sxs-lookup"><span data-stu-id="29c17-147">Feel there is a better way?</span></span> <span data-ttu-id="29c17-148">[Bir sorun açın](https://github.com/dotnet/spark/issues) ve katkıda bulunmakiçin çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="29c17-148">[Open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="29c17-149">Herhangi bir ortam değişkeni güncelleştirilmişse komut satırının yeni bir örneği gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="29c17-149">A new instance of the command line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="29c17-150">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29c17-150">Build</span></span>

<span data-ttu-id="29c17-151">Bu kılavuzun geri kalanı için, Apache Spark deposu için .NET'i makinenize klonlamış olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="29c17-151">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="29c17-152">Klonlanmış depo için istediğiniz yeri seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29c17-152">You can choose any location for the cloned repository.</span></span> <span data-ttu-id="29c17-153">Örneğin, \*C:\github\dotnet-spark\*.</span><span class="sxs-lookup"><span data-stu-id="29c17-153">For example, \*C:\github\dotnet-spark\*.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="29c17-154">Apache Scala uzantıları katmanı için .NET oluştur</span><span class="sxs-lookup"><span data-stu-id="29c17-154">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="29c17-155">Bir .NET başvurusu gönderdiğinizde , .NET for Apache Spark'ın Scala'da yazılmış olması gereken mantık Scala'da yazılıdır ve isteklerinizi nasıl işleyeceğinizi bildirir (örneğin, yeni bir Kıvılcım Oturumu oluşturma isteği, .NET tarafından JVM tarafına veri aktarımı isteği vb.).</span><span class="sxs-lookup"><span data-stu-id="29c17-155">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (for example, request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="29c17-156">Bu mantık [Spark Scala Kaynak Kodu için .NET](https://github.com/dotnet/spark/tree/master/src/scala)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="29c17-156">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="29c17-157">.NET Framework veya .NET Core kullanıyor sanız, Apache Spark Scala uzantı katmanı için .NET'i oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="29c17-157">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package
```

<span data-ttu-id="29c17-158">Desteklenen Spark sürümleri için oluşturulan JAR'ları görmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="29c17-158">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="29c17-159">Kıvılcım örnek uygulamaları için .NET'i oluşturun</span><span class="sxs-lookup"><span data-stu-id="29c17-159">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="29c17-160">Bu bölümde, Apache Spark için .NET [için örnek uygulamaların](https://github.com/dotnet/spark/tree/master/examples) nasıl oluşturulabildiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29c17-160">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="29c17-161">Bu adımlar, Kıvılcım uygulaması için herhangi bir .NET için genel oluşturma işlemini anlamada yardımcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="29c17-161">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="29c17-162">.NET Framework için Visual Studio'u kullanma</span><span class="sxs-lookup"><span data-stu-id="29c17-162">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="29c17-163">Visual `src\csharp\Microsoft.Spark.sln` Studio'da açın `Microsoft.Spark.CSharp.Examples` ve `examples` projeyi klasörün altında oluşturun (bu da .NET ciltleme projesini oluşturur).</span><span class="sxs-lookup"><span data-stu-id="29c17-163">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="29c17-164">İsterseniz, `Microsoft.Spark.Examples` projeye kendi kodunuzu yazabilirsiniz (bu örnekteki 'input_file.json' ile veri çerçevesi oluşturmak istediğiniz verilerin yer verdiği bir json dosyasıdır):</span><span class="sxs-lookup"><span data-stu-id="29c17-164">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     <span data-ttu-id="29c17-165">Yapı başarılı olduktan sonra, çıktı dizininde üretilen uygun ikilileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="29c17-165">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>
     <span data-ttu-id="29c17-166">Örnek konsol çıkışı:</span><span class="sxs-lookup"><span data-stu-id="29c17-166">Sample console output:</span></span>

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="29c17-167">.NET Core için .NET Çekirdek CLI'yi kullanma</span><span class="sxs-lookup"><span data-stu-id="29c17-167">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="29c17-168">Şu anda Spark .NET için .NET Core yapılarını otomatikleştirmek üzerinde çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="29c17-168">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="29c17-169">O zamana kadar, bazı adımları el ile gerçekleştirmedeki sabrınız için teşekkür ederiz.</span><span class="sxs-lookup"><span data-stu-id="29c17-169">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="29c17-170">İşçiyi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29c17-170">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="29c17-171">Örnek konsol çıkışı:</span><span class="sxs-lookup"><span data-stu-id="29c17-171">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. <span data-ttu-id="29c17-172">Örnekleri oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29c17-172">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      <span data-ttu-id="29c17-173">Örnek konsol çıkışı:</span><span class="sxs-lookup"><span data-stu-id="29c17-173">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="29c17-174">Kıvılcım örnek uygulamaları için .NET'i çalıştırın</span><span class="sxs-lookup"><span data-stu-id="29c17-174">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="29c17-175">Örnekleri oluşturduğunuzda, .NET Framework `spark-submit` veya .NET Core'u hedefleyip hedeflemediğinize bakılmaksızın bunları çalıştırmak yoluyla olacaktır.</span><span class="sxs-lookup"><span data-stu-id="29c17-175">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="29c17-176">[Önkoşullar](#prerequisites) bölümünü takip ettiğinizden ve Apache Spark'ı yüklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="29c17-176">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="29c17-177">İkilinin `DOTNET_WORKER_DIR` `PATH` oluşturulduğu yolu içerecek şekilde ayarlayın (örneğin, *C:\github\dotnet\spark\artlar\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artlar\bin\Microsoft.Spark.Worker\Debug\Netcorenet2.1\win10-x64\net publish.NET):* `Microsoft.Spark.Worker`</span><span class="sxs-lookup"><span data-stu-id="29c17-177">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="29c17-178">Powershell'i açın ve uygulama ikilinizin oluşturulduğu dizine gidin (örneğin, *C:\github\dotnet\spark\artifaks\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core için:</span><span class="sxs-lookup"><span data-stu-id="29c17-178">Open Powershell and go to the directory where your app binary has been generated (for example, *C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="29c17-179">Uygulamanızı çalıştırmak temel yapıyı izler:</span><span class="sxs-lookup"><span data-stu-id="29c17-179">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="29c17-180">Çalıştırabileceğiniz bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="29c17-180">Here are some examples you can run:</span></span>

     - <span data-ttu-id="29c17-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="29c17-181">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="29c17-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="29c17-182">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="29c17-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven erişilebilir)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="29c17-183">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="29c17-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (kavanoz lar sağlandı)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="29c17-184">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
