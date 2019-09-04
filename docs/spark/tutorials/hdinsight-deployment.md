---
title: Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma
description: HDInsight için bir .NET Apache Spark uygulamasının nasıl dağıtılacağını öğrenin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 81d1af1fd4e3329c4a289eea388edf8af57d7c4e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243941"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="c1459-103">Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="c1459-103">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="c1459-104">Bu öğreticide, Azure HDInsight 'a Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="c1459-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Azure HDInsight.</span></span>

<span data-ttu-id="c1459-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c1459-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="c1459-106">Microsoft. spark. Worker 'ı hazırla</span><span class="sxs-lookup"><span data-stu-id="c1459-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="c1459-107">Spark .NET uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="c1459-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="c1459-108">Uygulamanızı Azure HDInsight 'a dağıtma</span><span class="sxs-lookup"><span data-stu-id="c1459-108">Deploy your app to Azure HDInsight</span></span>
> * <span data-ttu-id="c1459-109">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c1459-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1459-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c1459-110">Prerequisites</span></span>

<span data-ttu-id="c1459-111">Başlamadan önce aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="c1459-111">Before you start, do the following:</span></span>

* <span data-ttu-id="c1459-112">[Azure Depolama Gezgini](https://azure.microsoft.com/features/storage-explorer/)indirin.</span><span class="sxs-lookup"><span data-stu-id="c1459-112">Download [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span>
* <span data-ttu-id="c1459-113">[İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="c1459-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="c1459-114">Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.</span><span class="sxs-lookup"><span data-stu-id="c1459-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="c1459-115">Çalışan bağımlılıklarını hazırlama</span><span class="sxs-lookup"><span data-stu-id="c1459-115">Prepare worker dependencies</span></span>

<span data-ttu-id="c1459-116">**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="c1459-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="c1459-117">Bir C# UDF (Kullanıcı tanımlı işlev) yürütmek istediğinizde Spark 'ıN, UDF 'yi yürütmek IÇIN .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1459-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="c1459-118">**Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1459-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="c1459-119">Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="c1459-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="c1459-120">Örneğin, kullanmak `.NET for Apache Spark v0.1.0` `netcoreapp2.1`istiyorsanız [Microsoft. spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)dosyasını indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1459-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="c1459-121">Kümenizin `Microsoft.Spark.Worker.<release>.tar.gz` erişimi olan bir dağıtılmış dosya sistemine (örn., Ida, IDB, ADLS) yükleyin ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) .</span><span class="sxs-lookup"><span data-stu-id="c1459-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="c1459-122">Apache Spark uygulamanızı .NET 'e hazırlama</span><span class="sxs-lookup"><span data-stu-id="c1459-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="c1459-123">Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.</span><span class="sxs-lookup"><span data-stu-id="c1459-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="c1459-124">Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="c1459-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="c1459-125">Linux üzerinde aşağıdaki komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1459-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="c1459-126">Yayımlanan `<your app>.zip` dosyalar için üretin.</span><span class="sxs-lookup"><span data-stu-id="c1459-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="c1459-127">Kullanarak `zip`Linux üzerinde aşağıdaki komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1459-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="c1459-128">Aşağıdakileri kümenizin erişimi olan bir dağıtılmış dosya sistemine (örn., IBir, ıDB, ADLS) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c1459-128">Upload the following to a distributed file system (e.g., HDFS, WASB, ADLS) that your cluster has access to:</span></span>

   * <span data-ttu-id="c1459-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="c1459-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="c1459-130">Dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler) veya derlemeler (Kullanıcı tanımlı işlevlerinizi ya da `app` bağlı olduğunuz kitaplıkları içeren dll 'ler gibi) her bir yürütücünün çalışma dizinine yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="c1459-130">Files (like dependency files or common data accessible to every worker) or Assemblies (like DLLs that contain your user-defined functions or libraries that your `app` depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-azure-hdinsight-spark"></a><span data-ttu-id="c1459-131">Azure HDInsight Spark dağıtma</span><span class="sxs-lookup"><span data-stu-id="c1459-131">Deploy to Azure HDInsight Spark</span></span>

<span data-ttu-id="c1459-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) , bulutta bulunan ve kullanıcıların Azure 'da Spark kümeleri başlatma ve yapılandırmalarına olanak tanıyan Apache Spark Microsoft uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c1459-132">[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) is the Microsoft implementation of Apache Spark in the cloud that allows users to launch and configure Spark clusters in Azure.</span></span> <span data-ttu-id="c1459-133">[Azure depolama](https://azure.microsoft.com/services/storage/) veya [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2)depolanan verilerinizi işlemek için HDInsight Spark kümelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1459-133">You can use HDInsight Spark clusters to process your data stored in [Azure Storage](https://azure.microsoft.com/services/storage/) or [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2).</span></span>

> [!NOTE]
> <span data-ttu-id="c1459-134">Azure HDInsight Spark Linux tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="c1459-134">Azure HDInsight Spark is Linux-based.</span></span> <span data-ttu-id="c1459-135">Uygulamanızı Azure HDInsight Spark dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c1459-135">If you are interested in deploying your app to Azure HDInsight Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="c1459-136">Microsoft. spark. Worker 'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="c1459-136">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="c1459-137">Bu adım kümeniz için yalnızca bir kere gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c1459-137">This step is only required once for your cluster.</span></span>

<span data-ttu-id="c1459-138">`install-worker.sh` [HDInsight betik eylemlerini](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)kullanarak kümede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1459-138">Run `install-worker.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

|<span data-ttu-id="c1459-139">Ayar</span><span class="sxs-lookup"><span data-stu-id="c1459-139">Setting</span></span>|<span data-ttu-id="c1459-140">Değer</span><span class="sxs-lookup"><span data-stu-id="c1459-140">Value</span></span>|
|-------|-----|
|<span data-ttu-id="c1459-141">Betik türü</span><span class="sxs-lookup"><span data-stu-id="c1459-141">Script type</span></span>|<span data-ttu-id="c1459-142">Özel</span><span class="sxs-lookup"><span data-stu-id="c1459-142">Custom</span></span>|
|<span data-ttu-id="c1459-143">Ad</span><span class="sxs-lookup"><span data-stu-id="c1459-143">Name</span></span>|<span data-ttu-id="c1459-144">Microsoft. spark. Worker 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="c1459-144">Install Microsoft.Spark.Worker</span></span>|
|<span data-ttu-id="c1459-145">Bash betiği URI 'SI</span><span class="sxs-lookup"><span data-stu-id="c1459-145">Bash script URI</span></span>|<span data-ttu-id="c1459-146">Karşıya yüklediğiniz `install-worker.sh`URI.</span><span class="sxs-lookup"><span data-stu-id="c1459-146">The URI to which you uploaded `install-worker.sh`.</span></span> <span data-ttu-id="c1459-147">Örneğin, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span><span class="sxs-lookup"><span data-stu-id="c1459-147">For example, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`</span></span>|
|<span data-ttu-id="c1459-148">Düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="c1459-148">Node type(s)</span></span>|<span data-ttu-id="c1459-149">Indan</span><span class="sxs-lookup"><span data-stu-id="c1459-149">Worker</span></span>|
|<span data-ttu-id="c1459-150">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1459-150">Parameters</span></span>|<span data-ttu-id="c1459-151">`install-worker.sh`Parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c1459-151">Parameters to `install-worker.sh`.</span></span> <span data-ttu-id="c1459-152">Örneğin, Azure Data Lake Gen 2 ' `install-worker.sh` ye karşıya yüklenmişse, bu durumda `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`olur.</span><span class="sxs-lookup"><span data-stu-id="c1459-152">For example, if you uploaded `install-worker.sh` to Azure Data Lake Gen 2 then it would be `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`.</span></span>|

![Betik eylemi resmi](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a><span data-ttu-id="c1459-154">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c1459-154">Run your app</span></span>

<span data-ttu-id="c1459-155">İşinizi, veya Apache Livy kullanarak `spark-submit` Azure HDInsight 'a gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1459-155">You can submit your job to Azure HDInsight using `spark-submit` or Apache Livy.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="c1459-156">Spark-gönder kullan</span><span class="sxs-lookup"><span data-stu-id="c1459-156">Use spark-submit</span></span>

<span data-ttu-id="c1459-157">Azure HDInsight 'a Apache Spark işleri için .NET göndermek için [Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1459-157">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>
 
1. <span data-ttu-id="c1459-158">`ssh`kümenizdeki baş düğümlerden birine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1459-158">`ssh` into one of the head nodes in your cluster.</span></span>

1. <span data-ttu-id="c1459-159">Şunu `spark-submit`Çalıştır:</span><span class="sxs-lookup"><span data-stu-id="c1459-159">Run `spark-submit`:</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a><span data-ttu-id="c1459-160">Apache Livy kullanın</span><span class="sxs-lookup"><span data-stu-id="c1459-160">Use Apache Livy</span></span>

<span data-ttu-id="c1459-161">Apache Spark işlerini bir Azure HDInsight Spark kümesine göndermek için Apache Spark REST API [Apache Livy](https://livy.incubator.apache.org/)'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1459-161">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="c1459-162">Daha fazla bilgi için bkz. [Apache Livy Ile uzak işler](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="c1459-162">For more information, see [Remote jobs with Apache Livy](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="c1459-163">Linux 'ta aşağıdaki komutu kullanarak `curl`çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c1459-163">You can run the following command on Linux using `curl`:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="c1459-164">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c1459-164">Next steps</span></span>

<span data-ttu-id="c1459-165">Bu öğreticide, .NET Apache Spark uygulamanızı Azure HDInsight 'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="c1459-165">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="c1459-166">HDInsight hakkında daha fazla bilgi edinmek için Azure HDInsight belgelerine geçin.</span><span class="sxs-lookup"><span data-stu-id="c1459-166">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1459-167">Azure HDInsight belgeleri</span><span class="sxs-lookup"><span data-stu-id="c1459-167">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
