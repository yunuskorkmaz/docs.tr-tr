---
title: Azure HDInsight 'a Apache Spark iş için .NET gönderme
description: Spark-gönder ve Apache Livy kullanarak Azure HDInsight 'a Apache Spark iş için .NET gönderme hakkında bilgi edinin.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 74be4ecf33a9a881633da0630fa1c1a4bf0b19c6
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688169"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="839d8-103">Azure HDInsight 'a Apache Spark iş için .NET gönderme</span><span class="sxs-lookup"><span data-stu-id="839d8-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="839d8-104">Apache Spark iş için .NET uygulamanızı HDInsight 'a dağıtmanın iki yolu vardır: `spark-submit` ve Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="839d8-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="839d8-105">Spark-gönder kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="839d8-105">Deploy using spark-submit</span></span>

<span data-ttu-id="839d8-106">Azure HDInsight 'a Apache Spark işleri için .NET göndermek için [Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="839d8-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="839d8-107">Azure portal HDInsight Spark kümenize gidin ve ardından **SSH + küme oturumu aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="839d8-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="839d8-108">SSH oturum açma bilgilerini kopyalayın ve oturumu bir terminale yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="839d8-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="839d8-109">Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="839d8-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="839d8-110">Sizi Ubuntu ve Spark 'a yönlendiren iletiler görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="839d8-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="839d8-111">Uygulamanızı HDInsight kümenizde çalıştırmak için **Spark-gönder** komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="839d8-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="839d8-112">Örnek betikteki **myContainer** ve **mystorageaccount** ' ın blob Kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirilmesini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="839d8-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="839d8-113">Ayrıca, Microsoft-Spark jar 'i, kullanılan Apache Spark Spark ve .NET sürümü ile değiştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="839d8-113">Also remember to replace the microsoft-spark jar with the version of Spark and .NET for Apache Spark being used.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="839d8-114">Apache Livy kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="839d8-114">Deploy using Apache Livy</span></span>

<span data-ttu-id="839d8-115">Apache Spark işlerini bir Azure HDInsight Spark kümesine göndermek için Apache Spark REST API [Apache Livy](https://livy.incubator.apache.org/)'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="839d8-115">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="839d8-116">Daha fazla bilgi için bkz. [Apache Livy Ile uzak işler](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="839d8-116">For more information, see [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="839d8-117">Linux 'ta aşağıdaki komutu kullanarak çalıştırabilirsiniz `curl` :</span><span class="sxs-lookup"><span data-stu-id="839d8-117">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="839d8-118">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="839d8-118">Next steps</span></span>

* [<span data-ttu-id="839d8-119">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="839d8-119">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="839d8-120">Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="839d8-120">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="839d8-121">HDInsight belgeleri</span><span class="sxs-lookup"><span data-stu-id="839d8-121">HDInsight Documentation</span></span>](/azure/hdinsight/)
