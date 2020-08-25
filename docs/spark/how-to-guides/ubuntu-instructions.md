---
title: Ubuntu üzerinde Apache Spark uygulaması için .NET oluşturma
description: Ubuntu 'da Apache Spark için .NET uygulamanızı nasıl oluşturacağınızı öğrenin
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: b5e06619611ac06c453df0314bcecb30e1b673a2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812204"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a><span data-ttu-id="1f2c6-103">Ubuntu 'da Apache Spark için .NET uygulamanızı nasıl oluşturacağınızı öğrenin</span><span class="sxs-lookup"><span data-stu-id="1f2c6-103">Learn how to build your .NET for Apache Spark application on Ubuntu</span></span>

<span data-ttu-id="1f2c6-104">Bu makalede, Ubuntu üzerinde Apache Spark uygulamalarınızı .NET için nasıl oluşturabileceğiniz öğretilir.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-104">This article teaches you how to build your .NET for Apache Spark applications on Ubuntu.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="1f2c6-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="1f2c6-105">Prerequisites</span></span>

<span data-ttu-id="1f2c6-106">Aşağıdaki önkoşulların tümüne zaten sahipseniz, [derleme](#build) adımlarına atlayın.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

1. <span data-ttu-id="1f2c6-107">**[.Net core 2,1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** 'sını veya **[.NET Core 3,1 SDK 'sını](https://dotnet.microsoft.com/download/dotnet-core/3.1)** indirin ve yükleyin-SDK 'yı yüklemek `dotnet` yolunuza toolzincirini ekler.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-107">Download and install **[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** or the **[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)** - installing the SDK adds the `dotnet` toolchain to your path.</span></span>  <span data-ttu-id="1f2c6-108">.NET Core 2,1, 2,2 ve 3,1 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>

2. <span data-ttu-id="1f2c6-109">**[OpenJDK 8](https://openjdk.java.net/install/)**' i yükler.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-109">Install **[OpenJDK 8](https://openjdk.java.net/install/)**.</span></span>

   - <span data-ttu-id="1f2c6-110">Aşağıdaki komutu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-110">You can use the following command:</span></span>

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * <span data-ttu-id="1f2c6-111">Komut satırınızdan çalıştırabildiğinizi doğrulayın `java` .</span><span class="sxs-lookup"><span data-stu-id="1f2c6-111">Verify you are able to run `java` from your command-line.</span></span>

      <span data-ttu-id="1f2c6-112">Örnek Java-sürüm çıkışı:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-112">Sample java -version output:</span></span>

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * <span data-ttu-id="1f2c6-113">Zaten birden fazla OpenJDK sürümü yüklüyse ve OpenJDK 8 ' i seçmek istiyorsanız aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-113">If you already have multiple OpenJDK versions installed and want to select OpenJDK 8, use the following command:</span></span>

      ```bash
      sudo update-alternatives --config java
      ```

3. <span data-ttu-id="1f2c6-114">**[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**'yi yükler.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-114">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>

   * <span data-ttu-id="1f2c6-115">Aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-115">Run the following command:</span></span>

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       <span data-ttu-id="1f2c6-116">Terminalinizi kapattığınızda bu ortam değişkenlerinin kaybolacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-116">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="1f2c6-117">Değişikliklerin kalıcı olmasını istiyorsanız, `export` satırları `~/.bashrc` dosyanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-117">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="1f2c6-118">Komut satırınızdan çalıştırabildiğinizi doğrulayın `mvn`</span><span class="sxs-lookup"><span data-stu-id="1f2c6-118">Verify you are able to run `mvn` from your command-line</span></span>

       <span data-ttu-id="1f2c6-119">Örnek MVN sürümü çıkışı:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-119">Sample mvn -version output:</span></span>

       ```output
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. <span data-ttu-id="1f2c6-120">**[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**' yı yükler.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-120">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
<span data-ttu-id="1f2c6-121">[Apache Spark 2.3 +](https://spark.apache.org/downloads.html) indirin ve yerel bir klasöre ayıklayın (ör. `~/bin/spark-2.3.2-bin-hadoop2.7` ).</span><span class="sxs-lookup"><span data-stu-id="1f2c6-121">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7`).</span></span> <span data-ttu-id="1f2c6-122">(Desteklenen Spark sürümleri 2,3. \*, 2.4.0, 2.4.1, 2.4.3 ve 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="1f2c6-122">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>

   ```bash
   tar -xvzf /path/to/spark-2.3.2-bin-hadoop2.7.tgz -C ~/bin/spark-2.3.2-bin-hadoop2.7
   ```

   * <span data-ttu-id="1f2c6-123">Gerekli [ortam değişkenlerini](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (ör. `~/bin/spark-2.3.2-bin-hadoop2.7/` ) ve `PATH` (örn. `$SPARK_HOME/bin:$PATH` ) ekleyin</span><span class="sxs-lookup"><span data-stu-id="1f2c6-123">Add the necessary [environment variables](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (e.g., `~/bin/spark-2.3.2-bin-hadoop2.7/`) and `PATH` (e.g., `$SPARK_HOME/bin:$PATH`)</span></span>

      ```bash
      export SPARK_HOME=~/bin/spark-2.3.2-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      <span data-ttu-id="1f2c6-124">Terminalinizi kapattığınızda bu ortam değişkenlerinin kaybolacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-124">Note that these environment variables will be lost when you close your terminal.</span></span> <span data-ttu-id="1f2c6-125">Değişikliklerin kalıcı olmasını istiyorsanız, `export` satırları `~/.bashrc` dosyanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-125">If you want the changes to be permanent, add the `export` lines to your `~/.bashrc` file.</span></span>

   * <span data-ttu-id="1f2c6-126">Komut satırınızdan çalıştırabildiğinizi doğrulayın `spark-shell` .</span><span class="sxs-lookup"><span data-stu-id="1f2c6-126">Verify you are able to run `spark-shell` from your command-line.</span></span>

      <span data-ttu-id="1f2c6-127">Örnek konsol çıkışı:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-127">Sample console output:</span></span>

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

<span data-ttu-id="1f2c6-128">Bir `dotnet` `java` `mvn` `spark-shell` sonraki bölüme geçmeden önce komut satırınızdan,,,,,, ' i çalıştırabildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-128">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="1f2c6-129">Daha iyi bir yol var mı?</span><span class="sxs-lookup"><span data-stu-id="1f2c6-129">Feel there is a better way?</span></span> <span data-ttu-id="1f2c6-130">Lütfen [bir sorun açıp](https://github.com/dotnet/spark/issues) katkıda bulunmaktan çekinmeyin.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-130">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

## <a name="build"></a><span data-ttu-id="1f2c6-131">Yapı</span><span class="sxs-lookup"><span data-stu-id="1f2c6-131">Build</span></span>

<span data-ttu-id="1f2c6-132">Bu kılavuzun geri kalanında, .NET Apache Spark deposunu makinenize Klonladığınız için, örneğin, `~/dotnet.spark/` .</span><span class="sxs-lookup"><span data-stu-id="1f2c6-132">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine e.g., `~/dotnet.spark/`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a><span data-ttu-id="1f2c6-133">Spark Scala uzantıları katmanı için .NET derleme</span><span class="sxs-lookup"><span data-stu-id="1f2c6-133">Build .NET for Spark Scala extensions layer</span></span>

<span data-ttu-id="1f2c6-134">.NET uygulaması gönderdiğinizde, Apache Spark için .NET, isteklerinizi nasıl işleyeceğinizi (örneğin, yeni bir Spark oturumu oluşturma isteği, .NET tarafından JVM 'ye veri aktarma isteği vb.) Apache Spark bildiren gerekli mantığı içerir.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-134">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="1f2c6-135">Bu mantık, [Apache Spark Scala kaynak kodu için .net](https://github.com/dotnet/spark/tree/master/src/scala)içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-135">This logic can be found in the [.NET for Apache Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="1f2c6-136">Sonraki adım, Apache Spark Scala uzantı katmanını .NET için derlemenize yöneliktir:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-136">The next step is to build the .NET for Apache Spark Scala extension layer:</span></span>

```bash
cd src/scala
mvn clean package
```

<span data-ttu-id="1f2c6-137">Desteklenen Spark sürümleri için oluşturulan JARs ' i görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-137">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x/target/microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x/target/microsoft-spark-2.4.x-<version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a><span data-ttu-id="1f2c6-138">.NET Core CLI kullanarak .NET örnek uygulamaları oluşturun</span><span class="sxs-lookup"><span data-stu-id="1f2c6-138">Build .NET sample applications using .NET Core CLI</span></span>

<span data-ttu-id="1f2c6-139">Bu bölümde, Apache Spark için .NET [örnek uygulamalarının](https://github.com/dotnet/spark/tree/master/examples) nasıl oluşturulacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-139">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="1f2c6-140">Bu adımlar, tüm Spark uygulamaları için tüm .NET oluşturma sürecini kavramaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-140">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

1. <span data-ttu-id="1f2c6-141">Çalışanı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-141">Build the worker:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="1f2c6-142">Örnek konsol çıkışı:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-142">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```

2. <span data-ttu-id="1f2c6-143">Örnekleri oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-143">Build the samples:</span></span>

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   ```

   <span data-ttu-id="1f2c6-144">Örnek konsol çıkışı:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-144">Sample console output:</span></span>

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp2.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.0/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="1f2c6-145">Spark örnek uygulamaları için .NET çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1f2c6-145">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="1f2c6-146">Örnekleri derleyip, `spark-submit` .NET Core uygulamalarınızı göndermek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-146">Once you build the samples, you can use `spark-submit` to submit your .NET Core apps.</span></span> <span data-ttu-id="1f2c6-147">[Önkoşul](#prerequisites) bölümünü izlediğinizden ve Apache Spark yüklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1f2c6-147">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

1. <span data-ttu-id="1f2c6-148">`DOTNET_WORKER_DIR`Veya `PATH` ortam değişkenini, `Microsoft.Spark.Worker` ikilinin oluşturulduğu yolu (örn.) içerecek şekilde ayarlayın `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish` .</span><span class="sxs-lookup"><span data-stu-id="1f2c6-148">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

2. <span data-ttu-id="1f2c6-149">Bir Terminal açın ve uygulama ikilisinin oluşturulduğu dizine gidin (ör. `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish` ).</span><span class="sxs-lookup"><span data-stu-id="1f2c6-149">Open a terminal and go to the directory where your app binary has been generated (e.g., `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish`).</span></span>

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp2.1/ubuntu.18.04-x64/publish
   ```

3. <span data-ttu-id="1f2c6-150">Uygulamanızı çalıştırmak temel yapıyı izler:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-150">Running your app follows the basic structure:</span></span>

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   <span data-ttu-id="1f2c6-151">Şunları çalıştırabilmeniz için bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1f2c6-151">Here are some examples you can run:</span></span>

   * <span data-ttu-id="1f2c6-152">**[Microsoft.Spark.Examples.Sql.Batch. Basit](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="1f2c6-152">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * <span data-ttu-id="1f2c6-153">**[Microsoft. spark. Examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="1f2c6-153">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * <span data-ttu-id="1f2c6-154">**[Microsoft. spark. Examples. Sql. streaming. StructuredKafkaWordCount (Maven erişilebilir)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="1f2c6-154">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * <span data-ttu-id="1f2c6-155">**[Microsoft. spark. Examples. Sql. streaming. StructuredKafkaWordCount (jars sağlanmış)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="1f2c6-155">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
