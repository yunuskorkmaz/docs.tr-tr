---
title: Windows'da Apache Spark uygulaması için bir .NET hata ayıklama
description: Windows'da Apache Spark uygulaması için .NET'inizi nasıl hata ayıklamanız gerektiğini öğrenin.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dac6aed1f7faba7f07b722a6dac0da930ab9ec66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185803"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="dfe6b-103">Apache Spark uygulaması için bir .NET hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dfe6b-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="dfe6b-104">Bu nasıl yapılsa, Windows'taki Apache Spark uygulaması için .NET'inizi hata ayıklamak için adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="dfe6b-105">Uygulamanızda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dfe6b-105">Debug your application</span></span>

<span data-ttu-id="dfe6b-106">Yeni bir komut istemi penceresi açın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dfe6b-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="dfe6b-107">Komutu çalıştırdığınızda, aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="dfe6b-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="dfe6b-108">Hata ayıklama modunda, DotnetRunner .NET uygulamasını başlatmaz, ancak .NET uygulamasını başlatmanızı bekler.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="dfe6b-109">Bu komut istemi penceresini açık bırakın ve .NET uygulamanızı C# hata ayıklama yoluyla başlatın ve uygulamanızı hata ayıkla.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="dfe6b-110">.NET uygulamanızı hata ayıklamak için bir C# hata[ayıklayıcı (Windows/macOS için Visual Studio Debugger](https://visualstudio.microsoft.com/vs/) veya [Visual Studio Code'da C# Debugger Uzantısı)](https://code.visualstudio.com/Docs/editor/debugging)ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="dfe6b-111">Kullanıcı tanımlı işlevin hata ayıklama (UDF)</span><span class="sxs-lookup"><span data-stu-id="dfe6b-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="dfe6b-112">Kullanıcı tanımlı işlevler yalnızca Visual Studio Debugger ile Windows'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="dfe6b-113">Çalıştırmadan `spark-submit`önce, aşağıdaki ortam değişkenini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="dfe6b-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="dfe6b-114">Spark uygulamanızı çalıştırdığınızda, bir `Choose Just-In-Time Debugger` pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="dfe6b-115">Visual Studio hata ayıklama seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="dfe6b-116">Hata ayıklama [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)aşağıdaki konumda kırılır:</span><span class="sxs-lookup"><span data-stu-id="dfe6b-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="dfe6b-117">Hata ayıklamayapmayı planladığınız UDF'yi içeren *.cs* dosyasına gidin ve [bir kesme noktası ayarlayın.](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019)</span><span class="sxs-lookup"><span data-stu-id="dfe6b-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="dfe6b-118">İşçi udf `The breakpoint will not currently be hit` içeren derlemeyi henüz yüklemediğinden, kesme noktası der ki.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="dfe6b-119">Uygulamanızı devam etmek için vurmak `F5` ve kesme noktası sonunda vurulur.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="dfe6b-120">Her görev için Tam Zamanında Hata Ayıklama penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="dfe6b-121">Aşırı açılır pencerelerden kaçınmak için, çalıştırıcı ların sayısını düşük bir sayıya ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="dfe6b-122">Örneğin, tek bir hata ayıklama örneği başlatan görev sayısını 1 olarak ayarlamak için kıvılcım gönderme için **--ana yerel[1]** seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="dfe6b-123">Hata Ayıklama Scala kodu</span><span class="sxs-lookup"><span data-stu-id="dfe6b-123">Debug Scala code</span></span>

<span data-ttu-id="dfe6b-124">Scala yan kodunu`DotnetRunner`(, , `DotnetBackendHandler`vb.) hata ayıklamanız gerekiyorsa, aşağıdaki komutu kullanabilir ve [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme hata ayıklama ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dfe6b-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="dfe6b-125">Komutu çalıştırdıktan sonra, [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklama takın.</span><span class="sxs-lookup"><span data-stu-id="dfe6b-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dfe6b-126">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="dfe6b-126">Next steps</span></span>

* [<span data-ttu-id="dfe6b-127">Apache Spark için .NET ile başlayın</span><span class="sxs-lookup"><span data-stu-id="dfe6b-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="dfe6b-128">Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="dfe6b-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="dfe6b-129">Apache Spark uygulaması için Bir .NET'i Databricks'e dağıtma</span><span class="sxs-lookup"><span data-stu-id="dfe6b-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="dfe6b-130">Amazon EMR Spark'a Apache Spark uygulaması için bir .NET dağıtın</span><span class="sxs-lookup"><span data-stu-id="dfe6b-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
