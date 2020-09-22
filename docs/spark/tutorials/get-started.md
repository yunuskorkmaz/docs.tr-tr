---
title: Apache Spark için .NET ile çalışmaya başlama
description: Windows, macOS ve Ubuntu 'da .NET Core kullanarak Apache Spark uygulaması için .NET çalıştırmayı öğrenin.
ms.date: 09/17/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 7afb35c9d02db1d1ee2bf04d565f79588b00695e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866042"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="48131-103">Öğretici: Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="48131-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="48131-104">Bu öğreticide, Windows, macOS ve Ubuntu 'da .NET Core kullanarak Apache Spark uygulaması için .NET nasıl çalıştırabileceğiniz öğretilir.</span><span class="sxs-lookup"><span data-stu-id="48131-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows, macOS, and Ubuntu.</span></span>

<span data-ttu-id="48131-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="48131-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="48131-106">Apache Spark için ortamınızı .NET için hazırlama</span><span class="sxs-lookup"><span data-stu-id="48131-106">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="48131-107">İlk .NET Apache Spark uygulamanızı yazma</span><span class="sxs-lookup"><span data-stu-id="48131-107">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="48131-108">Apache Spark için .NET uygulamanızı derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="48131-108">Build and run your .NET for Apache Spark application</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="48131-109">Ortamınızı hazırlama</span><span class="sxs-lookup"><span data-stu-id="48131-109">Prepare your environment</span></span>

<span data-ttu-id="48131-110">Uygulamanızı yazmaya başlamadan önce bazı önkoşul bağımlılıklarını ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48131-110">Before you begin writing your app, you need to set up some prerequisite dependencies.</span></span> <span data-ttu-id="48131-111">`dotnet` `java` `spark-shell` Komut satırı ortamınızdan çalıştırırsanız, ortamınız zaten hazırlanmışsa bir sonraki bölüme atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48131-111">If you can run `dotnet`, `java`, `spark-shell` from your command line environment, then your environment is already prepared and you can skip to the next section.</span></span> <span data-ttu-id="48131-112">Komutlardan herhangi birini veya tümünü çalıştırabiliyorsanız, aşağıdaki adımları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="48131-112">If you cannot run any or all of the commands, do the following steps.</span></span>

### <a name="1-install-net"></a><span data-ttu-id="48131-113">1. .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="48131-113">1. Install .NET</span></span>

<span data-ttu-id="48131-114">.NET uygulamaları oluşturmaya başlamak için .NET SDK 'sını (yazılım geliştirme seti) indirmeniz ve yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="48131-114">To start building .NET apps, you need to download and install the .NET SDK (Software Development Kit).</span></span>

<span data-ttu-id="48131-115">[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)indirin ve yükleyin.</span><span class="sxs-lookup"><span data-stu-id="48131-115">Download and install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1).</span></span> <span data-ttu-id="48131-116">SDK 'Yı yüklemek `dotnet` yolunuza toolzincirini ekler.</span><span class="sxs-lookup"><span data-stu-id="48131-116">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span>

<span data-ttu-id="48131-117">.NET Core SDK yükledikten sonra, yeni bir komut istemi veya Terminal açın ve çalıştırın `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="48131-117">Once you've installed the .NET Core SDK, open a new command prompt or terminal and run `dotnet`.</span></span>

<span data-ttu-id="48131-118">Komut çalışır ve DotNet kullanımı hakkında bilgi içeriyorsa, bir sonraki adıma geçebilir.</span><span class="sxs-lookup"><span data-stu-id="48131-118">If the command runs and prints out information about how to use dotnet, can move to the next step.</span></span> <span data-ttu-id="48131-119">Bir `'dotnet' is not recognized as an internal or external command` hata alırsanız, komutu çalıştırmadan önce **Yeni** bir komut istemi veya Terminal açtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="48131-119">If you receive a `'dotnet' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt or terminal before running the command.</span></span>

### <a name="2-install-java"></a><span data-ttu-id="48131-120">2. Java 'Yı Install</span><span class="sxs-lookup"><span data-stu-id="48131-120">2. Install Java</span></span>

<span data-ttu-id="48131-121">Windows ve macOS için [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) veya Ubuntu Için [OpenJDK 8](https://openjdk.java.net/install/) ' i yükler.</span><span class="sxs-lookup"><span data-stu-id="48131-121">Install [Java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) for Windows and macOS, or [OpenJDK 8](https://openjdk.java.net/install/) for Ubuntu.</span></span>

<span data-ttu-id="48131-122">İşletim sisteminiz için uygun sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="48131-122">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="48131-123">Örneğin, bir Windows x64 makinesi için **jdk-8u201-windows-x64.exe** (aşağıda gösterildiği gibi) veya MacOS için **JDK-8u231-macosx-x64. dmg** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="48131-123">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine (as shown below) or **jdk-8u231-macosx-x64.dmg** for macOS.</span></span> <span data-ttu-id="48131-124">Sonra, `java` yüklemeyi doğrulamak için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="48131-124">Then, use the command `java` to verify the installation.</span></span>

![Java Indirme](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a><span data-ttu-id="48131-126">3. sıkıştırma yazılımını yükler</span><span class="sxs-lookup"><span data-stu-id="48131-126">3. Install compression software</span></span>

<span data-ttu-id="48131-127">Apache Spark, sıkıştırılmış. tgz dosyası olarak indirilir.</span><span class="sxs-lookup"><span data-stu-id="48131-127">Apache Spark is downloaded as a compressed .tgz file.</span></span> <span data-ttu-id="48131-128">Dosyayı ayıklamak için [7-zip](https://www.7-zip.org/) veya [WinZip](https://www.winzip.com/)gibi bir ayıklama programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="48131-128">Use an extraction program, like [7-Zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/), to extract the file.</span></span>

### <a name="4-install-apache-spark"></a><span data-ttu-id="48131-129">4. Apache Spark yüklemesi</span><span class="sxs-lookup"><span data-stu-id="48131-129">4. Install Apache Spark</span></span>

<span data-ttu-id="48131-130">[Apache Spark indirin ve yükleyin](https://spark.apache.org/downloads.html).</span><span class="sxs-lookup"><span data-stu-id="48131-130">[Download and install Apache Spark](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="48131-131">2,3. \* veya 2.4.0, 2.4.1, 2.4.3 veya 2.4.4 (.NET Apache Spark Apache Spark diğer sürümleriyle uyumlu değildir) arasından seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48131-131">You'll need to select from version 2.3.\* or 2.4.0, 2.4.1, 2.4.3, or 2.4.4 (.NET for Apache Spark is not compatible with other versions of Apache Spark).</span></span>

<span data-ttu-id="48131-132">Aşağıdaki adımlarda kullanılan komutlar, [2.4.1 Apache Spark indirdiğiniz ve yüklediğiniz](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)varsayılır.</span><span class="sxs-lookup"><span data-stu-id="48131-132">The commands used in the following steps assume you have [downloaded and installed Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz).</span></span> <span data-ttu-id="48131-133">Farklı bir sürüm kullanmak istiyorsanız, **2.4.1** değerini uygun sürüm numarasıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48131-133">If you wish to use a different version, replace **2.4.1** with the appropriate version number.</span></span> <span data-ttu-id="48131-134">Ardından, **. tar** dosyasını ve Apache Spark dosyalarını ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="48131-134">Then, extract the **.tar** file and the Apache Spark files.</span></span>

<span data-ttu-id="48131-135">İç içe geçmiş **. tar** dosyasını ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="48131-135">To extract the nested **.tar** file:</span></span>

* <span data-ttu-id="48131-136">İndirdiğiniz **Spark-2.4.1-bin-Hadoop 2.7. tgz** dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="48131-136">Locate the **spark-2.4.1-bin-hadoop2.7.tgz** file that you downloaded.</span></span>
* <span data-ttu-id="48131-137">Dosyaya sağ tıklayın ve **7-ZIP-> buradan Ayıkla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="48131-137">Right click on the file and select **7-Zip -> Extract here**.</span></span>
* <span data-ttu-id="48131-138">**Spark-2.4.1-bin-Hadoop 2.7. tar** , indirdiğiniz **. tgz** dosyası ile birlikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="48131-138">**spark-2.4.1-bin-hadoop2.7.tar** is created alongside the **.tgz** file you downloaded.</span></span>

<span data-ttu-id="48131-139">Apache Spark dosyalarını ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="48131-139">To extract the Apache Spark files:</span></span>

* <span data-ttu-id="48131-140">**Spark-2.4.1-bin-Hadoop 2.7. tar** öğesine sağ tıklayın ve **7-ZIP-> dosyaları ayıkla ' yı seçin...**</span><span class="sxs-lookup"><span data-stu-id="48131-140">Right-click on **spark-2.4.1-bin-hadoop2.7.tar** and select **7-Zip -> Extract files...**</span></span>
* <span data-ttu-id="48131-141">**Ayıkla** alanına **c:\Bin** yazın.</span><span class="sxs-lookup"><span data-stu-id="48131-141">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="48131-142">**Ayıkla** alanının altındaki onay kutusunun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="48131-142">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="48131-143">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="48131-143">Select **OK**.</span></span>
* <span data-ttu-id="48131-144">Apache Spark dosyaları C:\bin\spark-2.4.1-bin-hadoop2.7\ ' ye ayıklanır</span><span class="sxs-lookup"><span data-stu-id="48131-144">The Apache Spark files are extracted to C:\bin\spark-2.4.1-bin-hadoop2.7\</span></span>

![Spark 'ı yükler](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

<span data-ttu-id="48131-146">Apache Spark bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48131-146">Run the following commands to set the environment variables used to locate Apache Spark.</span></span> <span data-ttu-id="48131-147">Windows 'ta, komut istemi 'ni yönetici modunda çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="48131-147">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="48131-148">Windows</span><span class="sxs-lookup"><span data-stu-id="48131-148">Windows</span></span>](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin"
```

#### <a name="maclinux"></a>[<span data-ttu-id="48131-149">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="48131-149">Mac/Linux</span></span>](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

<span data-ttu-id="48131-150">Her şeyi yükledikten ve ortam değişkenlerinizi ayarladıktan sonra, **Yeni** bir komut istemi veya Terminal açın ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="48131-150">Once you've installed everything and set your environment variables, open a **new** command prompt or terminal and run the following command:</span></span>

```text
spark-submit --version
```

<span data-ttu-id="48131-151">Komut çalışır ve sürüm bilgilerini yazdırıyorsa, sonraki adıma geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48131-151">If the command runs and prints version information, you can move to the next step.</span></span>

<span data-ttu-id="48131-152">Bir `'spark-submit' is not recognized as an internal or external command` hata alırsanız, **Yeni** bir komut istemi açtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="48131-152">If you receive a `'spark-submit' is not recognized as an internal or external command` error, make sure you opened a **new** command prompt.</span></span>

### <a name="5-install-net-for-apache-spark"></a><span data-ttu-id="48131-153">5. Apache Spark için .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="48131-153">5. Install .NET for Apache Spark</span></span>

<span data-ttu-id="48131-154">Apache Spark GitHub için .NET 'ten [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) sürümünü indirin.</span><span class="sxs-lookup"><span data-stu-id="48131-154">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub.</span></span> <span data-ttu-id="48131-155">Örneğin, bir Windows makinesi kullanıyorsanız ve .NET Core 'u kullanmayı planlıyorsanız, [Windows x64 netcoreapp 3.1 sürümünü indirin](https://github.com/dotnet/spark/releases).</span><span class="sxs-lookup"><span data-stu-id="48131-155">For example if you're on a Windows machine and plan to use .NET Core, [download the Windows x64 netcoreapp3.1 release](https://github.com/dotnet/spark/releases).</span></span>

<span data-ttu-id="48131-156">Microsoft. spark. Worker öğesini ayıklamak için:</span><span class="sxs-lookup"><span data-stu-id="48131-156">To extract the Microsoft.Spark.Worker:</span></span>

* <span data-ttu-id="48131-157">İndirdiğiniz **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="48131-157">Locate the **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** file that you downloaded.</span></span>
* <span data-ttu-id="48131-158">Sağ tıklayıp **7-ZIP-> dosyaları ayıkla ' yı seçin...**</span><span class="sxs-lookup"><span data-stu-id="48131-158">Right-click and select **7-Zip -> Extract files...**.</span></span>
* <span data-ttu-id="48131-159">**Ayıkla** alanına **c:\Bin** yazın.</span><span class="sxs-lookup"><span data-stu-id="48131-159">Enter **C:\bin** in the **Extract to** field.</span></span>
* <span data-ttu-id="48131-160">**Ayıkla** alanının altındaki onay kutusunun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="48131-160">Uncheck the checkbox below the **Extract to** field.</span></span>
* <span data-ttu-id="48131-161">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="48131-161">Select **OK**.</span></span>

![.NET Spark 'ı yükler](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a><span data-ttu-id="48131-163">6. WinUtils 'i (yalnızca Windows) yükler</span><span class="sxs-lookup"><span data-stu-id="48131-163">6. Install WinUtils (Windows only)</span></span>

<span data-ttu-id="48131-164">Apache Spark için .NET, Apache Spark birlikte WinUtils 'in yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="48131-164">.NET for Apache Spark requires WinUtils to be installed alongside Apache Spark.</span></span> <span data-ttu-id="48131-165">[winutils.exeindirin ](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span><span class="sxs-lookup"><span data-stu-id="48131-165">[Download winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe).</span></span> <span data-ttu-id="48131-166">Ardından, WinUtils 'ı **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**'e kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="48131-166">Then, copy WinUtils into **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.</span></span>

> [!NOTE]
> <span data-ttu-id="48131-167">Spark install klasörünüzün adının sonunda açıklanan farklı bir Hadoop sürümü kullanıyorsanız, Hadoop sürümünüzle uyumlu olan [WinUtils sürümünü seçin](https://github.com/steveloughran/winutils) .</span><span class="sxs-lookup"><span data-stu-id="48131-167">If you are using a different version of Hadoop, which is annotated at the end of your Spark install folder name, [select the version of WinUtils](https://github.com/steveloughran/winutils) that's compatible with your version of Hadoop.</span></span>

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a><span data-ttu-id="48131-168">7. DOTNET_WORKER_DIR ayarla ve bağımlılıkları denetle</span><span class="sxs-lookup"><span data-stu-id="48131-168">7. Set DOTNET_WORKER_DIR and check dependencies</span></span>

<span data-ttu-id="48131-169">`DOTNET_WORKER_DIR`.NET uygulamaları tarafından Apache Spark .net bulmak için kullanılan ortam değişkenini ayarlamak için aşağıdaki komutlardan birini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="48131-169">Run one of the following commands to set the `DOTNET_WORKER_DIR` environment variable, which is used by .NET apps to locate .NET for Apache Spark.</span></span> <span data-ttu-id="48131-170">`<PATH-DOTNET_WORKER_DIR>`' İ indirdiğiniz ve ayıkladığınız dizinle değiştirdiğinizden emin olun `Microsoft.Spark.Worker` .</span><span class="sxs-lookup"><span data-stu-id="48131-170">Make sure to replace `<PATH-DOTNET_WORKER_DIR>` with the directory where you downloaded and extracted the `Microsoft.Spark.Worker`.</span></span> <span data-ttu-id="48131-171">Windows 'ta, komut istemi 'ni yönetici modunda çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="48131-171">On Windows, make sure to run the command prompt in administrator mode.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="48131-172">Windows</span><span class="sxs-lookup"><span data-stu-id="48131-172">Windows</span></span>](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[<span data-ttu-id="48131-173">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="48131-173">Mac/Linux</span></span>](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

<span data-ttu-id="48131-174">Son olarak, bir `dotnet` `java` `spark-shell` sonraki bölüme geçmeden önce komut satırınızdan, ve ' yi çalıştırıp çalıştırabileceğinizi iki kez kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="48131-174">Finally, double-check that you can run `dotnet`, `java`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="48131-175">Apache Spark uygulaması için .NET yazma</span><span class="sxs-lookup"><span data-stu-id="48131-175">Write a .NET for Apache Spark app</span></span>

### <a name="1-create-a-console-app"></a><span data-ttu-id="48131-176">1. konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="48131-176">1. Create a console app</span></span>

<span data-ttu-id="48131-177">Komut isteminizde veya terminalinizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="48131-177">In your command prompt or terminal, run the following commands to create a new console application:</span></span>

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

<span data-ttu-id="48131-178">`dotnet`Komut `new` sizin için türünde bir uygulama oluşturur `console` .</span><span class="sxs-lookup"><span data-stu-id="48131-178">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="48131-179">`-o`Parametresi, uygulamanızın depolandığı *MySparkApp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur.</span><span class="sxs-lookup"><span data-stu-id="48131-179">The `-o` parameter creates a directory named *MySparkApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="48131-180">`cd MySparkApp`Komut, dizini oluşturduğunuz uygulama dizini olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="48131-180">The `cd MySparkApp` command changes the directory to the app directory you created.</span></span>

### <a name="2-install-nuget-package"></a><span data-ttu-id="48131-181">2. NuGet paketini yükler</span><span class="sxs-lookup"><span data-stu-id="48131-181">2. Install NuGet package</span></span>

<span data-ttu-id="48131-182">.NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="48131-182">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="48131-183">Komut isteminizde veya terminalinizde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="48131-183">In your command prompt or terminal, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> <span data-ttu-id="48131-184">Bu öğretici, `Microsoft.Spark` Aksi belirtilmediği takdirde NuGet paketinin en son sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="48131-184">This tutorial uses the latest version of the `Microsoft.Spark` NuGet package unless otherwise specified.</span></span>

### <a name="3-write-your-app"></a><span data-ttu-id="48131-185">3. uygulamanızı yazma</span><span class="sxs-lookup"><span data-stu-id="48131-185">3. Write your app</span></span>

<span data-ttu-id="48131-186">Visual Studio Code veya herhangi bir metin düzenleyicisinde *program.cs* açın ve kodun tümünü aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="48131-186">Open *Program.cs* in Visual Studio Code, or any text editor, and replace all of the code with the following:</span></span>

```csharp
using Microsoft.Spark.Sql;
using static Microsoft.Spark.Sql.Functions;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create Spark session
            SparkSession spark =
                SparkSession
                    .Builder()
                    .AppName("word_count_sample")
                    .GetOrCreate();

            // Create initial DataFrame
            string filePath = args[0];
            DataFrame dataFrame = spark.Read().Text(filePath);

            //Count words
            DataFrame words =
                dataFrame
                    .Select(Split(Col("value")," ").Alias("words"))
                    .Select(Explode(Col("words")).Alias("word"))
                    .GroupBy("word")
                    .Count()
                    .OrderBy(Col("count").Desc());

            // Display results
            words.Show();

            // Stop Spark session
            spark.Stop();
        }
    }
}
```

<span data-ttu-id="48131-187">[Mini oturum](xref:Microsoft.Spark.Sql.SparkSession) , uygulamanızın bağlamını ve bilgilerini yöneten Apache Spark uygulamaların giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="48131-187">[SparkSession](xref:Microsoft.Spark.Sql.SparkSession) is the entrypoint of Apache Spark applications, which manages the context and information of your application.</span></span> <span data-ttu-id="48131-188">[Metin](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) yöntemini kullanarak, tarafından belirtilen dosyadaki metin verileri `filePath` bir veri [çerçevesine](xref:Microsoft.Spark.Sql.DataFrame)okunurdur.</span><span class="sxs-lookup"><span data-stu-id="48131-188">Using the [Text](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) method, the text data from the file specified by the `filePath` is read into a [DataFrame](xref:Microsoft.Spark.Sql.DataFrame).</span></span> <span data-ttu-id="48131-189">DataFrame, verileri bir adlandırılmış sütunlar kümesiyle düzenlemenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="48131-189">A DataFrame is a way of organizing data into a set of named columns.</span></span> <span data-ttu-id="48131-190">Daha sonra, dosyadaki cümleleri ayırmak için bir dizi dönüştürme uygulanır, sözcüklerin her birini gruplayın, onları Sayın ve azalan sırada sıralayın.</span><span class="sxs-lookup"><span data-stu-id="48131-190">Then, a series of transformations is applied to split the sentences in the file, group each of the words, count them and order them in descending order.</span></span> <span data-ttu-id="48131-191">Bu işlemlerin sonucu, başka bir veri çerçevesinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="48131-191">The result of these operations is stored in another DataFrame.</span></span> <span data-ttu-id="48131-192">Bu noktada, Apache Spark geç için .NET verileri değerlendirirken hiçbir işlem gerçekleşmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="48131-192">Note that at this point, no operations have taken place because .NET for Apache Spark lazily evaluates the data.</span></span> <span data-ttu-id="48131-193">Bu işlem [,](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) `words` dönüştürülmüş veri çerçevesinin içeriğini, yukarıdaki satırlarda tanımlanan işlemleri konsola görüntülemek için olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="48131-193">It's not until the [Show](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) method is called to display the contents of the `words` transformed DataFrame to the console that the operations defined in the lines above execute.</span></span> <span data-ttu-id="48131-194">Spark oturumuna artık gerek kalmadığında, oturumunuzu durdurmak için [stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="48131-194">Once you no longer need the Spark session, use the [Stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) method to stop your session.</span></span>

### <a name="4-create-data-file"></a><span data-ttu-id="48131-195">4. veri dosyası oluştur</span><span class="sxs-lookup"><span data-stu-id="48131-195">4. Create data file</span></span>

<span data-ttu-id="48131-196">Uygulamanız metin satırları içeren bir dosyayı işler.</span><span class="sxs-lookup"><span data-stu-id="48131-196">Your app processes a file containing lines of text.</span></span> <span data-ttu-id="48131-197">*MySparkApp* dizininizde aşağıdaki metni içeren *input.txt* dosyası adlı bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="48131-197">Create a file called *input.txt* file in your *MySparkApp* directory, containing the following text:</span></span>

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

<span data-ttu-id="48131-198">Değişiklikleri kaydedin ve dosyayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="48131-198">Save the changes and close the file.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="48131-199">Apache Spark uygulamanızı .NET için çalıştırın</span><span class="sxs-lookup"><span data-stu-id="48131-199">Run your .NET for Apache Spark app</span></span>

<span data-ttu-id="48131-200">Uygulamanızı derlemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="48131-200">Run the following command to build your application:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="48131-201">Yapı çıkış dizininize gidin ve `spark-submit` uygulamanızı Apache Spark çalışacak şekilde göndermek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="48131-201">Navigate to your build output directory and use the `spark-submit` command to submit your application to run on Apache Spark.</span></span> <span data-ttu-id="48131-202">`<version>`' In .net çalışanınız sürümü ile ve `<path-of-input.txt>` *input.txt* dosyanın yolu ile değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="48131-202">Make sure to replace  `<version>` with the version of your .NET worker and `<path-of-input.txt>` with the path of your *input.txt* file is stored.</span></span>

### <a name="windows"></a>[<span data-ttu-id="48131-203">Windows</span><span class="sxs-lookup"><span data-stu-id="48131-203">Windows</span></span>](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-2.4.x-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[<span data-ttu-id="48131-204">Mac/Linux</span><span class="sxs-lookup"><span data-stu-id="48131-204">Mac/Linux</span></span>](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-2.4.x-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> <span data-ttu-id="48131-205">Bu komut Apache Spark indirdiğinizi ve bunu kullanabilmeniz için PATH ortam değişkenine eklediğinizi varsayar `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="48131-205">This command assumes you have downloaded Apache Spark and added it to your PATH environment variable to be able to use `spark-submit`.</span></span> <span data-ttu-id="48131-206">Aksi takdirde, tam yolu kullanmanız gerekir (örneğin, *C:\bin\apache-spark\bin\spark-Submit* veya *~/Spark/bin/Spark-Submit*).</span><span class="sxs-lookup"><span data-stu-id="48131-206">Otherwise, you'd have to use the full path (for example, *C:\bin\apache-spark\bin\spark-submit* or *~/spark/bin/spark-submit*).</span></span>

<span data-ttu-id="48131-207">Uygulamanız çalıştırıldığında, *input.txt* dosyanın sözcük sayısı verisi konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="48131-207">When your app runs, the word count data of the *input.txt* file is written to the console.</span></span>

```console
+------+-----+
|  word|count|
+------+-----+
|  .NET|    3|
|Apache|    2|
|   app|    2|
|  This|    2|
| Spark|    2|
| World|    1|
|counts|    1|
|   for|    1|
| words|    1|
|  with|    1|
| Hello|    1|
|  uses|    1|
+------+-----+
```

<span data-ttu-id="48131-208">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="48131-208">Congratulations!</span></span> <span data-ttu-id="48131-209">Apache Spark uygulaması için bir .NET başarıyla yazıldı ve çalıştırdınız.</span><span class="sxs-lookup"><span data-stu-id="48131-209">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="48131-210">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="48131-210">Next steps</span></span>

<span data-ttu-id="48131-211">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="48131-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="48131-212">Apache Spark için ortamınızı .NET için hazırlama</span><span class="sxs-lookup"><span data-stu-id="48131-212">Prepare your environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="48131-213">İlk .NET Apache Spark uygulamanızı yazma</span><span class="sxs-lookup"><span data-stu-id="48131-213">Write your first .NET for Apache Spark application</span></span>
> * <span data-ttu-id="48131-214">Apache Spark için .NET uygulamanızı derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="48131-214">Build and run your .NET for Apache Spark application</span></span>

<span data-ttu-id="48131-215">Yukarıdaki adımları açıklayan bir videoyu görmek için, [Apache Spark 101 video serisine yönelik .net](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)' i inceleyin.</span><span class="sxs-lookup"><span data-stu-id="48131-215">To see a video explaining the steps above, check out the [.NET for Apache Spark 101 video series](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).</span></span>

<span data-ttu-id="48131-216">Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.</span><span class="sxs-lookup"><span data-stu-id="48131-216">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="48131-217">Apache Spark kaynakları için .NET</span><span class="sxs-lookup"><span data-stu-id="48131-217">.NET for Apache Spark Resources</span></span>](../resources/index.md)
