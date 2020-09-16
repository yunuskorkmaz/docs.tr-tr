---
title: Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama
description: Windows 'da Apache Spark için .NET uygulamanızı nasıl ayıklayacağınızı öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 249b4bccbf1378d8ef8c824f39151c33fb9f875a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557157"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="18ba7-103">Apache Spark uygulama için bir .NET hatası ayıklama</span><span class="sxs-lookup"><span data-stu-id="18ba7-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="18ba7-104">Bu nasıl yapılır, Windows 'da Apache Spark için .NET uygulamanızı hata ayıklama adımlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="18ba7-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a><span data-ttu-id="18ba7-105">Uygulamanızda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="18ba7-105">Debug your application</span></span>

<span data-ttu-id="18ba7-106">Yeni bir komut istemi penceresi açın ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="18ba7-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="18ba7-107">Komutu çalıştırdığınızda aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="18ba7-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="18ba7-108">Hata ayıklama modunda, DotnetRunner .NET uygulamasını başlatmaz, bunun yerine .NET uygulamasını başlatmanız için bekler.</span><span class="sxs-lookup"><span data-stu-id="18ba7-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="18ba7-109">Uygulamanızda hata ayıklamak için bu komut istemi penceresini açık bırakın ve C# hata ayıklayıcısı aracılığıyla .NET uygulamanızı başlatın.</span><span class="sxs-lookup"><span data-stu-id="18ba7-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="18ba7-110">Uygulamanızda hata ayıklamak için bir C# hata ayıklayıcı ([Windows/macOS Için Visual Studio hata ayıklayıcı](https://visualstudio.microsoft.com/vs/) veya [C# hata ayıklayıcı uzantısı Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) ile .NET uygulamanızı başlatın.</span><span class="sxs-lookup"><span data-stu-id="18ba7-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="18ba7-111">Kullanıcı tanımlı bir işlevde hata ayıklama (UDF)</span><span class="sxs-lookup"><span data-stu-id="18ba7-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="18ba7-112">Kullanıcı tanımlı işlevler yalnızca Visual Studio hata ayıklayıcı ile Windows 'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="18ba7-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="18ba7-113">Çalıştırmadan önce `spark-submit` Aşağıdaki ortam değişkenini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="18ba7-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="18ba7-114">Spark uygulamanızı çalıştırdığınızda bir `Choose Just-In-Time Debugger` pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="18ba7-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="18ba7-115">Bir Visual Studio hata ayıklayıcısı seçin.</span><span class="sxs-lookup"><span data-stu-id="18ba7-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="18ba7-116">Hata ayıklayıcı [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)içinde aşağıdaki konumda kesilir:</span><span class="sxs-lookup"><span data-stu-id="18ba7-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="18ba7-117">Hata ayıklamayı planladığınız UDF 'yi içeren *. cs* dosyasına gidin ve [bir kesme noktası ayarlayın](/visualstudio/debugger/using-breakpoints?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="18ba7-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="18ba7-118">`The breakpoint will not currently be hit`Çalışan, UDF içeren derlemeyi henüz yüklememediği için kesme noktası olacaktır.</span><span class="sxs-lookup"><span data-stu-id="18ba7-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="18ba7-119">`F5`Uygulamanıza devam etmek için isabet, sonunda kesme noktasına ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="18ba7-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="18ba7-120">Tam zamanında hata ayıklayıcı Seç penceresi her bir görev için açılır.</span><span class="sxs-lookup"><span data-stu-id="18ba7-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="18ba7-121">Aşırı açılan pencerelerin olmaması için, yürüticilerinin sayısını düşük bir sayı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="18ba7-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="18ba7-122">Örneğin, tek bir hata ayıklayıcı örneği başlatan görev sayısını 1 olarak ayarlamak için Spark-Gönder için **--Master yerel [1]** seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18ba7-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="18ba7-123">Scala kodunda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="18ba7-123">Debug Scala code</span></span>

<span data-ttu-id="18ba7-124">Scala tarafı kodunda ( `DotnetRunner` , `DotnetBackendHandler` , vb.) hata ayıklaması yapmanız gerekirse, aşağıdaki komutu kullanabilir ve [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklayıcı ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="18ba7-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="18ba7-125">Komutu çalıştırdıktan sonra, [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklayıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="18ba7-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="18ba7-126">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="18ba7-126">Next steps</span></span>

* [<span data-ttu-id="18ba7-127">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="18ba7-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="18ba7-128">Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="18ba7-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="18ba7-129">Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı</span><span class="sxs-lookup"><span data-stu-id="18ba7-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="18ba7-130">Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="18ba7-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
