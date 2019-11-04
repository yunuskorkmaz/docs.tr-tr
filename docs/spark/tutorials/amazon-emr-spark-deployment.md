---
title: Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma
description: Apache Spark uygulamasının bir .NET uygulamasını Amazon EMR Spark 'a dağıtmayı öğrenin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a1ff1ba4d5e855e0ac36b99b0c9d63adfaaaac1e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454941"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="aad92-103">Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="aad92-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="aad92-104">Bu öğreticide, Amazon EMR Spark 'a Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="aad92-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="aad92-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="aad92-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="aad92-106">Microsoft. spark. Worker 'ı hazırla</span><span class="sxs-lookup"><span data-stu-id="aad92-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="aad92-107">Spark .NET uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="aad92-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="aad92-108">Uygulamanızı Amazon EMR Spark 'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="aad92-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="aad92-109">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="aad92-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aad92-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="aad92-110">Prerequisites</span></span>

<span data-ttu-id="aad92-111">Başlamadan önce aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="aad92-111">Before you start, do the following:</span></span>

* <span data-ttu-id="aad92-112">[AWS CLI](https://aws.amazon.com/cli/)'yi indirin.</span><span class="sxs-lookup"><span data-stu-id="aad92-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="aad92-113">[İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="aad92-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="aad92-114">Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.</span><span class="sxs-lookup"><span data-stu-id="aad92-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="aad92-115">Çalışan bağımlılıklarını hazırlama</span><span class="sxs-lookup"><span data-stu-id="aad92-115">Prepare worker dependencies</span></span>

<span data-ttu-id="aad92-116">**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="aad92-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="aad92-117">Bir C# UDF (Kullanıcı tanımlı işlev) yürütmek istediğinizde Spark 'ıN, UDF 'yi yürütmek IÇIN .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aad92-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="aad92-118">**Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="aad92-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="aad92-119">Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="aad92-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="aad92-120">Örneğin, `netcoreapp2.1` kullanarak `.NET for Apache Spark v0.1.0` ' ı istiyorsanız, [Microsoft. spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)dosyasını indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad92-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="aad92-121">`Microsoft.Spark.Worker.<release>.tar.gz` ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'yi, kümenizin erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="aad92-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="aad92-122">Apache Spark uygulamanızı .NET 'e hazırlama</span><span class="sxs-lookup"><span data-stu-id="aad92-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="aad92-123">Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.</span><span class="sxs-lookup"><span data-stu-id="aad92-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="aad92-124">Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="aad92-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="aad92-125">Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aad92-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="aad92-126">Yayımlanan dosyalar için `<your app>.zip` üretir.</span><span class="sxs-lookup"><span data-stu-id="aad92-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="aad92-127">`zip`kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aad92-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="aad92-128">Aşağıdaki öğeleri, kümenizin erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="aad92-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="aad92-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="aad92-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="aad92-130">Her bir yürütücünün çalışma dizinine yerleştirilmesi için dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler gibi) veya derlemeler (Kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren dll 'Ler gibi).</span><span class="sxs-lookup"><span data-stu-id="aad92-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="aad92-131">Amazon EMR Spark 'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="aad92-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="aad92-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) , AWS 'de büyük veri çerçevelerini çalıştırmayı kolaylaştıran bir yönetilen küme platformudur.</span><span class="sxs-lookup"><span data-stu-id="aad92-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="aad92-133">Amazon EMR Spark, Linux tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="aad92-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="aad92-134">Bu nedenle, uygulamanızı Amazon EMR Spark 'a dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="aad92-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="aad92-135">Microsoft. spark. Worker 'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="aad92-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="aad92-136">Bu adım yalnızca küme oluşturulurken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="aad92-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="aad92-137">[Önyükleme eylemlerini](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)kullanarak küme oluşturma sırasında `install-worker.sh` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aad92-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="aad92-138">AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aad92-138">Run the following command on Linux using AWS CLI.</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="aad92-139">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="aad92-139">Run your app</span></span>

<span data-ttu-id="aad92-140">Bu uygulamayı Amazon EMR Spark: Spark-gönderme ve Amazon EMR adımlarında çalıştırmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="aad92-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="aad92-141">Spark-gönder kullan</span><span class="sxs-lookup"><span data-stu-id="aad92-141">Use spark-submit</span></span>

<span data-ttu-id="aad92-142">[Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanarak, Amazon emr spark 'a Apache Spark işleri için .net gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aad92-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="aad92-143">Kümedeki düğümlerden birine `ssh`.</span><span class="sxs-lookup"><span data-stu-id="aad92-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="aad92-144">`spark-submit`'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aad92-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="aad92-145">Amazon EMR adımlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="aad92-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="aad92-146">[Amazon emr adımları](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) , BIR ışı emr kümesinde yüklü Spark çerçevesine göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aad92-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="aad92-147">AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aad92-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="aad92-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="aad92-148">Next steps</span></span>

<span data-ttu-id="aad92-149">Bu öğreticide, Apache Spark için .NET uygulamanızı Amazon EMR Spark 'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="aad92-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="aad92-150">Apache Spark örnek projelerine yönelik .NET için GitHub ' a devam edin.</span><span class="sxs-lookup"><span data-stu-id="aad92-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aad92-151">Apache Spark örnekleri için .NET</span><span class="sxs-lookup"><span data-stu-id="aad92-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
