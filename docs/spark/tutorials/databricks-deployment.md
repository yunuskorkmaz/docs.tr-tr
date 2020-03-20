---
title: Apache Spark uygulaması için Bir .NET'i Databricks'e dağıtma
description: Apache Spark uygulaması için bir .NET uygulamasını Databricks'e nasıl dağıtacağınızkeşfedin.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5308530831fa288bf637849c1342f51769c3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77503968"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="e13fc-103">Öğretici: Databricks'e Apache Spark uygulaması için bir .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="e13fc-103">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="e13fc-104">Bu öğretici, tek tıklamayla kuruluma, kolaylaştırılmış iş akışlarına ve işbirliğine olanak tanıyan etkileşimli çalışma alanına sahip Apache Spark tabanlı bir analiz platformu olan Azure Databricks aracılığıyla uygulamanızı buluta nasıl dağıtacağınız öğretilir.</span><span class="sxs-lookup"><span data-stu-id="e13fc-104">This tutorial teaches you how to deploy your app to the cloud through Azure Databricks, an Apache Spark-based analytics platform with one-click setup, streamlined workflows, and interactive workspace that enables collaboration.</span></span>

<span data-ttu-id="e13fc-105">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e13fc-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e13fc-106">Azure Databricks çalışma alanı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e13fc-106">Create an Azure Databricks workspace.</span></span>
> - <span data-ttu-id="e13fc-107">Apache Spark uygulaması için .NET'inizi yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-107">Publish your .NET for Apache Spark app.</span></span>
> - <span data-ttu-id="e13fc-108">Bir Kıvılcım iş ve Kıvılcım kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e13fc-108">Create a Spark job and Spark cluster.</span></span>
> - <span data-ttu-id="e13fc-109">Uygulamanızı Kıvılcım kümesinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-109">Run your app on the Spark cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e13fc-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e13fc-110">Prerequisites</span></span>

<span data-ttu-id="e13fc-111">Başlamadan önce aşağıdaki görevleri yapın:</span><span class="sxs-lookup"><span data-stu-id="e13fc-111">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="e13fc-112">Azure hesabınız yoksa, ücretsiz bir [hesap](https://azure.microsoft.com/free/)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e13fc-112">If you don't have an Azure account, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="e13fc-113">[Azure portalında](https://portal.azure.com/)oturum açın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-113">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="e13fc-114">[Apache Spark için .NET](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) 'i tamamlayın - 10 Dakikalık eğitimde başlayın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-114">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="create-an-azure-databricks-workspace"></a><span data-ttu-id="e13fc-115">Azure Databricks çalışma alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e13fc-115">Create an Azure Databricks workspace</span></span>

> [!Note]
> <span data-ttu-id="e13fc-116">Bu öğretici **Azure Ücretsiz Deneme Aboneliği**kullanılarak gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e13fc-116">This tutorial cannot be carried out using **Azure Free Trial Subscription**.</span></span>
> <span data-ttu-id="e13fc-117">Ücretsiz bir hesabınız varsa, profilinize gidin ve aboneliğinizi istediğiniz **kadar öde**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-117">If you have a free account, go to your profile and change your subscription to **pay-as-you-go**.</span></span> <span data-ttu-id="e13fc-118">Daha fazla bilgi için bkz. [Ücretsiz Azure hesabı](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="e13fc-118">For more information, see [Azure free account](https://azure.microsoft.com/free/).</span></span> <span data-ttu-id="e13fc-119">Ardından, [harcama sınırını kaldırın](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)ve bölgenizdeki VCPU'lar için kota artışı [isteyin.](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request)</span><span class="sxs-lookup"><span data-stu-id="e13fc-119">Then, [remove the spending limit](https://docs.microsoft.com/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit), and [request a quota increase](https://docs.microsoft.com/azure/azure-supportability/resource-manager-core-quotas-request) for vCPUs in your region.</span></span> <span data-ttu-id="e13fc-120">Azure Databricks çalışma alanınızı oluşturduğunuzda, çalışma alanına ücretsiz Premium Azure Databricks DBUs'a 14 gün süreyle erişim sağlamak için **Deneme (Premium - 14 Gün Ücretsiz DBUs)** fiyatlandırma katmanını seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-120">When you create your Azure Databricks workspace, you can select the **Trial (Premium - 14-Days Free DBUs)** pricing tier to give the workspace access to free Premium Azure Databricks DBUs for 14 days.</span></span>

<span data-ttu-id="e13fc-121">Bu bölümde Azure portalını kullanarak bir Azure Databricks çalışma alanı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-121">In this section, you create an Azure Databricks workspace using the Azure portal.</span></span>

1. <span data-ttu-id="e13fc-122">Azure portalında, **bir kaynak** > Oluştur**Analytics** > **Azure Databricks'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-122">In the Azure portal, select **Create a resource** > **Analytics** > **Azure Databricks**.</span></span>

   ![Azure portalında Bir Azure Databricks kaynağı oluşturma](./media/databricks-deployment/create-databricks-resource.png)

2. <span data-ttu-id="e13fc-124">**Azure Databricks Hizmeti** bölümünde, Databricks çalışma alanı oluşturmak için değerler sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-124">Under **Azure Databricks Service**, provide the values to create a Databricks workspace.</span></span>

    |<span data-ttu-id="e13fc-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="e13fc-125">Property</span></span>  |<span data-ttu-id="e13fc-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e13fc-126">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="e13fc-127">**Çalışma alanı adı**</span><span class="sxs-lookup"><span data-stu-id="e13fc-127">**Workspace name**</span></span>     | <span data-ttu-id="e13fc-128">Databricks çalışma alanınız için bir ad sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-128">Provide a name for your Databricks workspace.</span></span>        |
    |<span data-ttu-id="e13fc-129">**Abonelik**</span><span class="sxs-lookup"><span data-stu-id="e13fc-129">**Subscription**</span></span>     | <span data-ttu-id="e13fc-130">Açılan listeden Azure aboneliğinizi seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-130">From the drop-down, select your Azure subscription.</span></span>        |
    |<span data-ttu-id="e13fc-131">**Kaynak grubu**</span><span class="sxs-lookup"><span data-stu-id="e13fc-131">**Resource group**</span></span>     | <span data-ttu-id="e13fc-132">Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-132">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="e13fc-133">Kaynak grubu, bir Azure çözümü için ilgili kaynakları bir arada tutan kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="e13fc-133">A resource group is a container that holds related resources for an Azure solution.</span></span> <span data-ttu-id="e13fc-134">Daha fazla bilgi için bkz. [Azure Kaynak Grubuna genel bakış](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="e13fc-134">For more information, see [Azure Resource Group overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> |
    |<span data-ttu-id="e13fc-135">**Konum**</span><span class="sxs-lookup"><span data-stu-id="e13fc-135">**Location**</span></span>     | <span data-ttu-id="e13fc-136">Tercih ettiğiniz bölgeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-136">Select your preferred region.</span></span> <span data-ttu-id="e13fc-137">Kullanılabilir bölgeler hakkında bilgi için, [bölgeye göre kullanılabilen Azure hizmetlerine](https://azure.microsoft.com/regions/services/)bakın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-137">For information about available regions, see [Azure services available by region](https://azure.microsoft.com/regions/services/).</span></span>        |
    |<span data-ttu-id="e13fc-138">**Fiyatlandırma Katmanı**</span><span class="sxs-lookup"><span data-stu-id="e13fc-138">**Pricing Tier**</span></span>     |  <span data-ttu-id="e13fc-139">**Standart,** **Premium**veya **Deneme**arasında seçim yapın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-139">Choose between **Standard**, **Premium**, or **Trial**.</span></span> <span data-ttu-id="e13fc-140">Bu katmanlar hakkında daha fazla bilgi için bkz. [Databricks fiyatlandırma sayfası](https://azure.microsoft.com/pricing/details/databricks/).</span><span class="sxs-lookup"><span data-stu-id="e13fc-140">For more information on these tiers, see [Databricks pricing page](https://azure.microsoft.com/pricing/details/databricks/).</span></span>       |
    |<span data-ttu-id="e13fc-141">**Sanal Ağ**</span><span class="sxs-lookup"><span data-stu-id="e13fc-141">**Virtual Network**</span></span>     |   <span data-ttu-id="e13fc-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="e13fc-142">No</span></span>       |

3. <span data-ttu-id="e13fc-143">**Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-143">Select **Create**.</span></span> <span data-ttu-id="e13fc-144">Çalışma alanının oluşturulması birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="e13fc-144">The workspace creation takes a few minutes.</span></span> <span data-ttu-id="e13fc-145">Çalışma alanı oluşturma sırasında, **Bildirimler'de**dağıtım durumunu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-145">During workspace creation, you can view the deployment status in **Notifications**.</span></span>

## <a name="install-azure-databricks-tools"></a><span data-ttu-id="e13fc-146">Azure Databricks araçlarını yükleme</span><span class="sxs-lookup"><span data-stu-id="e13fc-146">Install Azure Databricks tools</span></span>

<span data-ttu-id="e13fc-147">Azure Databricks kümelerine bağlanmak ve yerel makinenizden dosyalar yüklemek için **Databricks CLI'yi** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-147">You can use the **Databricks CLI** to connect to Azure Databricks clusters and upload files to them from your local machine.</span></span> <span data-ttu-id="e13fc-148">Databricks, DBFS (Databricks Dosya Sistemi) aracılığıyla erişim dosyalarını kümeler.</span><span class="sxs-lookup"><span data-stu-id="e13fc-148">Databricks clusters access files through DBFS (Databricks File System).</span></span>

1. <span data-ttu-id="e13fc-149">Databricks CLI Python 3.6 veya üzeri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e13fc-149">The Databricks CLI requires Python 3.6 or above.</span></span> <span data-ttu-id="e13fc-150">Python zaten yüklüyse, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-150">If you already have Python installed, you can skip this step.</span></span>

   <span data-ttu-id="e13fc-151">**Windows için:**</span><span class="sxs-lookup"><span data-stu-id="e13fc-151">**For Windows:**</span></span>

   [<span data-ttu-id="e13fc-152">Windows için Python'u İndirin</span><span class="sxs-lookup"><span data-stu-id="e13fc-152">Download Python for Windows</span></span>](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   <span data-ttu-id="e13fc-153">**Linux için:** Python çoğu Linux dağıtımında önceden yüklenmiş olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="e13fc-153">**For Linux:** Python comes preinstalled on most Linux distributions.</span></span> <span data-ttu-id="e13fc-154">Hangi sürümü yüklediğinizi görmek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e13fc-154">Run the following command to see which version you have installed:</span></span>

   ```bash
   python3 --version
   ```

2. <span data-ttu-id="e13fc-155">Databricks CLI'yi yüklemek için pip'i kullanın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-155">Use pip to install the Databricks CLI.</span></span> <span data-ttu-id="e13fc-156">Python 3.4 ve daha sonra varsayılan olarak pip içerir.</span><span class="sxs-lookup"><span data-stu-id="e13fc-156">Python 3.4 and later include pip by default.</span></span> <span data-ttu-id="e13fc-157">Python 3 için pip3 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-157">Use pip3 for Python 3.</span></span> <span data-ttu-id="e13fc-158">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e13fc-158">Run the following command:</span></span>

   ```bash
   pip3 install databricks-cli
   ```

3. <span data-ttu-id="e13fc-159">Databricks CLI'yi yükledikten sonra, yeni bir komut istemi `databricks`açın ve komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-159">Once you've installed the Databricks CLI, open a new command prompt and run the command `databricks`.</span></span> <span data-ttu-id="e13fc-160">Bir **'databricks'** alırsanız bir iç veya dış komut hatası olarak tanınmıyorsa, yeni bir komut istemi açtığınıza emin olun.</span><span class="sxs-lookup"><span data-stu-id="e13fc-160">If you receive a **'databricks' is not recognized as an internal or external command error**, make sure you opened a new command prompt.</span></span>

## <a name="set-up-azure-databricks"></a><span data-ttu-id="e13fc-161">Azure Veri Tuğlaları'nı ayarlama</span><span class="sxs-lookup"><span data-stu-id="e13fc-161">Set up Azure Databricks</span></span>

<span data-ttu-id="e13fc-162">Databricks CLI yüklü olduğundan, kimlik doğrulama ayrıntılarını ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e13fc-162">Now that you have the Databricks CLI installed, you need to set up authentication details.</span></span>

1. <span data-ttu-id="e13fc-163">Databricks CLI komutunu `databricks configure --token`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-163">Run the Databricks CLI command `databricks configure --token`.</span></span>

2. <span data-ttu-id="e13fc-164">Yapılandırma komutunu çalıştırdıktan sonra, bir ana bilgisayar girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="e13fc-164">After running the configure command, you are prompted to enter a host.</span></span> <span data-ttu-id="e13fc-165">Ana bilgisayar URL'niz şu biçimi kullanır: **https://<\Konum>.azuredatabricks.net**.</span><span class="sxs-lookup"><span data-stu-id="e13fc-165">Your host URL uses the format: **https://<\Location>.azuredatabricks.net**.</span></span> <span data-ttu-id="e13fc-166">Örneğin, Azure Databricks Hizmeti oluşturma sırasında **eastus2'yi** **https://eastus2.azuredatabricks.net**seçtiyseniz, ana bilgisayar .</span><span class="sxs-lookup"><span data-stu-id="e13fc-166">For instance, if you selected **eastus2** during Azure Databricks Service creation, the host would be **https://eastus2.azuredatabricks.net**.</span></span>

3. <span data-ttu-id="e13fc-167">Ana bilgisayarA girdikten sonra, bir belirteç girmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="e13fc-167">After entering your host, you are prompted to enter a token.</span></span> <span data-ttu-id="e13fc-168">Azure portalında, Azure Veri Tuğlaları çalışma alanınızı başlatmak için **Çalışma Alanını Başlat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-168">In the Azure portal, select **Launch Workspace** to launch your Azure Databricks workspace.</span></span>

   ![Azure Databricks Çalışma Alanını Başlat](./media/databricks-deployment/launch-databricks-workspace.png)

4. <span data-ttu-id="e13fc-170">Çalışma alanınızın ana sayfasında **Kullanıcı Ayarları'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-170">On the home page of your workspace, select **User Settings**.</span></span>

   ![Azure Databricks çalışma alanında kullanıcı ayarları](./media/databricks-deployment/databricks-user-settings.png)

5. <span data-ttu-id="e13fc-172">Kullanıcı Ayarları sayfasında yeni bir belirteç oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-172">On the User Settings page, you can generate a new token.</span></span> <span data-ttu-id="e13fc-173">Oluşturulan belirteci kopyalayın ve komut isteminize geri yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-173">Copy the generated token and paste it back into your command prompt.</span></span>

   ![Azure Databricks çalışma alanında yeni erişim belirteci oluşturma](./media/databricks-deployment/generate-token.png)

<span data-ttu-id="e13fc-175">Artık oluşturduğunuz Azure Veri Tuğlaları kümelerine erişebilmeli ve DBFS'ye dosya yükleyebilmelisin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-175">You should now be able to access any Azure Databricks clusters you create and upload files to the DBFS.</span></span>

## <a name="download-worker-dependencies"></a><span data-ttu-id="e13fc-176">Çalışan bağımlılıklarını karşıdan yükleme</span><span class="sxs-lookup"><span data-stu-id="e13fc-176">Download worker dependencies</span></span>

1. <span data-ttu-id="e13fc-177">Microsoft.Spark.Worker, yazdığınız kullanıcı tanımlı işlevler (UDF' ler) gibi Apache Spark'ın uygulamanızı yürütmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e13fc-177">Microsoft.Spark.Worker helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="e13fc-178">[Microsoft.Spark.Worker'ı](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz)karşıdan yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-178">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz).</span></span>

2. <span data-ttu-id="e13fc-179">*install-worker.sh,* Apache Spark bağımlı dosyaları için .NET'i kümenizin düğümlerine kopyalamanızı sağlayan bir komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e13fc-179">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="e13fc-180">Yerel bilgisayarınızda **install-worker.sh** adlı yeni bir dosya oluşturun ve GitHub'da bulunan [install-worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-180">Create a new file named **install-worker.sh** on your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span>

3. <span data-ttu-id="e13fc-181">*db-init.sh,* bağımlılıkları Databricks Spark kümenize yükleyen bir komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e13fc-181">The *db-init.sh* is a script that installs dependencies onto your Databricks Spark cluster.</span></span>

   <span data-ttu-id="e13fc-182">Yerel bilgisayarınızda **db-init.sh** adlı yeni bir dosya oluşturun ve GitHub'da bulunan [db-init.sh içeriğini](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-182">Create a new file named **db-init.sh** on your local computer, and paste the [db-init.sh contents](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) located on GitHub.</span></span>

   <span data-ttu-id="e13fc-183">Oluşturduğunuz dosyada değişkeni `DOTNET_SPARK_RELEASE` ' `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`ye göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-183">In the file you just created, set the `DOTNET_SPARK_RELEASE` variable to `https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz`.</span></span> <span data-ttu-id="e13fc-184">*db-init.sh* dosyanın geri kalanını olduğu gibi bırakın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-184">Leave the rest of the *db-init.sh* file as-is.</span></span>

> [!Note]
> <span data-ttu-id="e13fc-185">Windows kullanıyorsanız, *install-worker.sh* ve *db-init.sh* komut dosyalarınızdaki satır uçlarının Unix tarzı (LF) olduğundan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-185">If you are using Windows, verify that the line-endings in your *install-worker.sh* and *db-init.sh* scripts are Unix-style (LF).</span></span> <span data-ttu-id="e13fc-186">Not Defteri++ ve Atom gibi metin editörleri aracılığıyla satır sonlarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-186">You can change line endings through text editors like Notepad++ and Atom.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="e13fc-187">Uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="e13fc-187">Publish your app</span></span>

<span data-ttu-id="e13fc-188">Ardından, Spark kümenizin uygulamanızı çalıştırmak için ihtiyaç duyduğu tüm dosyalara erişebilmesini sağlamak [için .NET for Apache Spark - Get in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) öğreticisinde oluşturulan *mySparkApp'ı* yayınlarsınız.</span><span class="sxs-lookup"><span data-stu-id="e13fc-188">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial to ensure your Spark cluster has access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="e13fc-189">*mySparkApp'ı*yayınlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e13fc-189">Run the following commands to publish the *mySparkApp*:</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="e13fc-190">Yayınlanan uygulama dosyalarınızı veri tuğlaları Kıvılcım kümenize kolayca yükleyebilmeniz için aşağıdaki görevleri yapın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-190">Do the following tasks to zip your published app files so that you can easily upload them to your Databricks Spark cluster.</span></span>

   <span data-ttu-id="e13fc-191">**Windows'da:**</span><span class="sxs-lookup"><span data-stu-id="e13fc-191">**On Windows:**</span></span>

   <span data-ttu-id="e13fc-192">mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64 adresinden ulaşın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-192">Navigate to mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64.</span></span> <span data-ttu-id="e13fc-193">Ardından, **Yayımla** klasörüne sağ tıklayın ve **> sıkıştırılmış (sıkıştırılmış) klasöre gönder'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-193">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="e13fc-194">Yeni **klasörpublish.zip**adı .</span><span class="sxs-lookup"><span data-stu-id="e13fc-194">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="e13fc-195">**Linux'ta aşağıdaki komutu çalıştırın:**</span><span class="sxs-lookup"><span data-stu-id="e13fc-195">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a><span data-ttu-id="e13fc-196">Dosyaları karşıya yükleme</span><span class="sxs-lookup"><span data-stu-id="e13fc-196">Upload files</span></span>

<span data-ttu-id="e13fc-197">Bu bölümde, kümenizin uygulamanızı bulutta çalıştırmak için gereken her şeye sahip olması için DBFS'ye birkaç dosya yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-197">In this section, you upload several files to DBFS so that your cluster has everything it needs to run your app in the cloud.</span></span> <span data-ttu-id="e13fc-198">DBFS'ye her dosya yüklediğinizde, bu dosyanın bilgisayarınızda bulunduğu dizinde olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e13fc-198">Each time you upload a file to the DBFS, make sure you are in the directory where that file is located on your computer.</span></span>

1. <span data-ttu-id="e13fc-199">*db-init.sh,* *install-worker.sh*ve *Microsoft.Spark.Worker'ı* DBFS'ye yüklemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="e13fc-199">Run the following commands to upload the *db-init.sh*, *install-worker.sh*, and *Microsoft.Spark.Worker* to DBFS:</span></span>

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz dbfs:/spark-dotnet/   Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz
   ```

2. <span data-ttu-id="e13fc-200">Kümeuygulamanızı çalıştırmak için gereken kalan dosyaları yüklemek için aşağıdaki komutları çalıştırın: sıkıştırılmış yayımlama klasörü, *input.txt*ve *microsoft-spark-2.4.x-0.3.0.jar*.</span><span class="sxs-lookup"><span data-stu-id="e13fc-200">Run the following commands to upload the remaining files your cluster will need to run your app: the zipped publish folder, *input.txt*, and *microsoft-spark-2.4.x-0.3.0.jar*.</span></span>

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.0\ubuntu.16.04-x64 directory
   databricks fs cp mySparkApp.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2.4.x-0.6.0.jar dbfs:/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar
   ```

## <a name="create-a-job"></a><span data-ttu-id="e13fc-201">Bir iş oluşturma</span><span class="sxs-lookup"><span data-stu-id="e13fc-201">Create a job</span></span>

<span data-ttu-id="e13fc-202">Uygulamanız, Apache **Spark**işleri için .NET'i çalıştırmak için kullandığınız komut olan kıvılcım gönder'i çalıştıran bir iş aracılığıyla Azure Databricks'te çalışır.</span><span class="sxs-lookup"><span data-stu-id="e13fc-202">Your app runs on Azure Databricks through a job that runs **spark-submit**, which is the command you use to run .NET for Apache Spark jobs.</span></span>

1. <span data-ttu-id="e13fc-203">Azure Veri Tuğlaları Çalışma Alanınızda **İşler** simgesini seçin ve ardından **+ İş Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-203">In your Azure Databricks Workspace, select the **Jobs** icon and then **+ Create Job**.</span></span>

   ![Azure Databricks işi oluşturma](./media/databricks-deployment/create-job.png)

2. <span data-ttu-id="e13fc-205">İşiniz için bir başlık seçin ve ardından **kıvılcım gönder'i yapılandır'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-205">Choose a title for your job, and then select **Configure spark-submit**.</span></span>

   ![Databricks işi için kıvılcım gönderme yapılandırma](./media/databricks-deployment/configure-spark-submit.png)

3. <span data-ttu-id="e13fc-207">İş yapılandırmasında aşağıdaki parametreleri yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-207">Paste the following parameters in the job configuration.</span></span> <span data-ttu-id="e13fc-208">Ardından, **Onayla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-208">Then, select **Confirm**.</span></span>

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2.4.x-0.6.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a><span data-ttu-id="e13fc-209">Küme oluşturma</span><span class="sxs-lookup"><span data-stu-id="e13fc-209">Create a cluster</span></span>

1. <span data-ttu-id="e13fc-210">İşinize gidin ve işinizin kümesini yapılandırmak için **Edit'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-210">Navigate to your job and select **Edit** to configure your job's cluster.</span></span>

2. <span data-ttu-id="e13fc-211">Kümenizi **Spark 2.4.1**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e13fc-211">Set your cluster to **Spark 2.4.1**.</span></span> <span data-ttu-id="e13fc-212">Ardından, **Gelişmiş Seçenekler** > **Init Komut Dosyaları'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-212">Then, select **Advanced Options** > **Init Scripts**.</span></span> <span data-ttu-id="e13fc-213">Komut Dosyası Yolunu `dbfs:/spark-dotnet/db-init.sh`' n için ayarla.</span><span class="sxs-lookup"><span data-stu-id="e13fc-213">Set Init Script Path as `dbfs:/spark-dotnet/db-init.sh`.</span></span>

   ![Azure Veri Tuğlaları'nda kıvılcım kümesini yapılandırma](./media/databricks-deployment/cluster-config.png)

3. <span data-ttu-id="e13fc-215">Küme ayarlarınızı onaylamak için **Onayla'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-215">Select **Confirm** to confirm your cluster settings.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="e13fc-216">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e13fc-216">Run your app</span></span>

1. <span data-ttu-id="e13fc-217">İşinize gidin ve yeni yapılandırılan Spark kümenizde işinizi çalıştırmak için **Şimdi Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-217">Navigate to your job and select **Run Now** to run your job on your newly configured Spark cluster.</span></span>

2. <span data-ttu-id="e13fc-218">İş kümesinin oluşturması birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="e13fc-218">It takes a few minutes for the job's cluster to create.</span></span> <span data-ttu-id="e13fc-219">Oluşturulduktan sonra, işiniz gönderilecektir ve çıktıyı görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-219">Once it is created, your job will be submitted, and you can view the output.</span></span>

3. <span data-ttu-id="e13fc-220">Sol menüden **Kümeler'i** ve ardından işinizin adını ve çalışmasını seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-220">Select **Clusters** from the left menu, and then the name and run of your job.</span></span>

4. <span data-ttu-id="e13fc-221">İşinizin çıktısını görüntülemek için **Sürücü Günlükleri'ni** seçin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-221">Select **Driver Logs** to view the output of your job.</span></span> <span data-ttu-id="e13fc-222">Uygulamanız yürütmeyi bitirdiğinde, standart çıktı konsoluna yazılan yerel çalıştırmaya başlarken aynı sözcük sayısı tablosunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-222">When your app finishes executing, you see the same word count table from the getting started local run written to the standard output console.</span></span>

   ![Azure Databricks iş çıktıtablosu](./media/databricks-deployment/table-output.png)

   <span data-ttu-id="e13fc-224">Tebrikler, bulutta Apache Spark uygulaması için ilk .NET'inizi çalıştırdınız!</span><span class="sxs-lookup"><span data-stu-id="e13fc-224">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="e13fc-225">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="e13fc-225">Clean up resources</span></span>

<span data-ttu-id="e13fc-226">Databricks çalışma alanına artık ihtiyacınız yoksa, Azure portalındaki Azure Veri Tuğlaları kaynağınızı silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-226">If you no longer need the Databricks workspace, you can delete your Azure Databricks resource in the Azure portal.</span></span> <span data-ttu-id="e13fc-227">Kaynak grubu adını seçerek de kaynak grubu sayfasını açabilir ve sonra **Kaynak grubunu sil**’i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e13fc-227">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e13fc-228">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e13fc-228">Next steps</span></span>

<span data-ttu-id="e13fc-229">Bu eğitimde, .NET'inizi Apache Spark uygulaması için Databricks'e dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="e13fc-229">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="e13fc-230">Databricks hakkında daha fazla bilgi edinmek için Azure Veri Tuğlaları Dokümantasyonu'na devam edin.</span><span class="sxs-lookup"><span data-stu-id="e13fc-230">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e13fc-231">Azure Databricks Dokümantasyon</span><span class="sxs-lookup"><span data-stu-id="e13fc-231">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)
