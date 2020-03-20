---
title: Databricks'e Apache Spark işi için bir .NET gönderme
description: Spark gönder ve Jar'ı Ayarla'yı kullanarak Databricks'e Apache Spark için bir .NET işini nasıl göndereceğinizi öğrenin.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187604"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a><span data-ttu-id="50b20-103">Databricks'e Apache Spark işi için bir .NET gönderme</span><span class="sxs-lookup"><span data-stu-id="50b20-103">Submit a .NET for Apache Spark job to Databricks</span></span>

<span data-ttu-id="50b20-104">Apache Spark için .NET işinizi Databricks'e `spark-submit` dağıtmanın iki yolu vardır: ve Jar'ı Ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="50b20-104">There are two ways to deploy your .NET for Apache Spark job to Databricks: `spark-submit` and Set Jar.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="50b20-105">Kıvılcım gönder'i kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="50b20-105">Deploy using spark-submit</span></span>

<span data-ttu-id="50b20-106">Apache [Spark](https://spark.apache.org/docs/latest/submitting-applications.html) işleri için .NET'i Databricks'e göndermek için kıvılcım gönder komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50b20-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="50b20-107">`spark-submit`yalnızca isteğe bağlı oluşturulan bir kümeye gönderilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="50b20-107">`spark-submit` allows submission only to a cluster that gets created on-demand.</span></span>

1. <span data-ttu-id="50b20-108">Databricks Çalışma Alanınıza gidin ve bir iş oluşturun.</span><span class="sxs-lookup"><span data-stu-id="50b20-108">Navigate to your Databricks Workspace and create a job.</span></span> <span data-ttu-id="50b20-109">İşiniz için bir başlık seçin ve ardından **kıvılcım gönder'i yapılandır'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="50b20-109">Choose a title for your job, and then select **Configure spark-submit**.</span></span> <span data-ttu-id="50b20-110">İş yapılandırmasında aşağıdaki parametreleri yapıştırın ve **onayla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="50b20-110">Paste the following parameters in the job configuration, then select **Confirm**.</span></span>

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > <span data-ttu-id="50b20-111">Yukarıdaki parametrenin içeriğini özel dosyalarınıza ve yapılandırmanıza göre güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="50b20-111">Update the contents of the above parameter based on your specific files and configuration.</span></span> <span data-ttu-id="50b20-112">Örneğin, DBFS'ye yüklediğiniz Microsoft.Spark kavanoz dosyasının sürümüne başvurun ve uygulamanızın uygun adını ve yayınlanan uygulama zip dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="50b20-112">For instance, reference the version of the Microsoft.Spark jar file that you uploaded to DBFS, and use the appropriate name of your app and published app zip file.</span></span>

2. <span data-ttu-id="50b20-113">İşinize gidin ve işinizin kümesini yapılandırmak için **Edit'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="50b20-113">Navigate to your job and select **Edit** to configure your job's cluster.</span></span> <span data-ttu-id="50b20-114">Databricks Runtime Sürümünü, dağıtımınızda kullanmak istediğiniz Apache Spark sürümünü temel alın.</span><span class="sxs-lookup"><span data-stu-id="50b20-114">Set the Databricks Runtime Version based on the version of Apache Spark you wish to use in your deployment.</span></span> <span data-ttu-id="50b20-115">Ardından **Gelişmiş Seçenekler > Init Komut Dosyaları'nı** `dbfs:/spark-dotnet/db-init.sh`seçin ve Komut Dosyası Yolunu 'da ' olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="50b20-115">Then select **Advanced Options > Init Scripts**, and set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> <span data-ttu-id="50b20-116">Küme ayarlarınızı onaylamak için **Onayla'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="50b20-116">Select **Confirm** to confirm your cluster settings.</span></span>

3. <span data-ttu-id="50b20-117">İşinize gidin ve yeni yapılandırılan Spark kümenizde işinizi çalıştırmak için **Şimdi Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="50b20-117">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span> <span data-ttu-id="50b20-118">İş kümesinin oluşturulması birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="50b20-118">It takes a few minutes for the job's cluster to be created.</span></span> <span data-ttu-id="50b20-119">Oluşturulduktan sonra, işiniz sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="50b20-119">Once it is created, your job will be submitted.</span></span> <span data-ttu-id="50b20-120">Databricks çalışma alanınızın sol menüsünden **Kümeler'i** seçerek çıktıyı görüntüleyebilir, ardından **Sürücü Günlükleri'ni**seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50b20-120">You can view the output by selecting **Clusters** from the left menu of your Databricks workspace, then select **Driver Logs**.</span></span>

## <a name="deploy-using-set-jar"></a><span data-ttu-id="50b20-121">Set Jar'ı kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="50b20-121">Deploy using Set Jar</span></span>

<span data-ttu-id="50b20-122">Alternatif olarak, Apache Spark işleri için .NET'i Databricks'e göndermek için Databricks çalışma alanınızdaki [Set Jar'ı](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50b20-122">Alternatively, you can use [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) in your Databricks workspace to submit .NET for Apache Spark jobs to Databricks.</span></span> <span data-ttu-id="50b20-123">*Set Jar* varolan bir etkin kümeye iş gönderme sağlar.</span><span class="sxs-lookup"><span data-stu-id="50b20-123">*Set Jar* allows job submission to an existing active cluster.</span></span>

### <a name="one-time-setup"></a><span data-ttu-id="50b20-124">Tek seferlik kurulum</span><span class="sxs-lookup"><span data-stu-id="50b20-124">One-time setup</span></span>

1. <span data-ttu-id="50b20-125">Databricks kümenize gidin ve sol taraftaki menüden **İş'leri** seçin ve ardından **JAR'ı ayarlayın.**</span><span class="sxs-lookup"><span data-stu-id="50b20-125">Navigate to your Databricks cluster and select **Jobs** from the left-side menu, followed by **Set JAR**.</span></span>

2. <span data-ttu-id="50b20-126">Yükleme uygun `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span><span class="sxs-lookup"><span data-stu-id="50b20-126">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`.</span></span>

3. <span data-ttu-id="50b20-127">Aşağıdaki parametreleri, aşağıdaki ler yerine yayınladığınız yürütülebilir `<your-app-name>`için doğru adı içerecek şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="50b20-127">Modify the following parameters to include the correct name for the executable that you published in place of `<your-app-name>`:</span></span>

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. <span data-ttu-id="50b20-128">Kümeyi, init komut dosyasını zaten ayarlamış olduğunuz varolan bir kümeye işaret etmek üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="50b20-128">Configure the cluster to point to an existing cluster for which you have already set the init script.</span></span>

### <a name="publish-and-run-your-app"></a><span data-ttu-id="50b20-129">Uygulamanızı yayımlayın ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="50b20-129">Publish and run your app</span></span>

1. <span data-ttu-id="50b20-130">Uygulamanızı yayımladığınızdan ve uygulama kodunuzu kullanmadığınızdan `SparkSession.Stop()`emin olun.</span><span class="sxs-lookup"><span data-stu-id="50b20-130">Ensure you have published your app, and that your application code does not use `SparkSession.Stop()`.</span></span>

2. <span data-ttu-id="50b20-131">Uygulamanızı Databricks kümenize yüklemek için [Databricks CLI'yi](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) kullanın.</span><span class="sxs-lookup"><span data-stu-id="50b20-131">Use [Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) to upload your application to your Databricks cluster.</span></span> <span data-ttu-id="50b20-132">Örneğin, yayınlanan uygulamanızı kümenize yüklemek için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="50b20-132">For example, use the following command to upload your published app to your cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. <span data-ttu-id="50b20-133">Uygulamanızda kullanıcı tanımlı işlevleriniz varsa, kullanıcı tanımlı işlevleri ve bağımlılıkları içeren DL'ler gibi uygulama derlemelerinin her *Microsoft.Spark.Worker'ın*çalışma dizinine yerleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="50b20-133">If you have any user-defined functions in your app, the app assemblies, such as DLLs that contain user-defined functions along with their dependencies, need to be placed in the working directory of each *Microsoft.Spark.Worker*.</span></span>

    <span data-ttu-id="50b20-134">Uygulama derlemelerinizi Databricks kümenize yükleyin:</span><span class="sxs-lookup"><span data-stu-id="50b20-134">Upload your application assemblies to your Databricks cluster:</span></span>

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    <span data-ttu-id="50b20-135">Uygulama bağımlılıkları yolunuza işaret etmek için [db-init.sh'daki](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) uygulama bağımlılıkları bölümünü açıklamave değiştirin.</span><span class="sxs-lookup"><span data-stu-id="50b20-135">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path.</span></span> <span data-ttu-id="50b20-136">Ardından, güncelleştirilmiş *db-init.sh* kümenize yükleyin:</span><span class="sxs-lookup"><span data-stu-id="50b20-136">Then, upload the updated *db-init.sh* to your cluster:</span></span>

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. <span data-ttu-id="50b20-137">İşinizi çalıştırmak için **Şimdi Çalıştır'> Iş > [İş adı] > Databricks kümesine** gidin.</span><span class="sxs-lookup"><span data-stu-id="50b20-137">Navigate to **Databricks cluster > Jobs > [Job-name] > Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="50b20-138">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="50b20-138">Next steps</span></span>

* [<span data-ttu-id="50b20-139">Apache Spark için .NET ile başlayın</span><span class="sxs-lookup"><span data-stu-id="50b20-139">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="50b20-140">Apache Spark uygulaması için Bir .NET'i Databricks'e dağıtma</span><span class="sxs-lookup"><span data-stu-id="50b20-140">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="50b20-141">Azure Databricks Dokümantasyon</span><span class="sxs-lookup"><span data-stu-id="50b20-141">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
