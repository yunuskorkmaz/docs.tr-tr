---
title: Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma
description: Apache Spark uygulaması için bir .NET uygulamasını HDInsight'a nasıl dağıtacağınız keşfedin.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 77b57463375c36444532bdd383ec4b3bfe3ab056
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504168"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="2fba3-103">Öğretici: Apache Spark uygulaması için Bir .NET uygulamasını Azure HDInsight'a dağıtma</span><span class="sxs-lookup"><span data-stu-id="2fba3-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="2fba3-104">Bu öğretici, Bir Azure HDInsight kümesi aracılığıyla .NET for Apache Spark uygulamanızı buluta nasıl dağıtacağınız öğretilir.</span><span class="sxs-lookup"><span data-stu-id="2fba3-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="2fba3-105">HDInsight'taki Spark kümeleri Azure Depolama ve Azure Veri Gölü Depolama ile uyumlu olduğundan HDInsight, Azure'da bir Kıvılcım kümesi oluşturmayı ve yapılandırmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="2fba3-106">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2fba3-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="2fba3-107">Azure Depolama Gezgini'ni kullanarak depolama hesaplarınıza erişin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="2fba3-108">Azure HDInsight kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2fba3-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="2fba3-109">Apache Spark uygulaması için .NET'inizi yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="2fba3-110">HDInsight komut dosyası eylemi oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="2fba3-111">Bir HDInsight kümesinde Apache Spark uygulaması için bir .NET çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2fba3-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2fba3-112">Prerequisites</span></span>

<span data-ttu-id="2fba3-113">Başlamadan önce aşağıdaki görevleri yapın:</span><span class="sxs-lookup"><span data-stu-id="2fba3-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="2fba3-114">Azure aboneliğiniz yoksa, ücretsiz bir [hesap](https://azure.microsoft.com/free/)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2fba3-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="2fba3-115">[Azure portalında](https://portal.azure.com/)oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="2fba3-116">Azure Depolama Gezgini'ni [Windows,](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409) [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)veya [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) bilgisayarınıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="2fba3-117">[Apache Spark için .NET](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) 'i tamamlayın - 10 Dakikalık eğitimde başlayın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="2fba3-118">Depolama hesaplarınıza erişin</span><span class="sxs-lookup"><span data-stu-id="2fba3-118">Access your storage accounts</span></span>

1. <span data-ttu-id="2fba3-119">Azure Depolama Gezgini'ni açın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="2fba3-120">Sol menüde **Hesap Ekle'yi** seçin ve Azure hesabınızda oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Depolama Gezgini'nden Azure hesabında oturum açma](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="2fba3-122">Oturum açmadan sonra, sahip olduğunuz tüm depolama hesaplarını ve depolama hesaplarınıza yüklediğiniz kaynakları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fba3-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="2fba3-123">HDInsight kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="2fba3-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fba3-124">HDInsight kümelerinin faturalandırması, kullanmasanız bile dakika başına eşit olarak dağılır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="2fba3-125">Kullanmayı bitirdikten sonra kümenizi sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fba3-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="2fba3-126">Daha fazla bilgi için bu öğreticinin [kaynakları temizle](#clean-up-resources) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="2fba3-127">Azure [portalını](https://portal.azure.com)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="2fba3-128">**+ Kaynak oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="2fba3-129">Ardından, **Analytics** kategorisinden **HDInsight'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Azure portalından HDInsight kaynağı oluşturma](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="2fba3-131">**Temel Bilgiler** bölümünde aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="2fba3-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="2fba3-132">Özellik</span><span class="sxs-lookup"><span data-stu-id="2fba3-132">Property</span></span>  |<span data-ttu-id="2fba3-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fba3-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="2fba3-134">Abonelik</span><span class="sxs-lookup"><span data-stu-id="2fba3-134">Subscription</span></span>  | <span data-ttu-id="2fba3-135">Açılan noktadan, etkin Azure aboneliklerinizden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="2fba3-136">Kaynak grubu</span><span class="sxs-lookup"><span data-stu-id="2fba3-136">Resource group</span></span> | <span data-ttu-id="2fba3-137">Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="2fba3-138">Kaynak grubu, bir Azure çözümü için ilgili kaynakları bir arada tutan kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="2fba3-139">Küme adı</span><span class="sxs-lookup"><span data-stu-id="2fba3-139">Cluster name</span></span> | <span data-ttu-id="2fba3-140">HDInsight Spark kümenize bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="2fba3-141">Konum</span><span class="sxs-lookup"><span data-stu-id="2fba3-141">Location</span></span>   | <span data-ttu-id="2fba3-142">Kaynak grubu için bir konum seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-142">Select a location for the resource group.</span></span> <span data-ttu-id="2fba3-143">Şablon hem kümeyi oluşturmak için hem de varsayılan küme depolaması için bu konumu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="2fba3-144">Küme türü</span><span class="sxs-lookup"><span data-stu-id="2fba3-144">Cluster type</span></span>| <span data-ttu-id="2fba3-145">Küme türü olarak **Spark'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="2fba3-146">Küme sürümü</span><span class="sxs-lookup"><span data-stu-id="2fba3-146">Cluster version</span></span>|<span data-ttu-id="2fba3-147">Küme türü seçildikten sonra bu alan varsayılan sürümle otomatik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2fba3-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="2fba3-148">Kıvılcım'ın 2.3 veya 2.4 sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="2fba3-149">Küme oturum açma kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="2fba3-149">Cluster login username</span></span>| <span data-ttu-id="2fba3-150">Küme oturum açma kullanıcı adını girin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-150">Enter the cluster login username.</span></span>  <span data-ttu-id="2fba3-151">Varsayılan ad, *admin* şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2fba3-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="2fba3-152">Küme oturum açma parolası</span><span class="sxs-lookup"><span data-stu-id="2fba3-152">Cluster login password</span></span>| <span data-ttu-id="2fba3-153">Herhangi bir giriş parolası girin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-153">Enter any login password.</span></span> |
    |<span data-ttu-id="2fba3-154">Secure Shell (SSH) kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="2fba3-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="2fba3-155">SSH kullanıcı adını girin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-155">Enter the SSH username.</span></span> <span data-ttu-id="2fba3-156">Varsayılan olarak bu hesap, *Küme Oturum Açma kullanıcı adı* hesabıyla aynı parolayı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="2fba3-157">**Sonraki'ni seçin:** **Depolama** sayfasına devam etmek için Depolama >>.</span><span class="sxs-lookup"><span data-stu-id="2fba3-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="2fba3-158">**Depolama** bölümünde aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="2fba3-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="2fba3-159">Özellik</span><span class="sxs-lookup"><span data-stu-id="2fba3-159">Property</span></span>  |<span data-ttu-id="2fba3-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fba3-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="2fba3-161">Birincil depolama türü</span><span class="sxs-lookup"><span data-stu-id="2fba3-161">Primary storage type</span></span>|<span data-ttu-id="2fba3-162">Varsayılan değeri kullanın **Azure Depolama**.</span><span class="sxs-lookup"><span data-stu-id="2fba3-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="2fba3-163">Seçim yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fba3-163">Selection method</span></span>|<span data-ttu-id="2fba3-164">Varsayılan değeri kullanın **Listeden seçin.**</span><span class="sxs-lookup"><span data-stu-id="2fba3-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="2fba3-165">Birincil depolama hesabı</span><span class="sxs-lookup"><span data-stu-id="2fba3-165">Primary storage account</span></span>|<span data-ttu-id="2fba3-166">Aboneliğinizi ve bu abonelik içindeki etkin depolama hesaplarınızdan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="2fba3-167">Kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="2fba3-167">Container</span></span>|<span data-ttu-id="2fba3-168">Bu kapsayıcı, kümenizin uygulamanızı bulutta çalıştırmak için dosyaları aradığı depolama hesabınızdaki özel blob kapsayıcısır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="2fba3-169">Herhangi bir kullanılabilir ad verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fba3-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="2fba3-170">**İnceleme altında + oluştur**, **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="2fba3-171">Kümenin oluşturulması yaklaşık 20 dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="2fba3-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="2fba3-172">Bir sonraki adıma devam etmeden önce kümenin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fba3-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="2fba3-173">Uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="2fba3-173">Publish your app</span></span>

<span data-ttu-id="2fba3-174">Ardından, [Apache Spark için .NET'te](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) oluşturulan *mySparkApp'ı* yayınlarsınız - 10 Dakikalık eğitimde başlayın, bu da Spark kümenize uygulamanızı çalıştırmak için gereken tüm dosyalara erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fba3-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="2fba3-175">*mySparkApp'ı*yayınlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2fba3-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="2fba3-176">**Windows'da:**</span><span class="sxs-lookup"><span data-stu-id="2fba3-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="2fba3-177">**Linux üzerinde:**</span><span class="sxs-lookup"><span data-stu-id="2fba3-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="2fba3-178">HdInsight kümenize kolayca yükleyebilmeniz için yayınlanmış uygulama dosyalarınızı fermuarlamak için aşağıdaki görevleri yapın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="2fba3-179">**Windows'da:**</span><span class="sxs-lookup"><span data-stu-id="2fba3-179">**On Windows:**</span></span>

   <span data-ttu-id="2fba3-180">*mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*adresinden ulaş.</span><span class="sxs-lookup"><span data-stu-id="2fba3-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="2fba3-181">Ardından, **Yayımla** klasörüne sağ tıklayın ve **> sıkıştırılmış (sıkıştırılmış) klasöre gönder'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="2fba3-182">Yeni **klasörpublish.zip**adı .</span><span class="sxs-lookup"><span data-stu-id="2fba3-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="2fba3-183">**Linux'ta aşağıdaki komutu çalıştırın:**</span><span class="sxs-lookup"><span data-stu-id="2fba3-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="2fba3-184">Dosyaları Azure'a yükleme</span><span class="sxs-lookup"><span data-stu-id="2fba3-184">Upload files to Azure</span></span>

<span data-ttu-id="2fba3-185">Ardından, kümenizin depolama alanı için seçtiğiniz blob kapsayıcısına aşağıdaki beş dosyayı yüklemek için Azure Depolama Gezgini'ni kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="2fba3-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="2fba3-186">Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="2fba3-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="2fba3-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="2fba3-187">install-worker.sh</span></span>
* <span data-ttu-id="2fba3-188">publish.zip</span><span class="sxs-lookup"><span data-stu-id="2fba3-188">publish.zip</span></span>
* <span data-ttu-id="2fba3-189">microsoft-kıvılcım-2.3.x-0.3.0.jar</span><span class="sxs-lookup"><span data-stu-id="2fba3-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="2fba3-190">input.txt.</span><span class="sxs-lookup"><span data-stu-id="2fba3-190">input.txt.</span></span>

1. <span data-ttu-id="2fba3-191">Azure Depolama Gezgini'ni açın ve sol menüden depolama hesabınıza gidin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="2fba3-192">Depolama hesabınızdaki **Blob Containers** altında kümeniz için blob konteynerine kadar inin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="2fba3-193">*Microsoft.Spark.Worker,* yazdığınız kullanıcı tanımlı işlevler (UDF' ler) gibi Apache Spark'ın uygulamanızı yürütmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="2fba3-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="2fba3-194">[Microsoft.Spark.Worker'ı](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)karşıdan yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="2fba3-195">Ardından, çalışanı yüklemek için Azure Depolama Gezgini'nde **Yükle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Dosyaları Azure Depolama Gezgini'ne yükleme](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="2fba3-197">*install-worker.sh,* Apache Spark bağımlı dosyaları için .NET'i kümenizin düğümlerine kopyalamanızı sağlayan bir komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="2fba3-198">Yerel bilgisayarınız **install-worker.sh** adlı yeni bir dosya oluşturun ve GitHub'da bulunan [install-worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="2fba3-199">Ardından, *blob* kabına install-worker.sh yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="2fba3-200">Kümenizin, uygulamanızın yayınlanmış dosyalarını içeren publish.zip dosyasına ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="2fba3-201">Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**adresine gidin ve **publish.zip'i**bulun.</span><span class="sxs-lookup"><span data-stu-id="2fba3-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="2fba3-202">Sonra blob konteyner *publish.zip* yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="2fba3-203">Kümenizin bir kavanoz dosyasına paketlenmiş uygulama koduna ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="2fba3-204">Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, ve **microsoft-spark-2.3.x-0.3.0.jar.**</span><span class="sxs-lookup"><span data-stu-id="2fba3-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="2fba3-205">Sonra, damla konteyner için kavanoz dosyası yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="2fba3-206">Birden fazla .jar dosyası olabilir (2.3.x ve Kıvılcım'ın 2.4.x sürümleri için).</span><span class="sxs-lookup"><span data-stu-id="2fba3-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="2fba3-207">Küme oluşturma sırasında seçtiğiniz Kıvılcım sürümüyle eşleşen .jar dosyasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fba3-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="2fba3-208">Örneğin, küme oluşturma sırasında Spark 2.3.2'yi seçtiyseniz *microsoft-spark-2.3.x-0.3.0.jar'ı* seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="2fba3-209">Kümenizin uygulamanıza girişe ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="2fba3-210">**mySparkApp** dizininize gidin ve **input.txt'yi**bulun.</span><span class="sxs-lookup"><span data-stu-id="2fba3-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="2fba3-211">Giriş dosyanızı blob kapsayıcınızdaki **kullanıcı/sshuser** dizinine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="2fba3-212">SSh aracılığıyla kümenize bağlanabileceksiniz ve bu klasör kümenizin girişini aradığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="2fba3-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="2fba3-213">*Input.txt* dosyası, belirli bir dizine yüklenen tek dosyadır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="2fba3-214">HDInsight komut dosyası eylemini çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2fba3-214">Run the HDInsight script action</span></span>

<span data-ttu-id="2fba3-215">Kümeniz çalıştığında ve dosyalarınızı Azure'a yükledikten sonra, kümedeki **install-worker.sh** komut dosyasını çalıştırMış sınız.</span><span class="sxs-lookup"><span data-stu-id="2fba3-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="2fba3-216">Azure portalında HDInsight Spark kümenize gidin ve ardından **Komut Dosyası eylemlerini**seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="2fba3-217">Select **+ Yeni gönder** ve aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="2fba3-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="2fba3-218">Özellik</span><span class="sxs-lookup"><span data-stu-id="2fba3-218">Property</span></span>  |<span data-ttu-id="2fba3-219">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fba3-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="2fba3-220">Komut dosyası türü</span><span class="sxs-lookup"><span data-stu-id="2fba3-220">Script type</span></span> |<span data-ttu-id="2fba3-221">Özel</span><span class="sxs-lookup"><span data-stu-id="2fba3-221">Custom</span></span>|
   | <span data-ttu-id="2fba3-222">Adı</span><span class="sxs-lookup"><span data-stu-id="2fba3-222">Name</span></span> | <span data-ttu-id="2fba3-223">İşçi Yükle</span><span class="sxs-lookup"><span data-stu-id="2fba3-223">Install Worker</span></span>|
   | <span data-ttu-id="2fba3-224">Bash script URI</span><span class="sxs-lookup"><span data-stu-id="2fba3-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="2fba3-225">Bu URI'yi onaylamak için Azure Depolama Gezgini'ndeki install-worker.sh sağ tıklayın ve Özellikler'i seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="2fba3-226">Düğüm türü(ler)</span><span class="sxs-lookup"><span data-stu-id="2fba3-226">Node type(s)</span></span>| <span data-ttu-id="2fba3-227">Işçi</span><span class="sxs-lookup"><span data-stu-id="2fba3-227">Worker</span></span>|
   | <span data-ttu-id="2fba3-228">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2fba3-228">Parameters</span></span> | <span data-ttu-id="2fba3-229">azure</span><span class="sxs-lookup"><span data-stu-id="2fba3-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="2fba3-230">/usr/yerel/bin</span><span class="sxs-lookup"><span data-stu-id="2fba3-230">/usr/local/bin</span></span>

3. <span data-ttu-id="2fba3-231">Komut dosyanızı göndermek için **Oluştur'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="2fba3-232">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2fba3-232">Run your app</span></span>

1. <span data-ttu-id="2fba3-233">Azure portalında HDInsight Spark kümenize gidin ve ardından **SSH + Cluster oturum açma'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="2fba3-234">Ssh giriş bilgilerini kopyalayın ve girişi bir terminale yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="2fba3-235">Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="2fba3-236">Ubuntu ve Spark'a hoş geldin mesajları görmelisin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="2fba3-237">UYGULAMANIZI HDInsight kümenizde çalıştırmak için **kıvılcım gönder** komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="2fba3-238">Örnek komut dosyasındaki **mycontainer** ve **mystorage account'u** blob kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2fba3-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="2fba3-239">Uygulamanız çalıştığında, konsola yazılan yerel çalıştırmaya başlarken aynı sözcük sayısı tablosunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="2fba3-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="2fba3-240">Tebrikler, bulutta Apache Spark uygulaması için ilk .NET'inizi çalıştırdınız!</span><span class="sxs-lookup"><span data-stu-id="2fba3-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="2fba3-241">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="2fba3-241">Clean up resources</span></span>

<span data-ttu-id="2fba3-242">HDInsight verilerinizi Azure Depolama'ya kaydeder, böylece kullanılmadığı bir kümeyi güvenle silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fba3-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="2fba3-243">Ayrıca, kullanılmıyorken dahi HDInsight kümesi için sizden ücret kesilir.</span><span class="sxs-lookup"><span data-stu-id="2fba3-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="2fba3-244">Küme ücretleri depolama ücretlerinin birkaç katı olduğundan, kullanılmadığında kümelerin silinmesi mantıklı olandır.</span><span class="sxs-lookup"><span data-stu-id="2fba3-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="2fba3-245">Kaynak grubu adını seçerek de kaynak grubu sayfasını açabilir ve sonra **Kaynak grubunu sil**’i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2fba3-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="2fba3-246">Kaynak grubunu silerek hem HDInsight Spark kümesini hem de varsayılan depolama hesabını silersiniz.</span><span class="sxs-lookup"><span data-stu-id="2fba3-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2fba3-247">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2fba3-247">Next steps</span></span>

<span data-ttu-id="2fba3-248">Bu eğitimde, .NET for Apache Spark uygulamanızı Azure HDInsight'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="2fba3-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="2fba3-249">HDInsight hakkında daha fazla bilgi edinmek için Azure HDInsight Belgelerine devam edin.</span><span class="sxs-lookup"><span data-stu-id="2fba3-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2fba3-250">Azure HDInsight Belgeleri</span><span class="sxs-lookup"><span data-stu-id="2fba3-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
