---
title: Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma
description: Apache Spark uygulamasının bir .NET uygulamasını Amazon EMR Spark 'a dağıtmayı öğrenin.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: dd1cfdf12266b55d9dbc0210479b89ba68c59a38
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688078"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="e4745-103">Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="e4745-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="e4745-104">Bu öğreticide, Amazon EMR Spark 'a Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="e4745-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="e4745-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) , AWS 'de büyük veri çerçevelerini çalıştırmayı kolaylaştıran bir yönetilen küme platformudur.</span><span class="sxs-lookup"><span data-stu-id="e4745-105">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

<span data-ttu-id="e4745-106">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="e4745-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="e4745-107">Microsoft. spark. Worker 'ı hazırla</span><span class="sxs-lookup"><span data-stu-id="e4745-107">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="e4745-108">Spark .NET uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="e4745-108">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="e4745-109">Uygulamanızı Amazon EMR Spark 'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="e4745-109">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="e4745-110">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e4745-110">Run your app</span></span>

> [!Note]
> <span data-ttu-id="e4745-111">AWS EMR Spark, Linux tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4745-111">AWS EMR Spark is Linux-based.</span></span> <span data-ttu-id="e4745-112">Bu nedenle, uygulamanızı AWS EMR Spark 'a dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için .NET Core derleyicisi kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4745-112">Therefore, if you are interested in deploying your app to AWS EMR Spark, make sure your app is .NET Standard compatible and that you use .NET Core compiler to compile your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e4745-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e4745-113">Prerequisites</span></span>

<span data-ttu-id="e4745-114">Başlamadan önce aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="e4745-114">Before you start, do the following:</span></span>

* <span data-ttu-id="e4745-115">[AWS CLI](https://aws.amazon.com/cli/)'yi indirin.</span><span class="sxs-lookup"><span data-stu-id="e4745-115">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="e4745-116">[İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="e4745-116">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="e4745-117">Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.</span><span class="sxs-lookup"><span data-stu-id="e4745-117">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="e4745-118">Çalışan bağımlılıklarını hazırlama</span><span class="sxs-lookup"><span data-stu-id="e4745-118">Prepare worker dependencies</span></span>

<span data-ttu-id="e4745-119">**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="e4745-119">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="e4745-120">Bir C# UDF (Kullanıcı tanımlı Işlev) yürütmek istediğinizde Spark 'ın, UDF 'yi yürütmek için .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4745-120">When you want to execute a C# UDF (User-Defined Function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="e4745-121">**Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4745-121">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="e4745-122">Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="e4745-122">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="e4745-123">Örneğin, `.NET for Apache Spark v1.0.0` kullanmak Istiyorsanız `netcoreapp3.1` [Microsoft. spark. Worker. netcoreapp 3.1. Linux-x64-1.0.0. tar. gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz)dosyasını indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4745-123">For example, if you want `.NET for Apache Spark v1.0.0` using `netcoreapp3.1`, you'd download [Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span>

2. <span data-ttu-id="e4745-124">`Microsoft.Spark.Worker.<release>.tar.gz`Kümenizin erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) .</span><span class="sxs-lookup"><span data-stu-id="e4745-124">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="e4745-125">Apache Spark uygulamanızı .NET 'e hazırlama</span><span class="sxs-lookup"><span data-stu-id="e4745-125">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="e4745-126">Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.</span><span class="sxs-lookup"><span data-stu-id="e4745-126">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="e4745-127">Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="e4745-127">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="e4745-128">Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4745-128">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="e4745-129">`<your app>.zip`Yayımlanan dosyalar için üretin.</span><span class="sxs-lookup"><span data-stu-id="e4745-129">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="e4745-130">Kullanarak Linux üzerinde aşağıdaki komutu çalıştırın `zip` .</span><span class="sxs-lookup"><span data-stu-id="e4745-130">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="e4745-131">Aşağıdaki öğeleri, kümenizin erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="e4745-131">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="e4745-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="e4745-132">`microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="e4745-133">Her bir yürütücünün çalışma dizinine yerleştirilmesi için dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler gibi) veya derlemeler (Kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren dll 'Ler gibi).</span><span class="sxs-lookup"><span data-stu-id="e4745-133">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="e4745-134">Amazon EMR Spark 'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="e4745-134">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="e4745-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) , AWS 'de büyük veri çerçevelerini çalıştırmayı kolaylaştıran bir yönetilen küme platformudur.</span><span class="sxs-lookup"><span data-stu-id="e4745-135">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="e4745-136">Amazon EMR Spark, Linux tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4745-136">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="e4745-137">Bu nedenle, uygulamanızı Amazon EMR Spark 'a dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4745-137">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="e4745-138">Microsoft. spark. Worker 'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="e4745-138">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="e4745-139">Bu adım yalnızca küme oluşturulurken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e4745-139">This step is only required at cluster creation.</span></span>

<span data-ttu-id="e4745-140">`install-worker.sh` [Önyükleme eylemlerini](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)kullanarak küme oluşturma sırasında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4745-140">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="e4745-141">AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4745-141">Run the following command on Linux using AWS CLI.</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="e4745-142">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e4745-142">Run your app</span></span>

<span data-ttu-id="e4745-143">Bu uygulamayı Amazon EMR Spark: Spark-gönderme ve Amazon EMR adımlarında çalıştırmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e4745-143">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="e4745-144">Spark-gönder kullan</span><span class="sxs-lookup"><span data-stu-id="e4745-144">Use spark-submit</span></span>

<span data-ttu-id="e4745-145">[Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanarak, Amazon emr spark 'a Apache Spark işleri için .net gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4745-145">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="e4745-146">`ssh` Kümedeki düğümlerden birine.</span><span class="sxs-lookup"><span data-stu-id="e4745-146">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="e4745-147">`spark-submit` komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4745-147">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="e4745-148">Amazon EMR adımlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="e4745-148">Use Amazon EMR Steps</span></span>

<span data-ttu-id="e4745-149">[Amazon emr adımları](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) , BIR ışı emr kümesinde yüklü Spark çerçevesine göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4745-149">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="e4745-150">AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e4745-150">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="e4745-151">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e4745-151">Next steps</span></span>

<span data-ttu-id="e4745-152">Bu öğreticide, Apache Spark için .NET uygulamanızı Amazon EMR Spark 'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="e4745-152">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="e4745-153">Apache Spark örnek projelerine yönelik .NET için GitHub ' a devam edin.</span><span class="sxs-lookup"><span data-stu-id="e4745-153">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e4745-154">Apache Spark örnekleri için .NET</span><span class="sxs-lookup"><span data-stu-id="e4745-154">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
