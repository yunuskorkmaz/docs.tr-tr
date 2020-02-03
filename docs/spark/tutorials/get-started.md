---
title: Apache Spark için .NET ile çalışmaya başlama
description: Windows 'da .NET Core kullanarak Apache Spark uygulaması için .NET çalıştırmayı öğrenin.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 679ee7660e96504768a781e1e384acab80362736
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743208"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="4c17d-103">Öğretici: Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="4c17d-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="4c17d-104">Bu öğreticide, Windows 'da .NET Core kullanarak Apache Spark bir uygulama için nasıl bir .NET çalıştırılacağı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="4c17d-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="4c17d-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4c17d-106">.NET için Windows ortamınızı Apache Spark için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="4c17d-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="4c17d-107">İlk .NET Apache Spark uygulamanızı yazma</span><span class="sxs-lookup"><span data-stu-id="4c17d-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="4c17d-108">Apache Spark uygulamanızı basit .NET için derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4c17d-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="4c17d-109">Ortamınızı hazırlama</span><span class="sxs-lookup"><span data-stu-id="4c17d-109">Prepare your environment</span></span>

<span data-ttu-id="4c17d-110">Uygulamanızı yazmaya başlamadan önce bazı önkoşul bağımlılıklarını ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="4c17d-111">Komut satırı ortamınızdan `dotnet`, `java`, `mvn``spark-shell` çalıştırabiliyorsanız, ortamınız zaten hazırlanmışsa ve sonraki bölüme atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c17d-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="4c17d-112">Komutlardan herhangi birini veya tümünü çalıştırabiliyorsanız, aşağıdaki adımları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="4c17d-113">1. .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="4c17d-113">1. Install .NET</span></span>

<span data-ttu-id="4c17d-114">.NET uygulamaları oluşturmaya başlamak için .NET SDK 'sını (yazılım geliştirme seti) indirmeniz ve yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="4c17d-115">[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0)indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span> <span data-ttu-id="4c17d-116">SDK yükleme, yolunuza `dotnet` toolzincirini ekler.</span><span class="sxs-lookup"><span data-stu-id="4c17d-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="4c17d-117">.NET Core SDK yükledikten sonra, yeni bir komut istemi açın ve `dotnet`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-117">Once you've installed the .NET Core SDK, open a new command prompt and run `dotnet`.</span></span>

<span data-ttu-id="4c17d-118">Komut çalışır ve DotNet kullanımı hakkında bilgi içeriyorsa, bir sonraki adıma geçebilir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="4c17d-119">`'dotnet' is not recognized as an internal or external command` hatası alırsanız, komutu çalıştırmadan önce **Yeni** bir komut istemi açtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4c17d-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="4c17d-120">2. Java 'Yı Install</span><span class="sxs-lookup"><span data-stu-id="4c17d-120">2. Install Java</span></span>

<span data-ttu-id="4c17d-121">[Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)' i yükler.</span><span class="sxs-lookup"><span data-stu-id="4c17d-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

<span data-ttu-id="4c17d-122">İşletim sisteminiz için uygun sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="4c17d-123">Örneğin, bir Windows x64 makinesi için **JDK-8u201-Windows-x64. exe** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span> <span data-ttu-id="4c17d-124">Ardından, yüklemeyi doğrulamak için `java` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-124">Then, use the command `java` to verify the installation.</span></span>

![Java Indirme](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a><span data-ttu-id="4c17d-126">3.7-zip ' i yükler</span><span class="sxs-lookup"><span data-stu-id="4c17d-126">3. Install 7-zip</span></span>

<span data-ttu-id="4c17d-127">Apache Spark, sıkıştırılmış. tgz dosyası olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="4c17d-128">Dosyayı ayıklamak için 7-zip gibi bir ayıklama programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-128">Use an extraction program, like 7-zip, to extract the file.</span></span>

* <span data-ttu-id="4c17d-129">[7 ZIP indiriyi](https://www.7-zip.org/)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-129">Visit [7-Zip downloads](https://www.7-zip.org/).</span></span>
* <span data-ttu-id="4c17d-130">Sayfadaki ilk tabloda, işletim sisteminize bağlı olarak 32 bit x86 veya 64 bit x64 indirmeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-130">In the first table on the page, select the 32-bit x86 or 64-bit x64 download, depending on your operating system.</span></span>
* <span data-ttu-id="4c17d-131">Yükleme tamamlandığında, yükleyiciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-131">When the download completes, run the installer.</span></span>

![7Zip Indir](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a><span data-ttu-id="4c17d-133">4. Apache Spark yüklemesi</span><span class="sxs-lookup"><span data-stu-id="4c17d-133">4. Install Apache Spark</span></span>

<span data-ttu-id="4c17d-134">[Apache Spark indirin ve yükleyin](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="4c17d-134">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="4c17d-135">2,3. \* veya 2.4.0, 2.4.1, 2.4.3 veya 2.4.4 (.NET Apache Spark Apache Spark diğer sürümleriyle uyumlu değildir) arasından seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-135">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="4c17d-136">Aşağıdaki adımlarda kullanılan komutlar, [2.4.1 Apache Spark indirdiğiniz ve yüklediğiniz](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4c17d-136">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="4c17d-137">Farklı bir sürüm kullanmak istiyorsanız, **2.4.1** değerini uygun sürüm numarasıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-137">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="4c17d-138">Ardından, **. tar** dosyasını ve Apache Spark dosyalarını ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-138">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="4c17d-139">İç içe geçmiş **. tar** dosyasını ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="4c17d-139">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="4c17d-140">İndirdiğiniz **Spark-2.4.1-bin-Hadoop 2.7. tgz** dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="4c17d-140">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="4c17d-141">Dosyaya sağ tıklayın ve **7-ZIP-> buradan Ayıkla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-141">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="4c17d-142">**Spark-2.4.1-bin-Hadoop 2.7. tar** , indirdiğiniz **. tgz** dosyası ile birlikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4c17d-142">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="4c17d-143">Apache Spark dosyalarını ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="4c17d-143">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="4c17d-144">**Spark-2.4.1-bin-Hadoop 2.7. tar** öğesine sağ tıklayın ve **7-ZIP-> dosyaları ayıkla ' yı seçin...**</span><span class="sxs-lookup"><span data-stu-id="4c17d-144">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="4c17d-145">**Ayıkla** alanına **c:\Bin** yazın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-145">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="4c17d-146">**Ayıkla** alanının altındaki onay kutusunun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-146">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="4c17d-147">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-147">Select **OK**.</span></span>
* <span data-ttu-id="4c17d-148">Apache Spark dosyaları C:\bin\spark-2.4.1-bin-hadoop2.7\ ' ye ayıklanır</span><span class="sxs-lookup"><span data-stu-id="4c17d-148">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7\</span></span>

![Spark 'ı yükler](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="4c17d-150">Apache Spark bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c17d-150">Run the following commands to set the environment variables used to locate Apache Spark:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="4c17d-151">Her şeyi yükledikten ve ortam değişkenlerinizi ayarladıktan sonra, **Yeni** bir komut istemi açın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c17d-151">Once you've installed everything and set your environment variables, open a **new** command prompt and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="4c17d-152">Komut çalışır ve sürüm bilgilerini yazdırıyorsa, sonraki adıma geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c17d-152">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="4c17d-153">`'spark-submit' is not recognized as an internal or external command` bir hata alırsanız, **Yeni** bir komut istemi açtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4c17d-153">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="4c17d-154">5. Apache Spark için .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="4c17d-154">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="4c17d-155">Apache Spark GitHub için .NET 'ten [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) sürümünü indirin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-155">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="4c17d-156">Örneğin, bir Windows makinesi kullanıyorsanız ve .NET Core 'u kullanmayı planlıyorsanız, [Windows x64 netcoreapp 2.1 sürümünü indirin](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span><span class="sxs-lookup"><span data-stu-id="4c17d-156">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp2.1 release](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).</span></span>

<span data-ttu-id="4c17d-157">Microsoft. spark. Worker öğesini ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="4c17d-157">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="4c17d-158">İndirdiğiniz **Microsoft. spark. Worker. netcoreapp 2.1. Win-x64-0.6.0. zip** dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="4c17d-158">Locate the **Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="4c17d-159">Sağ tıklayıp **7 ZIP-> dosyaları ayıkla ' yı seçin...**</span><span class="sxs-lookup"><span data-stu-id="4c17d-159">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="4c17d-160">**Ayıkla** alanına **c:\Bin** yazın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-160">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="4c17d-161">**Ayıkla** alanının altındaki onay kutusunun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-161">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="4c17d-162">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-162">Select **OK**.</span></span>

![.NET Spark 'ı yükler](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a><span data-ttu-id="4c17d-164">6. WinUtils 'i yükler</span><span class="sxs-lookup"><span data-stu-id="4c17d-164">6. Install WinUtils</span></span>

<span data-ttu-id="4c17d-165">Apache Spark için .NET, Apache Spark birlikte WinUtils 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-165">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="4c17d-166">[Winutils. exe dosyasını indirin](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="4c17d-166">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="4c17d-167">Ardından, WinUtils 'ı **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**'e kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-167">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="4c17d-168">Spark install klasörünüzün adının sonunda açıklanan farklı bir Hadoop sürümü kullanıyorsanız, Hadoop sürümünüzle uyumlu olan [WinUtils sürümünü seçin](https://github.com/steveloughran/winutils) .</span><span class="sxs-lookup"><span data-stu-id="4c17d-168">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="4c17d-169">7. DOTNET_WORKER_DIR ayarla ve bağımlılıkları denetle</span><span class="sxs-lookup"><span data-stu-id="4c17d-169">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="4c17d-170">.NET uygulamaları tarafından Apache Spark .NET konumunu bulmak üzere kullanılan `DOTNET_WORKER_DIR` ortam değişkenini ayarlamak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c17d-170">Run the following command to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark:</span></span>

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

<span data-ttu-id="4c17d-171">Son olarak, bir sonraki bölüme geçmeden önce komut satırınızdan `dotnet`, `java`, `mvn``spark-shell` çalıştırıp çalıştırabileceğinizi iki kez kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="4c17d-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="4c17d-172">Apache Spark uygulaması için .NET yazma</span><span class="sxs-lookup"><span data-stu-id="4c17d-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="4c17d-173">1. konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c17d-173">1. Create a console app</span></span>

<span data-ttu-id="4c17d-174">Komut istemindeki yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c17d-174">In your command prompt, run the following commands to create a new console application:</span></span>

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="4c17d-175">`dotnet` komutu sizin için `console` türünde bir `new` uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c17d-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="4c17d-176">`-o` parametresi, uygulamanızın depolandığı *mySparkApp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="4c17d-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="4c17d-177">`cd mySparkApp` komutu, dizini yeni oluşturduğunuz uygulama diziniyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4c17d-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="4c17d-178">2. NuGet paketini yükler</span><span class="sxs-lookup"><span data-stu-id="4c17d-178">2. Install NuGet package</span></span>

<span data-ttu-id="4c17d-179">.NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="4c17d-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="4c17d-180">Komut isteminde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c17d-180">In your command prompt, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a><span data-ttu-id="4c17d-181">3. uygulamanızı kodlayın</span><span class="sxs-lookup"><span data-stu-id="4c17d-181">3. Code your app</span></span>

<span data-ttu-id="4c17d-182">Visual Studio Code veya herhangi bir metin düzenleyicisinde *program.cs* açın ve kodun tümünü aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="4c17d-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-add-data-file"></a><span data-ttu-id="4c17d-183">4. veri dosyası Ekle</span><span class="sxs-lookup"><span data-stu-id="4c17d-183">4. Add data file</span></span>

<span data-ttu-id="4c17d-184">Uygulamanız metin satırları içeren bir dosyayı işler.</span><span class="sxs-lookup"><span data-stu-id="4c17d-184">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="4c17d-185">*MySparkApp* dizininizde aşağıdaki metni içeren bir *input. txt* dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4c17d-185">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="4c17d-186">Apache Spark uygulamanızı .NET için çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4c17d-186">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="4c17d-187">Uygulamanızı derlemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c17d-187">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="4c17d-188">Apache Spark üzerinde çalışacak uygulamanızı göndermek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4c17d-188">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. <span data-ttu-id="4c17d-189">Uygulamanız çalıştırıldığında, *Input. txt* dosyasının sözcük sayısı verisi konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="4c17d-189">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="4c17d-190">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="4c17d-190">Congratulations!</span></span> <span data-ttu-id="4c17d-191">Apache Spark uygulaması için bir .NET başarıyla yazıldı ve çalıştırdınız.</span><span class="sxs-lookup"><span data-stu-id="4c17d-191">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4c17d-192">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4c17d-192">Next steps</span></span>

<span data-ttu-id="4c17d-193">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="4c17d-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4c17d-194">.NET için Windows ortamınızı Apache Spark için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="4c17d-194">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="4c17d-195">İlk .NET Apache Spark uygulamanızı yazma</span><span class="sxs-lookup"><span data-stu-id="4c17d-195">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="4c17d-196">Apache Spark uygulamanızı basit .NET için derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4c17d-196">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="4c17d-197">Yukarıdaki adımları açıklayan bir videoyu görmek için, [Apache Spark 101 video serisi için .net](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)'i kullanıma alın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-197">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="4c17d-198">Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.</span><span class="sxs-lookup"><span data-stu-id="4c17d-198">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4c17d-199">Apache Spark kaynakları için .NET</span><span class="sxs-lookup"><span data-stu-id="4c17d-199">.NET for Apache Spark Resources</span></span>](../resources/index.md)
