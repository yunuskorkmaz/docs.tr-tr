---
title: Databricks 'e Apache Spark iş için .NET gönderme
description: Spark-gönder ve ayarla jar kullanarak Databricks 'e yönelik bir .NET Apache Spark işi göndermeyi öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: bebd170a689d8ae56aa6c55486d70354da2437ea
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617775"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="c0fc5-103">Databricks 'e Apache Spark iş için .NET gönderme</span><span class="sxs-lookup"><span data-stu-id="c0fc5-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="c0fc5-104">.NET Apache Spark işlerini Databricks kümelerinde çalıştırabilirsiniz, ancak kullanıma hazır değildir.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-104">You can run your .NET for Apache Spark jobs on Databricks clusters, but it is not available out-of-the-box.</span></span> <span data-ttu-id="c0fc5-105">Apache Spark iş için .NET uygulamanızı Databricks 'e dağıtmanın iki yolu vardır: `spark-submit` ve jar 'Yi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-105">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="c0fc5-106">Spark-gönder kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="c0fc5-106">Deploy using spark-submit</span></span>

<span data-ttu-id="c0fc5-107">Apache Spark işleri için .NET 'i Databricks 'e göndermek için [Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-107">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="c0fc5-108">`spark-submit`yalnızca isteğe bağlı olarak oluşturulan bir kümeye gönderim yapılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-108">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="c0fc5-109">Databricks çalışma alanınıza gidin ve bir iş oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-109">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="c0fc5-110">İşiniz için bir başlık seçin ve ardından **Spark-gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-110">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="c0fc5-111">Aşağıdaki parametreleri iş yapılandırmasına yapıştırın ve **Onayla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-111">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="c0fc5-112">Yukarıdaki parametrenin içeriğini, belirli dosyalarınıza ve yapılandırmanıza göre güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-112">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="c0fc5-113">Örneğin, DBFS 'ye yüklediğiniz Microsoft. Spark jar dosyasının sürümüne başvurun ve uygulamanızın uygun adını ve yayımlanmış uygulama ZIP dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-113">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="c0fc5-114">İşinizin kümesini yapılandırmak için işinize gidin ve **Düzenle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-114">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="c0fc5-115">Dağıtımınızda kullanmak istediğiniz Apache Spark sürümüne göre Databricks Runtime sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-115">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="c0fc5-116">Ardından **Init betikleri > gelişmiş seçenekler**' i seçin ve Init betiği yolunu olarak ayarlayın `dbfs:/spark-dotnet/db-init.sh` .</span><span class="sxs-lookup"><span data-stu-id="c0fc5-116">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="c0fc5-117">Küme ayarlarınızı onaylamak için **Onayla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-117">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="c0fc5-118">İşinizi yeni yapılandırılmış Spark kümenizde çalıştırmak için işinize gidin ve **Şimdi Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-118">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="c0fc5-119">İş kümesinin oluşturulması birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-119">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="c0fc5-120">Oluşturulduktan sonra işiniz gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-120">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="c0fc5-121">Databricks çalışma alanınızın sol menüsünde **kümeler** ' ı seçerek çıktıyı görüntüleyebilir, ardından **sürücü günlükleri**' ni seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-121">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="c0fc5-122">Set jar kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="c0fc5-122">Deploy using Set Jar</span></span>

<span data-ttu-id="c0fc5-123">Alternatif olarak, databricks 'e Apache Spark işleri için .NET göndermek üzere Databricks çalışma alanınızda [set jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-123">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="c0fc5-124">*Set jar* , mevcut bir etkin kümeye iş gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-124">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="c0fc5-125">Tek seferlik kurulum</span><span class="sxs-lookup"><span data-stu-id="c0fc5-125">One-time setup</span></span>

1. <span data-ttu-id="c0fc5-126">Databricks kümenize gidin ve sol taraftaki menüden **işler** ' i ve ardından **jar ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-126">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="c0fc5-127">Uygun olanını karşıya yükleyin `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` .</span><span class="sxs-lookup"><span data-stu-id="c0fc5-127">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="c0fc5-128">Aşağıdaki parametreleri, yerine yayımladığınız yürütülebilir dosya için doğru adı içerecek şekilde değiştirin `<your-app-name>` :</span><span class="sxs-lookup"><span data-stu-id="c0fc5-128">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="c0fc5-129">Kümeyi, zaten init betiğini ayarlamış olduğunuz mevcut bir kümeye işaret etmek üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-129">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="c0fc5-130">Uygulamanızı yayımlayın ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c0fc5-130">Publish and run your app</span></span>

1. <span data-ttu-id="c0fc5-131">Uygulamanızı yayımladığınızdan ve uygulama kodunuzun kullanmadığından emin olun `SparkSession.Stop()` .</span><span class="sxs-lookup"><span data-stu-id="c0fc5-131">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="c0fc5-132">Uygulamanızı Databricks kümenize yüklemek için [DATABRICKS CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-132">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="c0fc5-133">Örneğin, yayımlanmış uygulamanızı kümenize yüklemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c0fc5-133">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="c0fc5-134">Uygulamanızda Kullanıcı tanımlı işlevleriniz varsa, bağımlılıklarıyla birlikte Kullanıcı tanımlı işlevler içeren dll 'Ler gibi uygulama derlemelerinin her bir *Microsoft. spark. Worker*çalışma dizinine yerleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-134">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="c0fc5-135">Uygulama derlemelerinizi Databricks kümenize yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c0fc5-135">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="c0fc5-136">[DB-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) ' deki uygulama bağımlılıkları bölümünü açıklama olarak değiştirin ve uygulama bağımlılıkları yolunu işaret edin.</span><span class="sxs-lookup"><span data-stu-id="c0fc5-136">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="c0fc5-137">Ardından, güncelleştirilmiş *DB-init.sh* , kümenize yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c0fc5-137">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="c0fc5-138">İşi çalıştırmak için **Şimdi çalıştırın > Databricks kümesi > işler > [iş-adı] Şimdi Çalıştır** .</span><span class="sxs-lookup"><span data-stu-id="c0fc5-138">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0fc5-139">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c0fc5-139">Next steps</span></span>

* [<span data-ttu-id="c0fc5-140">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="c0fc5-140">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="c0fc5-141">Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı</span><span class="sxs-lookup"><span data-stu-id="c0fc5-141">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="c0fc5-142">Azure Databricks Belgeleri</span><span class="sxs-lookup"><span data-stu-id="c0fc5-142">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
