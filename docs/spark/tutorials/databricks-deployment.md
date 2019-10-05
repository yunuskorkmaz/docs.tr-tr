---
title: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı
description: Databricks 'e Apache Spark uygulamasının bir .NET uygulamasını nasıl dağıtacağınızı öğrenin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 035a3c36337413153ee0370aec154d48b84a4711
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957248"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="b0f9e-103">Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı</span><span class="sxs-lookup"><span data-stu-id="b0f9e-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="b0f9e-104">Bu öğreticide, Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="b0f9e-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="b0f9e-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="b0f9e-106">Microsoft. spark. Worker 'ı hazırla</span><span class="sxs-lookup"><span data-stu-id="b0f9e-106">Prepare Microsoft.Spark.Worker</span></span>
> - <span data-ttu-id="b0f9e-107">Spark .NET uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="b0f9e-107">Publish your Spark .NET app</span></span>
> - <span data-ttu-id="b0f9e-108">Uygulamanızı Databricks 'e dağıtın</span><span class="sxs-lookup"><span data-stu-id="b0f9e-108">Deploy your app to Databricks</span></span>
> - <span data-ttu-id="b0f9e-109">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b0f9e-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0f9e-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b0f9e-110">Prerequisites</span></span>

<span data-ttu-id="b0f9e-111">Başlamadan önce aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="b0f9e-111">Before you start, do the following:</span></span>

- <span data-ttu-id="b0f9e-112">[Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)'yi indirin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
- <span data-ttu-id="b0f9e-113">[İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="b0f9e-114">Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="b0f9e-115">Çalışan bağımlılıklarını hazırlama</span><span class="sxs-lookup"><span data-stu-id="b0f9e-115">Prepare worker dependencies</span></span>

<span data-ttu-id="b0f9e-116">**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="b0f9e-117">Bir C# UDF (Kullanıcı tanımlı işlev) yürütmek istediğinizde Spark 'ıN, UDF 'yi yürütmek IÇIN .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="b0f9e-118">**Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="b0f9e-119">Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="b0f9e-120">Örneğin, `netcoreapp2.1` kullanarak `.NET for Apache Spark v0.1.0` ' ı istiyorsanız, [Microsoft. spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)dosyasını indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="b0f9e-121">@No__t-0 ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) ' i, kümenizin erişimi olan bir dağıtılmış dosya sistemine (ÖRNEĞIN, dBFS) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="b0f9e-122">Apache Spark uygulamanızı .NET 'e hazırlama</span><span class="sxs-lookup"><span data-stu-id="b0f9e-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="b0f9e-123">Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="b0f9e-124">Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="b0f9e-125">Linux üzerinde aşağıdaki komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-125">You can run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="b0f9e-126">Yayımlanan dosyalar için `<your app>.zip` üretir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="b0f9e-127">Linux üzerinde `zip` kullanarak aşağıdaki komutu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="b0f9e-128">Aşağıdakileri kümenizin erişimi olan bir dağıtılmış dosya sistemine (örneğin, DBFS) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="b0f9e-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   - <span data-ttu-id="b0f9e-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   - `<your app>.zip`
   - <span data-ttu-id="b0f9e-130">Her bir yürütücünün çalışma dizinine yerleştirilmesi için dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler gibi) veya derlemeler (Kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren dll 'Ler gibi).</span><span class="sxs-lookup"><span data-stu-id="b0f9e-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="b0f9e-131">Databricks’e dağıtma</span><span class="sxs-lookup"><span data-stu-id="b0f9e-131">Deploy to Databricks</span></span>

<span data-ttu-id="b0f9e-132">[Databricks](https://databricks.com) , Apache Spark kullanarak bulut tabanlı büyük veri işleme sağlayan bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="b0f9e-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) ve [AWS Databricks](https://databricks.com/aws) , Linux tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="b0f9e-134">Bu nedenle, uygulamanızı Databricks 'e dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisi](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="b0f9e-135">Databricks, mevcut bir etkin kümeye .NET Apache Spark uygulamaları göndermenize veya bir işi her başlattığınızda yeni bir küme oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="b0f9e-136">Bu, bir .NET Apache Spark uygulaması göndermeden önce **Microsoft. spark. Worker** 'ın yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="b0f9e-137">Microsoft. spark. Worker 'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="b0f9e-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="b0f9e-138">Bu adım, bir küme için yalnızca bir kere gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="b0f9e-139">[DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) 'i yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="b0f9e-140">**DB-init.sh** öğesini, kümenize indirmek ve yüklemek istediğiniz **Microsoft. spark. Worker** sürümüne işaret etmek üzere değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="b0f9e-141">[Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html)'yı yükler.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="b0f9e-142">Databricks CLı için [kimlik doğrulama ayrıntılarını ayarlayın](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) .</span><span class="sxs-lookup"><span data-stu-id="b0f9e-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="b0f9e-143">Aşağıdaki komutu kullanarak dosyaları Databricks kümenize yükleyin:</span><span class="sxs-lookup"><span data-stu-id="b0f9e-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="b0f9e-144">Databricks çalışma alanınıza gidin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="b0f9e-145">Sol taraftaki menüden **kümeler** ' ı seçin ve ardından **küme oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="b0f9e-146">Kümeyi uygun şekilde yapılandırdıktan sonra, **Init betiğini** ayarlayın ve kümeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Betik eylemi resmi](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="b0f9e-148">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b0f9e-148">Run your app</span></span> 

<span data-ttu-id="b0f9e-149">@No__t-0 veya `spark-submit` ' i kullanarak işinizi Databricks 'e gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="b0f9e-150">Set JAR kullanın</span><span class="sxs-lookup"><span data-stu-id="b0f9e-150">Use Set JAR</span></span>

<span data-ttu-id="b0f9e-151">[Set jar](https://docs.databricks.com/user-guide/jobs.html#create-a-job) , mevcut bir etkin kümeye bir iş göndermenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="b0f9e-152">Tek seferlik kurulum</span><span class="sxs-lookup"><span data-stu-id="b0f9e-152">One-time setup</span></span>

1. <span data-ttu-id="b0f9e-153">Databricks kümenize gidin ve sol taraftaki menüden **işler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="b0f9e-154">Ardından **kavanı ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="b0f9e-155">Uygun `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` dosyasını karşıya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="b0f9e-156">Parametreleri uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-156">Set the parameters appropriately.</span></span>

   | <span data-ttu-id="b0f9e-157">Parametre</span><span class="sxs-lookup"><span data-stu-id="b0f9e-157">Parameter</span></span>   | <span data-ttu-id="b0f9e-158">Değer</span><span class="sxs-lookup"><span data-stu-id="b0f9e-158">Value</span></span>                                                |
   |-------------|------------------------------------------------------|
   | <span data-ttu-id="b0f9e-159">Ana sınıf</span><span class="sxs-lookup"><span data-stu-id="b0f9e-159">Main Class</span></span>  | <span data-ttu-id="b0f9e-160">org. Apache. spark. deploy. DotNet. DotnetRunner</span><span class="sxs-lookup"><span data-stu-id="b0f9e-160">org.apache.spark.deploy.dotnet.DotnetRunner</span></span>          |
   | <span data-ttu-id="b0f9e-161">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0f9e-161">Arguments</span></span>   | <span data-ttu-id="b0f9e-162">/dBFS/Apps/<-app-name >. zip <-App-Main-sınıfınızın ></span><span class="sxs-lookup"><span data-stu-id="b0f9e-162">/dbfs/apps/<your-app-name>.zip <your-app-main-class></span></span> |

4. <span data-ttu-id="b0f9e-163">**Kümeyi** , önceki bölümde Için **Init betiğini** oluşturduğunuz var olan kümeye işaret etmek üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-163">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="b0f9e-164">Uygulamanızı yayımlayın ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b0f9e-164">Publish and run your app</span></span>

1. <span data-ttu-id="b0f9e-165">Uygulamanızı Databricks kümenize yüklemek için [DATABRICKS CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-165">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="b0f9e-166">Bu adım yalnızca, uygulama derlemelerinizin (örneğin, bağımlılıklarıyla birlikte Kullanıcı tanımlı işlevler içeren dll 'Ler) her **Microsoft. spark. Worker**çalışma dizinine yerleştirilmesi gereken durumlarda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-166">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="b0f9e-167">Uygulama derlemelerinizi Databricks kümenize yükleyin</span><span class="sxs-lookup"><span data-stu-id="b0f9e-167">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="b0f9e-168">[DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) ' deki uygulama bağımlılıkları bölümünü Açıklama penceresinde, uygulama bağımlılıkları yolunu işaret edin ve Databricks kümenize yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-168">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="b0f9e-169">Kümenizi yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-169">Restart your cluster.</span></span>

3. <span data-ttu-id="b0f9e-170">Databricks çalışma alanınızdaki Databricks kümenize gidin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="b0f9e-171">**İşler**altında işiniz ' ı seçin ve ardından işi çalıştırmak Için **Şimdi Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="b0f9e-172">Spark-gönder kullan</span><span class="sxs-lookup"><span data-stu-id="b0f9e-172">Use spark-submit</span></span>

<span data-ttu-id="b0f9e-173">[Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutu, bir işi yeni bir kümeye göndermenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-173">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="b0f9e-174">[Bir Iş oluşturun](https://docs.databricks.com/user-guide/jobs.html) ve **Spark-gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-174">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="b0f9e-175">Aşağıdaki parametrelerle `spark-submit` yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="b0f9e-175">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="b0f9e-176">Databricks çalışma alanınızdaki Databricks kümenize gidin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-176">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="b0f9e-177">**İşler**altında işiniz ' ı seçin ve ardından işi çalıştırmak Için **Şimdi Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-177">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b0f9e-178">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="b0f9e-178">Next steps</span></span>

<span data-ttu-id="b0f9e-179">Bu öğreticide, Apache Spark için .NET uygulamanızı Databricks 'e dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-179">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="b0f9e-180">Databricks hakkında daha fazla bilgi edinmek için Azure Databricks belgelerine ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="b0f9e-180">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0f9e-181">Azure Databricks belgeleri</span><span class="sxs-lookup"><span data-stu-id="b0f9e-181">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
