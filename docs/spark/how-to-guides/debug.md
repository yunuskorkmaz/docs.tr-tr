---
title: Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama
description: Windows 'da Apache Spark için .NET uygulamanızı nasıl ayıklayacağınızı öğrenin.
ms.date: 08/15/2019
ms.topic: how-to
ms.custom: mvc
ms.openlocfilehash: 08142bd45c475ddd131053213ebdea5f843fa736
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69667660"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="ac816-103">Apache Spark uygulama için bir .NET hatası ayıklama</span><span class="sxs-lookup"><span data-stu-id="ac816-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="ac816-104">Bu nasıl yapılır, Windows 'da Apache Spark uygulaması ve Scala kodu için .NET uygulamanızda hata ayıklamak üzere çalıştırmanız gereken komutları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac816-104">This how-to provides the commands you need to run to debug your .NET for Apache Spark application and Scala code on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="ac816-105">Uygulamanızda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ac816-105">Debug your application</span></span>

<span data-ttu-id="ac816-106">Yeni bir komut istemi penceresi açın, aşağıdakileri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac816-106">Open a new command prompt window, run the following:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="ac816-107">Komutu çalıştırdığınızda aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="ac816-107">When you run the command, you see the following output:</span></span>

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="ac816-108">Bu hata ayıklama modunda, `DotnetRunner` .NET uygulamasını başlatamaz, ancak bağlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="ac816-108">In this debug mode, `DotnetRunner` does not launch the .NET application, but it waits for it to connect.</span></span> <span data-ttu-id="ac816-109">Bu komut istemi penceresini açık bırakın.</span><span class="sxs-lookup"><span data-stu-id="ac816-109">Leave this command prompt window open.</span></span>

<span data-ttu-id="ac816-110">Artık uygulamanızda hata ayıklamak için, .NET uygulamanızı herhangi bir hata ayıklayıcı ile çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac816-110">Now you can run your .NET application with any debugger to debug your application.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="ac816-111">Scala kodunda hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ac816-111">Debug Scala code</span></span>

<span data-ttu-id="ac816-112">`DotnetRunner` Ya`DotnetBackendHandler`da gibi Scala tarafı kodunda hata ayıklaması yapmanız gerekiyorsa, aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="ac816-112">If you need to debug the Scala side code, such as `DotnetRunner` or `DotnetBackendHandler`, run the following command:</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="ac816-113">Komutu çalıştırdıktan sonra, [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklayıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac816-113">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ac816-114">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ac816-114">Next steps</span></span>

* [<span data-ttu-id="ac816-115">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="ac816-115">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="ac816-116">Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="ac816-116">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="ac816-117">Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı</span><span class="sxs-lookup"><span data-stu-id="ac816-117">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="ac816-118">Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="ac816-118">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)