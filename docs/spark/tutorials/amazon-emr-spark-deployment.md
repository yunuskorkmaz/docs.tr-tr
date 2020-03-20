---
title: Amazon EMR Spark'a Apache Spark uygulaması için bir .NET dağıtın
description: Apache Spark uygulaması için Bir .NET uygulamasını Amazon EMR Spark'a nasıl dağıtacağınız keşfedin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73454941"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="72f33-103">Amazon EMR Spark'a Apache Spark uygulaması için bir .NET dağıtın</span><span class="sxs-lookup"><span data-stu-id="72f33-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="72f33-104">Bu öğretici, Amazon EMR Spark'a Apache Spark uygulaması için bir .NET uygulamasının nasıl dağıtılanacağını öğretir.</span><span class="sxs-lookup"><span data-stu-id="72f33-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="72f33-105">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72f33-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="72f33-106">Microsoft.Spark.Worker'ı hazırlayın</span><span class="sxs-lookup"><span data-stu-id="72f33-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="72f33-107">Kıvılcım .NET uygulamanızı yayımlayın</span><span class="sxs-lookup"><span data-stu-id="72f33-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="72f33-108">Uygulamanızı Amazon EMR Spark'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="72f33-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="72f33-109">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="72f33-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72f33-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="72f33-110">Prerequisites</span></span>

<span data-ttu-id="72f33-111">Başlamadan önce aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="72f33-111">Before you start, do the following:</span></span>

* <span data-ttu-id="72f33-112">[AWS CLI'yi](https://aws.amazon.com/cli/)indirin.</span><span class="sxs-lookup"><span data-stu-id="72f33-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="72f33-113">[install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="72f33-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="72f33-114">Bu, Apache Spark bağımlı dosyaları için .NET'i daha sonra Spark kümenizin alt düğümlerine kopyalamak için kullandığınız yardımcı komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="72f33-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="72f33-115">Çalışan bağımlılıklarını hazırlama</span><span class="sxs-lookup"><span data-stu-id="72f33-115">Prepare worker dependencies</span></span>

<span data-ttu-id="72f33-116">**Microsoft.Spark.Worker,** Spark kümenizin tek tek alt düğümlerinde yaşayan bir arka uç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="72f33-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="72f33-117">Bir C# UDF (kullanıcı tanımlı işlev) yürütmek istediğinizde, Spark'ın UDF'yi yürütmek için .NET CLR'yi nasıl başlatabileceğinizi anlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="72f33-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="72f33-118">**Microsoft.Spark.Worker,** Spark'a bu işlevselliği sağlayan bir sınıf koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="72f33-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="72f33-119">Kümenizde dağıtılacak bir [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="72f33-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="72f33-120">Örneğin, kullanmak `.NET for Apache Spark v0.1.0` `netcoreapp2.1`istiyorsanız, [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72f33-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="72f33-121">Kümenizin erişebilen dağıtılmış bir dosya sistemine (örneğin, S3) yükleyin `Microsoft.Spark.Worker.<release>.tar.gz` ve [install-worker.sh.](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh)</span><span class="sxs-lookup"><span data-stu-id="72f33-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="72f33-122">.NET'inizi Apache Spark uygulamasına hazırlayın</span><span class="sxs-lookup"><span data-stu-id="72f33-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="72f33-123">Uygulamanızı oluşturmak için [Başlangıç](get-started.md) öğretisini izleyin.</span><span class="sxs-lookup"><span data-stu-id="72f33-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="72f33-124">Spark .NET uygulamanızı bağımsız olarak yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="72f33-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="72f33-125">Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72f33-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="72f33-126">Yayınlanan `<your app>.zip` dosyalar için üretin.</span><span class="sxs-lookup"><span data-stu-id="72f33-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="72f33-127">Kullanarak Linux üzerinde aşağıdaki `zip`komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72f33-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="72f33-128">Kümenizin erişebilen dağıtılmış bir dosya sistemine (örneğin, S3) aşağıdaki öğeleri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="72f33-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="72f33-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu kavanoz [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahildir ve uygulamanızın yapı çıktı dizini nde yer alır.</span><span class="sxs-lookup"><span data-stu-id="72f33-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="72f33-130">Her çalışanın erişebileceği bağımlılık dosyaları (bağımlılık dosyaları veya her çalışanın erişebileceği yaygın veriler gibi) veya derlemeler (uygulamanızın bağlı olduğu kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren DL'ler gibi) her uygulayıcının çalışma dizinine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="72f33-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="72f33-131">Amazon EMR Spark'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="72f33-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="72f33-132">[Amazon EMR,](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) AWS'de büyük veri çerçevelerinin çalıştırAn basitleştiren yönetilen bir küme platformudur.</span><span class="sxs-lookup"><span data-stu-id="72f33-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="72f33-133">Amazon EMR Spark Linux tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="72f33-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="72f33-134">Bu nedenle, uygulamanızı Amazon EMR Spark'a dağıtmak istiyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini kullandığınızdan](https://dotnet.microsoft.com/download) emin olun.</span><span class="sxs-lookup"><span data-stu-id="72f33-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="72f33-135">Microsoft.Spark.Worker'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="72f33-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="72f33-136">Bu adım yalnızca küme oluşturma da gereklidir.</span><span class="sxs-lookup"><span data-stu-id="72f33-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="72f33-137">`install-worker.sh` [Bootstrap Eylemleri](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)kullanarak küme oluşturma sırasında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72f33-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="72f33-138">AWS CLI kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72f33-138">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="72f33-139">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="72f33-139">Run your app</span></span>

<span data-ttu-id="72f33-140">Uygulamanızı Amazon EMR Spark'ta çalıştırmanın iki yolu vardır: kıvılcım gönderme ve Amazon EMR Adımları.</span><span class="sxs-lookup"><span data-stu-id="72f33-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="72f33-141">Kıvılcım gönder'i kullanma</span><span class="sxs-lookup"><span data-stu-id="72f33-141">Use spark-submit</span></span>

<span data-ttu-id="72f33-142">Apache Spark işleri için .NET'i Amazon EMR Spark'a göndermek için [kıvılcım gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72f33-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="72f33-143">`ssh`kümedeki düğümlerden birine.</span><span class="sxs-lookup"><span data-stu-id="72f33-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="72f33-144">`spark-submit` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72f33-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="72f33-145">Amazon EMR Adımlarını Kullan</span><span class="sxs-lookup"><span data-stu-id="72f33-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="72f33-146">[Amazon EMR Adımları,](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) EMR kümesine yüklenen Spark çerçevesine iş göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72f33-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="72f33-147">AWS CLI kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="72f33-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="72f33-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="72f33-148">Next steps</span></span>

<span data-ttu-id="72f33-149">Bu eğitimde, Apache Spark uygulaması için .NET'inizi Amazon EMR Spark'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="72f33-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="72f33-150">Apache Spark örnek projeleri için .NET için GitHub'a devam edin.</span><span class="sxs-lookup"><span data-stu-id="72f33-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72f33-151">.Net Apache Spark örnekleri için</span><span class="sxs-lookup"><span data-stu-id="72f33-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
