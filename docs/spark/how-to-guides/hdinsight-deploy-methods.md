---
title: Azure HDInsight'a Apache Spark işi için bir .NET gönderme
description: Kıvılcım gönder ve Apache Livy'yi kullanarak Azure HDInsight'a Apache Spark için bir .NET işini nasıl göndereceğinizi öğrenin.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 83359f7f613b500a4ce121ce1612cda0ad1191ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185792"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="09059-103">Azure HDInsight'a Apache Spark işi için bir .NET gönderme</span><span class="sxs-lookup"><span data-stu-id="09059-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="09059-104">Apache Spark için .NET işinizi HDInsight'a `spark-submit` ve Apache Livy'ye dağıtmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="09059-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="09059-105">Kıvılcım gönder'i kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="09059-105">Deploy using spark-submit</span></span>

<span data-ttu-id="09059-106">Apache [Spark](https://spark.apache.org/docs/latest/submitting-applications.html) işleri için .NET'i Azure HDInsight'a göndermek için kıvılcım gönder komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09059-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="09059-107">Azure portalında HDInsight Spark kümenize gidin ve ardından **SSH + Cluster oturum açma'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="09059-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="09059-108">Ssh giriş bilgilerini kopyalayın ve girişi bir terminale yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="09059-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="09059-109">Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="09059-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="09059-110">Ubuntu ve Spark'a hoş geldin mesajları görmelisin.</span><span class="sxs-lookup"><span data-stu-id="09059-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="09059-111">UYGULAMANIZI HDInsight kümenizde çalıştırmak için **kıvılcım gönder** komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="09059-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="09059-112">Örnek komut dosyasındaki **mycontainer** ve **mystorage account'u** blob kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="09059-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="09059-113">Ayrıca, dağıtım için `microsoft-spark-2.3.x-0.6.0.jar` kullandığınız uygun kavanoz dosyasıyla değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="09059-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="09059-114">`2.3.x`Apache Spark sürümünü temsil `0.6.0` eder ve [Apache Spark işçisi için .NET](https://github.com/dotnet/spark/releases)sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="09059-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="09059-115">Apache Livy kullanarak dağıtın</span><span class="sxs-lookup"><span data-stu-id="09059-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="09059-116">[Apache Livy](https://livy.incubator.apache.org/),Apache Spark REST API'yi kullanarak Apache Spark işleri için .NET'i bir Azure HDInsight Spark kümesine gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09059-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="09059-117">Daha fazla bilgi için, [Apache Livy ile Uzak işleri](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface)bakın.</span><span class="sxs-lookup"><span data-stu-id="09059-117">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="09059-118">Aşağıdaki komutu Kullanarak Linux `curl`üzerinde çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="09059-118">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="09059-119">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="09059-119">Next steps</span></span>

* [<span data-ttu-id="09059-120">Apache Spark için .NET ile başlayın</span><span class="sxs-lookup"><span data-stu-id="09059-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="09059-121">Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="09059-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="09059-122">HDInsight Dokümantasyon</span><span class="sxs-lookup"><span data-stu-id="09059-122">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
