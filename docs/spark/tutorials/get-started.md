---
title: Apache Spark için .NET ile başlayın
description: Windows, MacOS ve Ubuntu'da .NET Core'u kullanarak Apache Spark uygulaması için bir .NET'in nasıl çalıştırılabildiğini keşfedin.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187540"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="51e42-103">Öğretici: Apache Spark için .NET ile başlayın</span><span class="sxs-lookup"><span data-stu-id="51e42-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="51e42-104">Bu öğretici, Windows, MacOS ve Ubuntu'da .NET Core'u kullanarak Apache Spark için bir .NET uygulamasını nasıl çalıştırabileceğinizi öğretir.</span><span class="sxs-lookup"><span data-stu-id="51e42-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, MacOS, and Ubuntu.</span></span>

<span data-ttu-id="51e42-105">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="51e42-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="51e42-106">Apache Spark için ortamınızı .NET'e hazırlayın</span><span class="sxs-lookup"><span data-stu-id="51e42-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="51e42-107">Apache Spark uygulaması için ilk .NET'inizi yazın</span><span class="sxs-lookup"><span data-stu-id="51e42-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="51e42-108">Apache Spark uygulaması için basit .NET'inizi oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="51e42-108">Build and run your simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="51e42-109">Ortamınızı hazırlama</span><span class="sxs-lookup"><span data-stu-id="51e42-109">Prepare your environment</span></span>

<span data-ttu-id="51e42-110">Uygulamanızı yazmaya başlamadan önce bazı ön koşul bağımlılıkları ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51e42-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="51e42-111">Komut satırı `dotnet`ortamınızdan `mvn` `spark-shell` , , , `java`çalıştırabiliyorsanız, ortamınız zaten hazırlanmıştır ve bir sonraki bölüme atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e42-111">If you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="51e42-112">Komutların hiçbirini veya tamamını çalıştıramıyorsanız, aşağıdaki adımları yapın.</span><span class="sxs-lookup"><span data-stu-id="51e42-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="51e42-113">1. Yükleyin .NET</span><span class="sxs-lookup"><span data-stu-id="51e42-113">1. Install .NET</span></span>

<span data-ttu-id="51e42-114">.NET uygulamaları oluşturmaya başlamak için .NET SDK'yı (Yazılım Geliştirme Kiti) indirmeniz ve yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="51e42-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="51e42-115">[.NET Core SDK'yı](https://dotnet.microsoft.com/download/dotnet-core/3.1)indirin ve kurun.</span><span class="sxs-lookup"><span data-stu-id="51e42-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="51e42-116">SDK'nın yüklenmesi, araç zincirini `dotnet` PATH'inize ekler.</span><span class="sxs-lookup"><span data-stu-id="51e42-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="51e42-117">.NET Core SDK'yı yükledikten sonra, yeni bir komut `dotnet`istemi veya terminal açın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="51e42-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="51e42-118">Komut çalışır ve dotnet nasıl kullanılacağı hakkında bilgi yazdırırsa, bir sonraki adıma taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e42-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="51e42-119">Bir `'dotnet' is not recognized as an internal or external command` hata alırsanız, komutu çalıştırmadan önce **yeni** bir komut istemi veya terminal açtığınıza emin olun.</span><span class="sxs-lookup"><span data-stu-id="51e42-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="51e42-120">2. Java Yükle</span><span class="sxs-lookup"><span data-stu-id="51e42-120">2. Install Java</span></span>

<span data-ttu-id="51e42-121">Windows ve MacOS için [Java 8.1'i](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) veya Ubuntu için [OpenJDK 8'i](https://openjdk.java.net/install/) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="51e42-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and MacOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="51e42-122">İşletim sisteminiz için uygun sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="51e42-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="51e42-123">Örneğin, windows x64 makinesi için **jdk-8u201-windows-x64.exe** veya MacOS için **jdk-8u231-macosx-x64.dmg'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="51e42-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for MacOS.</span></span> <span data-ttu-id="51e42-124">Ardından, yüklemeyi `java` doğrulamak için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="51e42-124">Then, use the command `java` to verify the installation.</span></span>

![Java İndir](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="51e42-126">3. Sıkıştırma yazılımı yükleyin</span><span class="sxs-lookup"><span data-stu-id="51e42-126">3. Install compression software</span></span>

<span data-ttu-id="51e42-127">Apache Spark sıkıştırılmış .tgz dosyası olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="51e42-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="51e42-128">Dosyayı ayıklamak için [7-Zip](https://www.7-zip.org/) veya [WinZip](https://www.winzip.com/)gibi bir çıkarma programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="51e42-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="51e42-129">4. Apache Spark yükleyin</span><span class="sxs-lookup"><span data-stu-id="51e42-129">4. Install Apache Spark</span></span>

<span data-ttu-id="51e42-130">[Apache Spark'ı indirin ve kurun.](https://spark.apache.org/downloads.html)</span><span class="sxs-lookup"><span data-stu-id="51e42-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="51e42-131">Sürüm 2.3.\* veya 2.4.0, 2.4.1, 2.4.3 veya 2.4.4 (.NET for Apache Spark'ın diğer sürümleriyle uyumlu değildir) arasından seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="51e42-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="51e42-132">Aşağıdaki adımlarda kullanılan komutlar, [Apache Spark 2.4.1'i indirdiğinizi ve yüklediğinizi](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)varsayar.</span><span class="sxs-lookup"><span data-stu-id="51e42-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="51e42-133">Farklı bir sürüm kullanmak istiyorsanız, **2.4.1'i** uygun sürüm numarasıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="51e42-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="51e42-134">**Ardından,.katran** dosyasını ve Apache Spark dosyalarını ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="51e42-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="51e42-135">İç içe **.katran** dosyasını ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="51e42-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="51e42-136">İndirdiğiniz **kıvılcım-2.4.1-bin-hadoop2.7.tgz** dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="51e42-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="51e42-137">Dosyaya sağ tıklayın ve **burada 7-Zip -> Extract**seçin.</span><span class="sxs-lookup"><span data-stu-id="51e42-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="51e42-138">**spark-2.4.1-bin-hadoop2.7.tar** indirdiğiniz **.tgz** dosyasının yanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="51e42-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="51e42-139">Apache Spark dosyalarını ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="51e42-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="51e42-140">Sağ tıklayın **spark-2.4.1-bin-hadoop2.7.tar** ve seçin **7-Zip -> Extract dosyaları...**</span><span class="sxs-lookup"><span data-stu-id="51e42-140">Right click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="51e42-141">**Alana Ekstre'ye** **C:\bin** girin.</span><span class="sxs-lookup"><span data-stu-id="51e42-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="51e42-142">Alana Ekstresinin altındaki onay kutusunun **işaretini** kaldırın.</span><span class="sxs-lookup"><span data-stu-id="51e42-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="51e42-143">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="51e42-143">Select **OK**.</span></span>
* <span data-ttu-id="51e42-144">Apache Kıvılcım dosyaları C:\bin\spark-2.4.1-bin-hadoop2.7</span><span class="sxs-lookup"><span data-stu-id="51e42-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7</span></span>\

![Kıvılcım Yükle](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="51e42-146">**Windows'da**Apache Spark'ı bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51e42-146">Run the following commands to set the environment variables used to locate Apache Spark on **Windows**:</span></span>

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

<span data-ttu-id="51e42-147">**MacOS** ve **Ubuntu'da**Apache Spark'ı bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51e42-147">Run the following commands to set the environment variables used to locate Apache Spark on **MacOS** and **Ubuntu**:</span></span>

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

<span data-ttu-id="51e42-148">Her şeyi yükledikten ve ortam değişkenlerinizi ayarladıktan **sonra, yeni** bir komut istemi veya terminal açın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51e42-148">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

`%SPARK_HOME%\bin\spark-submit --version`

<span data-ttu-id="51e42-149">Komut sürüyor ve sürüm bilgilerini yazdırıyorsa, bir sonraki adıma geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51e42-149">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="51e42-150">Bir `'spark-submit' is not recognized as an internal or external command` hata alırsanız, **yeni** bir komut istemi açtığınıza emin olun.</span><span class="sxs-lookup"><span data-stu-id="51e42-150">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="51e42-151">5. Apache Spark için .NET yükle</span><span class="sxs-lookup"><span data-stu-id="51e42-151">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="51e42-152">Apache Spark GitHub için .NET'ten [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) sürümünden indirin.</span><span class="sxs-lookup"><span data-stu-id="51e42-152">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="51e42-153">Örneğin bir Windows makinesindeyseniz ve .NET Core'u kullanmayı planlıyorsanız, [Windows x64 netcoreapp3.1 sürümünden yararlanın.](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip)</span><span class="sxs-lookup"><span data-stu-id="51e42-153">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).</span></span>

<span data-ttu-id="51e42-154">Microsoft.Spark.Worker ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="51e42-154">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="51e42-155">İndirdiğiniz **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="51e42-155">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="51e42-156">Sağ tıklayın ve **7-Zip -> Extract dosyaları seçin...**.</span><span class="sxs-lookup"><span data-stu-id="51e42-156">Right click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="51e42-157">**Alana Ekstre'ye** **C:\bin** girin.</span><span class="sxs-lookup"><span data-stu-id="51e42-157">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="51e42-158">Alana Ekstresinin altındaki onay kutusunun **işaretini** kaldırın.</span><span class="sxs-lookup"><span data-stu-id="51e42-158">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="51e42-159">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="51e42-159">Select **OK**.</span></span>

![Yükle .NET Kıvılcım](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="51e42-161">6. WinUtils'i yükleyin (yalnızca Windows)</span><span class="sxs-lookup"><span data-stu-id="51e42-161">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="51e42-162">.NET Apache Spark için WinUtils Apache Spark yanında yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51e42-162">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="51e42-163">[Karşıdan yükleme winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="51e42-163">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="51e42-164">Sonra WinUtils'i **C:\bin\spark-2.4.1-bin-hadoop2.7\bin'e**kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="51e42-164">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="51e42-165">Spark yükleme klasör adının sonunda açıklamalı hadoop'un farklı bir sürümünü kullanıyorsanız, Hadoop sürümünüzle uyumlu [WinUtils sürümünü seçin.](https://github.com/steveloughran/winutils)</span><span class="sxs-lookup"><span data-stu-id="51e42-165">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="51e42-166">7. DOTNET_WORKER_DIR ayarlayın ve bağımlılıkları kontrol edin</span><span class="sxs-lookup"><span data-stu-id="51e42-166">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="51e42-167">Apache Spark için .NET'i bulmak için .NET uygulamaları tarafından kullanılan `DOTNET_WORKER_DIR` Çevre Değişkenini ayarlamak için aşağıdaki komutlardan birini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="51e42-167">Run one of the following commands to set the `DOTNET_WORKER_DIR` Environment Variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span>

<span data-ttu-id="51e42-168">Windows'da, yeni bir [ortam değişkeni](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` oluşturun ve Microsoft.Spark.Worker'ı indirip ayıkladığınız `C:\bin\Microsoft.Spark.Worker\`dizine ayarlayın (örneğin, ). **Windows**</span><span class="sxs-lookup"><span data-stu-id="51e42-168">On **Windows**, create a [new environment variable](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, `C:\bin\Microsoft.Spark.Worker\`).</span></span>

<span data-ttu-id="51e42-169">**MacOS'ta,** Microsoft.Spark.Worker'ı indirip ayıkladığınız dizine (örneğin `export DOTNET_WORKER_DIR <your_path>` *~/bin/Microsoft.Spark.Worker/ )* kullanarak yeni bir ortam değişkeni oluşturun ve ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="51e42-169">On **MacOS**, create a new environment variable using `export DOTNET_WORKER_DIR <your_path>` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker/*).</span></span>

<span data-ttu-id="51e42-170">**Ubuntu'da,** yeni bir [ortam değişkeni](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` oluşturun ve Microsoft.Spark.Worker'ı indirip ayıkladığınız dizine ayarlayın (örneğin, *~/bin/Microsoft.Spark.Worker).*</span><span class="sxs-lookup"><span data-stu-id="51e42-170">On **Ubuntu**, create a [new environment variable](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the Microsoft.Spark.Worker (for example, *~/bin/Microsoft.Spark.Worker*).</span></span>

<span data-ttu-id="51e42-171">Son olarak, bir sonraki bölüme `mvn` `spark-shell` geçmeden önce komut satırınızdan , , , `dotnet` `java`çalıştırabileceğinizi iki kez kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="51e42-171">Finally, double-check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="51e42-172">Apache Spark uygulaması için bir .NET yazın</span><span class="sxs-lookup"><span data-stu-id="51e42-172">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="51e42-173">1. Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="51e42-173">1. Create a console app</span></span>

<span data-ttu-id="51e42-174">Komut istemi veya terminalinizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51e42-174">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

<span data-ttu-id="51e42-175">Komut `dotnet` sizin için `new` bir `console` tür uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51e42-175">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="51e42-176">Parametre, `-o` uygulamanızın depolandığı *mySparkApp* adında bir dizin oluşturur ve gerekli dosyalarla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="51e42-176">The `-o` parameter creates a directory named *mySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="51e42-177">Komut, `cd mySparkApp` dizini yeni oluşturduğunuz uygulama dizinine değiştirir.</span><span class="sxs-lookup"><span data-stu-id="51e42-177">The `cd mySparkApp` command changes the directory to the app directory you just created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="51e42-178">2. NuGet paketini yükleyin</span><span class="sxs-lookup"><span data-stu-id="51e42-178">2. Install NuGet package</span></span>

<span data-ttu-id="51e42-179">Bir uygulamada Apache Spark için .NET'i kullanmak için Microsoft.Spark paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="51e42-179">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="51e42-180">Komut istemiveya terminalinizde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51e42-180">In your command prompt or terminal, run the following command:</span></span>

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a><span data-ttu-id="51e42-181">3. Uygulamanızı kodlayın</span><span class="sxs-lookup"><span data-stu-id="51e42-181">3. Code your app</span></span>

<span data-ttu-id="51e42-182">Visual Studio Code veya herhangi bir metin düzenleyicisinde *Program.cs* açın ve kodun tümünün yerine aşağıdakileri girin:</span><span class="sxs-lookup"><span data-stu-id="51e42-182">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
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

### <a name="4-create-and-add-a-data-file"></a><span data-ttu-id="51e42-183">4. Veri dosyası oluşturma ve ekleme</span><span class="sxs-lookup"><span data-stu-id="51e42-183">4. Create and add a data file</span></span>

<span data-ttu-id="51e42-184">Komut isteminizi veya terminalinizi açın ve uygulama klasörünüze gidin.</span><span class="sxs-lookup"><span data-stu-id="51e42-184">Open your command prompt or terminal and navigate into your app folder.</span></span>

```bash
cd <your-app-output-directory>
```

<span data-ttu-id="51e42-185">Uygulamanız metin satırları içeren bir dosyayı işler.</span><span class="sxs-lookup"><span data-stu-id="51e42-185">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="51e42-186">*mySparkApp* dizininde aşağıdaki metni içeren bir *giriş.txt* dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="51e42-186">Create an *input.txt* file in your *mySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="51e42-187">Apache Spark uygulaması için .NET'inizi çalıştırın</span><span class="sxs-lookup"><span data-stu-id="51e42-187">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="51e42-188">Uygulamanızı oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51e42-188">Run the following command to build your application:</span></span>

   ```dotnetcli
   dotnet build
   ```

2. <span data-ttu-id="51e42-189">Apache Spark'ta çalışmak üzere başvurunuzu göndermek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="51e42-189">Run the following command to submit your application to run on Apache Spark:</span></span>

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > <span data-ttu-id="51e42-190">Bu komut, Apache Spark'ı indirdiğinizi ve kullanabilmek `spark-submit`için PATH ortamı değişkeninize eklediğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="51e42-190">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="51e42-191">Aksi takdirde, tam yolu kullanmanız gerekir (örneğin, *C:\bin\apache-spark\bin\spark-gönder* veya *~/kıvılcım/bin/spark-gönder).*</span><span class="sxs-lookup"><span data-stu-id="51e42-191">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

3. <span data-ttu-id="51e42-192">Uygulamanız çalıştığında, *input.txt* dosyasının sözcük sayısı verileri konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="51e42-192">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

<span data-ttu-id="51e42-193">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="51e42-193">Congratulations!</span></span> <span data-ttu-id="51e42-194">Apache Spark uygulaması için bir .NET'i başarıyla yazıp çalıştırdın.</span><span class="sxs-lookup"><span data-stu-id="51e42-194">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51e42-195">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="51e42-195">Next steps</span></span>

<span data-ttu-id="51e42-196">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="51e42-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="51e42-197">Windows ortamınızı Apache Spark için .NET'e hazırlayın</span><span class="sxs-lookup"><span data-stu-id="51e42-197">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="51e42-198">Apache Spark uygulaması için ilk .NET'inizi yazın</span><span class="sxs-lookup"><span data-stu-id="51e42-198">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="51e42-199">Apache Spark uygulaması için basit .NET'inizi oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="51e42-199">Build and run your simple .NET for Apache Spark application</span></span>

<span data-ttu-id="51e42-200">Yukarıdaki adımları açıklayan bir video görmek [için, Apache Spark 101 video serisi için .NET](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)çıkış.</span><span class="sxs-lookup"><span data-stu-id="51e42-200">To see a video explaining the steps above, checkout the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="51e42-201">Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.</span><span class="sxs-lookup"><span data-stu-id="51e42-201">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="51e42-202">.NET Apache Spark Kaynakları için</span><span class="sxs-lookup"><span data-stu-id="51e42-202">.NET for Apache Spark Resources</span></span>](../resources/index.md)
