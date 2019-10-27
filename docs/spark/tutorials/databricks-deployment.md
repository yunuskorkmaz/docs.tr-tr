---
title: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı
description: Databricks 'e Apache Spark uygulamasının bir .NET uygulamasını nasıl dağıtacağınızı öğrenin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9e338886c68845d5f95e7beb0cd7ac3a729d3281
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961045"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="9ae86-103">Öğretici: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı</span><span class="sxs-lookup"><span data-stu-id="9ae86-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="9ae86-104">Bu öğreticide, tek tıklamayla kurulum, kolaylaştırılmış iş akışları ve işbirliği sağlayan etkileşimli çalışma alanı ile Apache Spark tabanlı bir analiz platformu olan Azure Databricks aracılığıyla Uygulamanızı buluta nasıl dağıtabileceğiniz öğretilir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="9ae86-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="9ae86-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> <span data-ttu-id="9ae86-106">Azure Databricks çalışma alanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ae86-106">Create an Azure Databricks workspace.</span></span>
> <span data-ttu-id="9ae86-107">Apache Spark için .NET uygulamanızı yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-107">Publish your .NET for Apache Spark app.</span></span>
> <span data-ttu-id="9ae86-108">Spark işi ve Spark kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ae86-108">Create a Spark job and Spark cluster.</span></span>
> <span data-ttu-id="9ae86-109">Uygulamanızı Spark kümesinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ae86-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="9ae86-110">Prerequisites</span></span>

<span data-ttu-id="9ae86-111">Başlamadan önce, aşağıdaki görevleri yapın:</span><span class="sxs-lookup"><span data-stu-id="9ae86-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="9ae86-112">Azure hesabınız yoksa [ücretsiz bir hesap](https://azure.microsoft.com/free/)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9ae86-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="9ae86-113">[Azure Portal](https://portal.azure.com/)oturum açın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="9ae86-114">[Apache Spark için .net ' i doldurun-10 dakikalık öğreticide kullanmaya başlayın](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="9ae86-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="9ae86-115">Azure Databricks çalışma alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ae86-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="9ae86-116">Bu öğretici **Azure Ücretsiz deneme aboneliği**kullanılarak gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="9ae86-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="9ae86-117">Ücretsiz hesabınız varsa, profilinize gidin ve aboneliğinizi **Kullandıkça Öde**ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="9ae86-118">Daha fazla bilgi için bkz. [Azure Ücretsiz hesabı](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="9ae86-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="9ae86-119">Ardından, [harcama limitini kaldırın](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)ve bölgenizdeki vCPU 'lar için [bir kota artışı isteyin](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) .</span><span class="sxs-lookup"><span data-stu-id="9ae86-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="9ae86-120">Azure Databricks çalışma alanınızı oluşturduğunuzda, çalışma alanına 14 gün boyunca ücretsiz Premium Azure Databricks DBUs erişimi sağlamak için **deneme (Premium-14 gün ücretsiz DBUs)** fiyatlandırma katmanını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="9ae86-121">Bu bölümde, Azure portal kullanarak bir Azure Databricks çalışma alanı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="9ae86-122">Azure portal > **Analytics** > Azure Databricks **kaynak oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Azure portal Azure Databricks kaynak oluşturma](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="9ae86-124">**Azure Databricks hizmeti**altında, Databricks çalışma alanı oluşturmak için değerleri girin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>
    
    |<span data-ttu-id="9ae86-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="9ae86-125">Property</span></span>  |<span data-ttu-id="9ae86-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ae86-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="9ae86-127">**Çalışma alanı adı**</span><span class="sxs-lookup"><span data-stu-id="9ae86-127">**Workspace name**</span></span>     | <span data-ttu-id="9ae86-128">Databricks çalışma alanınız için bir ad sağlayın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="9ae86-129">**Aboneliğiniz**</span><span class="sxs-lookup"><span data-stu-id="9ae86-129">**Subscription**</span></span>     | <span data-ttu-id="9ae86-130">Açılan listeden Azure aboneliğinizi seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="9ae86-131">**Kaynak grubu**</span><span class="sxs-lookup"><span data-stu-id="9ae86-131">**Resource group**</span></span>     | <span data-ttu-id="9ae86-132">Yeni bir kaynak grubu oluşturmak mı yoksa mevcut bir kaynak grubu mı kullanmak istediğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="9ae86-133">Kaynak grubu, bir Azure çözümü için ilgili kaynakları tutan bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="9ae86-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="9ae86-134">Daha fazla bilgi için bkz. [Azure Kaynak grubuna genel bakış](/azure/azure-databricks/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="9ae86-134">For more information, see [Azure Resource Group overview](/azure/azure-databricks/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="9ae86-135">**Konum**</span><span class="sxs-lookup"><span data-stu-id="9ae86-135">**Location**</span></span>     | <span data-ttu-id="9ae86-136">Tercih ettiğiniz bölgeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-136">Select your preferred region.</span></span> <span data-ttu-id="9ae86-137">Kullanılabilir bölgeler hakkında daha fazla bilgi için bkz. [bölgeye göre kullanılabilir Azure hizmetleri](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="9ae86-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="9ae86-138">**Fiyatlandırma Katmanı**</span><span class="sxs-lookup"><span data-stu-id="9ae86-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="9ae86-139">**Standart**, **Premium**veya **deneme**arasında seçim yapın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="9ae86-140">Bu katmanlar hakkında daha fazla bilgi için bkz. [Databricks fiyatlandırma sayfası](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="9ae86-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="9ae86-141">**Sanal ağ**</span><span class="sxs-lookup"><span data-stu-id="9ae86-141">**Virtual Network**</span></span>     |   <span data-ttu-id="9ae86-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="9ae86-142">No</span></span>       |

3. <span data-ttu-id="9ae86-143">**Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-143">Select **Create**.</span></span> <span data-ttu-id="9ae86-144">Çalışma alanı oluşturma birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="9ae86-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="9ae86-145">Çalışma alanı oluşturma sırasında, **Bildirimler**' de dağıtım durumunu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="9ae86-146">Azure Databricks araçları 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="9ae86-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="9ae86-147">**Databricks CLI** kullanarak Azure Databricks kümelerine bağlanabilir ve dosyaları yerel makinenizden bunlara yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="9ae86-148">Databricks kümeleri, DBFS (Databricks dosya sistemi) üzerinden dosyalara erişim.</span><span class="sxs-lookup"><span data-stu-id="9ae86-148">Databricks clusters access files through DBFS (Databricks File System).</span></span> 

1. <span data-ttu-id="9ae86-149">Databricks CLı, Python 3,6 veya üstünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="9ae86-150">Zaten Python yüklüyse, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-150">If you already have Python installed, you can skip this step.</span></span>
 
   <span data-ttu-id="9ae86-151">**Windows için:**</span><span class="sxs-lookup"><span data-stu-id="9ae86-151">**For Windows:**</span></span>

   [<span data-ttu-id="9ae86-152">Windows için Python indirin</span><span class="sxs-lookup"><span data-stu-id="9ae86-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="9ae86-153">**Linux için:** Python, çoğu Linux dağıtımlarına önceden yüklenmiş olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="9ae86-154">Hangi sürümü yüklecağınızı görmek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9ae86-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="9ae86-155">Databricks CLı 'yı yüklemek için PIP kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="9ae86-156">Python 3,4 ve üzeri, varsayılan olarak PIP 'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="9ae86-157">Python 3 için pip3 kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="9ae86-158">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9ae86-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="9ae86-159">Databricks CLı 'yı yükledikten sonra yeni bir komut istemi açın ve `databricks`komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="9ae86-160">**' Databricks ' bir iç veya dış komut hatası olarak tanınmazsa**, yeni bir komut istemi açtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9ae86-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="9ae86-161">Azure Databricks ayarlama</span><span class="sxs-lookup"><span data-stu-id="9ae86-161">Set up Azure Databricks</span></span>

<span data-ttu-id="9ae86-162">Databricks CLı yükleolduğunuza göre, kimlik doğrulama ayrıntılarını ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="9ae86-163">Databricks CLı komutunu `databricks configure --token`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="9ae86-164">Configure komutunu çalıştırdıktan sonra, bir ana bilgisayar girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="9ae86-165">Ana bilgisayar URL 'niz şu biçimi kullanır: **https://< \Location >. azuredatabricks. net**.</span><span class="sxs-lookup"><span data-stu-id="9ae86-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="9ae86-166">Örneğin, Azure Databricks hizmeti oluşturma sırasında **eastus2** seçtiyseniz, konak **https://eastus2.azuredatabricks.net** olur.</span><span class="sxs-lookup"><span data-stu-id="9ae86-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="9ae86-167">Ana bilgisayarınızı girdikten sonra bir belirteç girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="9ae86-168">Azure portal, Azure Databricks çalışma alanınızı başlatmak için **çalışma alanını Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Azure Databricks çalışma alanını Başlat](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="9ae86-170">Çalışma alanınızın giriş sayfasında **Kullanıcı ayarları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Azure Databricks çalışma alanındaki Kullanıcı ayarları](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="9ae86-172">Kullanıcı ayarları sayfasında, yeni bir belirteç oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="9ae86-173">Oluşturulan belirteci kopyalayın ve komut isteminize geri yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Azure Databricks çalışma alanında yeni erişim belirteci oluştur](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="9ae86-175">Artık oluşturduğunuz Azure Databricks kümelerine erişebiliyor ve dosyaları DBFS 'ye yükleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="9ae86-176">Çalışan bağımlılıklarını indir</span><span class="sxs-lookup"><span data-stu-id="9ae86-176">Download worker dependencies</span></span>

1. <span data-ttu-id="9ae86-177">Microsoft. spark. Worker, yazdığınız kullanıcı tanımlı işlevler (UDF 'ler) gibi uygulamanızı Apache Spark yürütmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9ae86-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="9ae86-178">[Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)öğesini indirin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="9ae86-179">*İnstall-Worker.sh* , Apache Spark bağımlı dosyaları için .net ' i kümenizin düğümlerine kopyalamanızı sağlayan bir betiktir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span> 

   <span data-ttu-id="9ae86-180">Yerel bilgisayarınızda **install-Worker.sh** adlı yeni bir dosya oluşturun ve GitHub 'da bulunan [install-Worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> 

3. <span data-ttu-id="9ae86-181">*DB-init.sh* , Databricks Spark kümenize bağımlılıklar yükleyen bir betiktir.</span><span class="sxs-lookup"><span data-stu-id="9ae86-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="9ae86-182">Yerel bilgisayarınızda **DB-init.sh** adlı yeni bir dosya oluşturun ve GitHub 'da bulunan [DB-init.sh içeriğini](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span> 
   
   <span data-ttu-id="9ae86-183">Yeni oluşturduğunuz dosyada `DOTNET_SPARK_RELEASE` değişkenini `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="9ae86-184">*DB-init.sh* dosyasının kalan kısmını olduğu gibi bırakın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="9ae86-185">Windows kullanıyorsanız, *install-Worker.sh* ve *DB-init.sh* betiklerinizde yer alan satır SONLARıNı UNIX stili (LF) olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="9ae86-186">Satır sonlarını notepad + + ve atom gibi metin düzenleyicilerle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="9ae86-187">Uygulamanızı yayınlama</span><span class="sxs-lookup"><span data-stu-id="9ae86-187">Publish your app</span></span>

<span data-ttu-id="9ae86-188">Daha sonra, Spark kümenizin uygulamanızı çalıştırmak için gereken tüm dosyalara erişebildiğinden emin olmak için, Apache Spark .NET sürümünde oluşturulan *mySparkApp* [-Get ile çalışmaya](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) başlayın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span> 

1. <span data-ttu-id="9ae86-189">*MySparkApp*yayımlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9ae86-189">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="9ae86-190">**Windows 'da:**</span><span class="sxs-lookup"><span data-stu-id="9ae86-190">**On Windows:**</span></span>

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x6
   ```

   <span data-ttu-id="9ae86-191">**Linux 'ta:**</span><span class="sxs-lookup"><span data-stu-id="9ae86-191">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="9ae86-192">Dosyaları Databricks Spark kümenize kolayca yükleyebilmeniz için, yayımlanan uygulama dosyalarınızı Zip halinde aşağıdaki görevleri yapın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-192">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="9ae86-193">**Windows 'da:**</span><span class="sxs-lookup"><span data-stu-id="9ae86-193">**On Windows:**</span></span>

   <span data-ttu-id="9ae86-194">MySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64 dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-194">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="9ae86-195">Ardından, **Yayımla** klasörüne sağ tıklayıp **> Sıkıştırılmış (daraltılmış) klasöre gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-195">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="9ae86-196">Yeni klasörü **Publish. zip**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-196">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="9ae86-197">**Linux 'ta aşağıdaki komutu çalıştırın:**</span><span class="sxs-lookup"><span data-stu-id="9ae86-197">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="9ae86-198">Dosyaları karşıya yükleme</span><span class="sxs-lookup"><span data-stu-id="9ae86-198">Upload files</span></span>

<span data-ttu-id="9ae86-199">Bu bölümde, kümenizin uygulamanızı bulutta çalıştırması için gereken her şeyin olması için birkaç dosyayı DBFS 'ye yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-199">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="9ae86-200">DBFS 'ye bir dosya yüklediğinizde, dosyanın bilgisayarınızda bulunduğu dizinde olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9ae86-200">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="9ae86-201">*DB-init.sh*, *install-Worker.sh*ve *Microsoft. spark. Worker* öğesini dBFS 'ye yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9ae86-201">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="9ae86-202">Geri kalan dosyaları karşıya yüklemek için aşağıdaki komutları çalıştırın: kümenizin uygulamanızı çalıştırması gerekir: daraltılmış yayımlama klasörü, *Input. txt*ve *Microsoft-Spark-2,4. x-0.3.0. jar*.</span><span class="sxs-lookup"><span data-stu-id="9ae86-202">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span> 

   ```console
   cd mySparkApp 
   databricks fs cp input.txt dbfs:/input.txt
   
   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory 
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="9ae86-203">İş oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ae86-203">Create a job</span></span>

<span data-ttu-id="9ae86-204">Uygulamanız, Apache Spark işleri için .NET çalıştırmak için kullandığınız komut olan **Spark-gönder**çalıştıran bir iş aracılığıyla Azure Databricks çalışır.</span><span class="sxs-lookup"><span data-stu-id="9ae86-204">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="9ae86-205">Azure Databricks çalışma alanınızda **işler** simgesini ve ardından **+ iş oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-205">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span> 

   ![Azure Databricks işi oluşturma](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="9ae86-207">İşiniz için bir başlık seçin ve ardından **Spark-gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-207">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Databricks için Spark-göndermeyi yapılandırma işi](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="9ae86-209">Aşağıdaki parametreleri iş yapılandırmasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-209">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="9ae86-210">Ardından **Onayla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-210">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="9ae86-211">Küme oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ae86-211">Create a cluster</span></span>

1. <span data-ttu-id="9ae86-212">İşinizin kümesini yapılandırmak için işinize gidin ve **Düzenle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-212">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="9ae86-213">Kümenizi **Spark 2.4.1**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-213">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="9ae86-214">Ardından, **Init betikleri** > **Gelişmiş Seçenekler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-214">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="9ae86-215">Init betiği yolunu `dbfs:/spark-dotnet/db-init.sh`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9ae86-215">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span> 

   ![Azure Databricks Spark kümesini yapılandırma](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="9ae86-217">Küme ayarlarınızı onaylamak için **Onayla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-217">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="9ae86-218">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9ae86-218">Run your app</span></span>

1. <span data-ttu-id="9ae86-219">İşinizi yeni yapılandırılmış Spark kümenizde çalıştırmak için işinize gidin ve **Şimdi Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-219">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="9ae86-220">İş kümesinin oluşturulması birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="9ae86-220">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="9ae86-221">Oluşturulduktan sonra işiniz gönderilir ve çıktıyı görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-221">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="9ae86-222">Sol menüden **kümeler** ' ı, sonra da işinizin adını ve çalıştırmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-222">Select **Clusters** from the left menu, and then the name and run of your job.</span></span> 

4. <span data-ttu-id="9ae86-223">İşinizin çıkışını görüntülemek için **sürücü günlükleri** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-223">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="9ae86-224">Uygulamanız yürütmeyi bitirdiğinde, başlangıç yerel çalıştırmasından standart çıkış konsoluna yazılan aynı sözcük sayısı tablosunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-224">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks iş çıkış tablosu](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="9ae86-226">Tebrikler, ilk .NET Apache Spark uygulamanızı bulutta çalıştırdık!</span><span class="sxs-lookup"><span data-stu-id="9ae86-226">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="9ae86-227">Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="9ae86-227">Clean up resources</span></span>

<span data-ttu-id="9ae86-228">Artık Databricks çalışma alanına ihtiyacınız yoksa, Azure portal Azure Databricks kaynağını silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-228">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="9ae86-229">Kaynak grubu adını da seçerek kaynak grubu sayfasını açabilir ve **kaynak grubunu sil**' i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ae86-229">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9ae86-230">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9ae86-230">Next steps</span></span>

<span data-ttu-id="9ae86-231">Bu öğreticide, Apache Spark için .NET uygulamanızı Databricks 'e dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="9ae86-231">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="9ae86-232">Databricks hakkında daha fazla bilgi edinmek için Azure Databricks belgelerine ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9ae86-232">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9ae86-233">Azure Databricks belgeleri</span><span class="sxs-lookup"><span data-stu-id="9ae86-233">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
