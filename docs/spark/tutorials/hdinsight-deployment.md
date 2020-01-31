---
title: Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma
description: HDInsight için bir .NET Apache Spark uygulamasının nasıl dağıtılacağını öğrenin.
ms.date: 01/23/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 76a150879324640352aa36f753ec3d6e7342bcaf
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860784"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="718aa-103">Öğretici: Azure HDInsight 'a Apache Spark uygulaması için .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="718aa-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="718aa-104">Bu öğreticide, Azure HDInsight kümesi aracılığıyla Apache Spark için .NET uygulamanızı buluta nasıl dağıtacağınız öğretilir.</span><span class="sxs-lookup"><span data-stu-id="718aa-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="718aa-105">HDInsight 'ta Spark kümeleri Azure depolama ve Azure Data Lake Storage uyumlu olduğundan, HDInsight, Azure 'da Spark kümesi oluşturmayı ve yapılandırmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="718aa-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="718aa-106">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="718aa-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="718aa-107">Azure Depolama Gezgini kullanarak depolama hesaplarınıza erişin.</span><span class="sxs-lookup"><span data-stu-id="718aa-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="718aa-108">Azure HDInsight kümesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="718aa-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="718aa-109">Apache Spark için .NET uygulamanızı yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="718aa-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="718aa-110">HDInsight betik eylemi oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="718aa-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="718aa-111">HDInsight kümesinde Apache Spark uygulaması için bir .NET çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="718aa-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="718aa-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="718aa-112">Prerequisites</span></span>

<span data-ttu-id="718aa-113">Başlamadan önce, aşağıdaki görevleri yapın:</span><span class="sxs-lookup"><span data-stu-id="718aa-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="718aa-114">Azure aboneliğiniz yoksa [ücretsiz bir hesap](https://azure.microsoft.com/free/) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="718aa-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/).</span></span>
* <span data-ttu-id="718aa-115">[Azure Portal](https://portal.azure.com/)’ında oturum açın.</span><span class="sxs-lookup"><span data-stu-id="718aa-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="718aa-116">[Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)veya [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) bilgisayarınıza Azure Depolama Gezgini ' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="718aa-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="718aa-117">[Apache Spark için .net ' i doldurun-10 dakikalık öğreticide kullanmaya başlayın](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="718aa-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="718aa-118">Depolama hesaplarınıza erişin</span><span class="sxs-lookup"><span data-stu-id="718aa-118">Access your storage accounts</span></span>

1. <span data-ttu-id="718aa-119">Azure Depolama Gezgini açın.</span><span class="sxs-lookup"><span data-stu-id="718aa-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="718aa-120">Sol menüden **Hesap Ekle** ' yi seçin ve Azure hesabınızda oturum açın.</span><span class="sxs-lookup"><span data-stu-id="718aa-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Depolama Gezgini Azure hesabında oturum açın](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="718aa-122">Oturum açtıktan sonra, sahip olduğunuz tüm depolama hesaplarını ve depolama hesaplarınıza yüklediğiniz kaynakları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="718aa-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="718aa-123">HDInsight kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="718aa-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="718aa-124">HDInsight kümelerinin faturalandırılması, kullanmadığınız olsalar dahi, dakikada eşit olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="718aa-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="718aa-125">Kullanmayı bitirdikten sonra kümenizi sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="718aa-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="718aa-126">Daha fazla bilgi için Bu öğreticinin [Temizleme kaynakları](#clean-up-resources) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="718aa-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="718aa-127">[Azure Portal](https://portal.azure.com)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="718aa-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="718aa-128">**+ Kaynak oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="718aa-129">Ardından **analiz** kategorisinden **HDInsight** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Azure portal HDInsight kaynağı oluşturma](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="718aa-131">**Temel bilgiler**bölümünde aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="718aa-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="718aa-132">Özellik</span><span class="sxs-lookup"><span data-stu-id="718aa-132">Property</span></span>  |<span data-ttu-id="718aa-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718aa-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="718aa-134">Aboneliği</span><span class="sxs-lookup"><span data-stu-id="718aa-134">Subscription</span></span>  | <span data-ttu-id="718aa-135">Açılan listeden, etkin Azure aboneliklerinizden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="718aa-136">Resource group</span><span class="sxs-lookup"><span data-stu-id="718aa-136">Resource group</span></span> | <span data-ttu-id="718aa-137">Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="718aa-138">Kaynak grubu, bir Azure çözümü için ilgili kaynakları bir arada tutan kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="718aa-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="718aa-139">Küme adı</span><span class="sxs-lookup"><span data-stu-id="718aa-139">Cluster name</span></span> | <span data-ttu-id="718aa-140">HDInsight Spark kümenize bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="718aa-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="718aa-141">Konum</span><span class="sxs-lookup"><span data-stu-id="718aa-141">Location</span></span>   | <span data-ttu-id="718aa-142">Kaynak grubu için bir konum seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-142">Select a location for the resource group.</span></span> <span data-ttu-id="718aa-143">Şablon, kümeyi oluşturmak için bu konumu ve varsayılan küme depolama alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="718aa-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="718aa-144">Küme türü</span><span class="sxs-lookup"><span data-stu-id="718aa-144">Cluster type</span></span>| <span data-ttu-id="718aa-145">Küme türü olarak **Spark** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="718aa-146">Küme sürümü</span><span class="sxs-lookup"><span data-stu-id="718aa-146">Cluster version</span></span>|<span data-ttu-id="718aa-147">Bu alan, küme türü seçildikten sonra varsayılan sürüm ile oto doldurulur.</span><span class="sxs-lookup"><span data-stu-id="718aa-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="718aa-148">Spark 'ın 2,3 veya 2,4 sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="718aa-149">Küme oturum açma Kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="718aa-149">Cluster login username</span></span>| <span data-ttu-id="718aa-150">Küme oturum açma Kullanıcı adı ' nı girin.</span><span class="sxs-lookup"><span data-stu-id="718aa-150">Enter the cluster login username.</span></span>  <span data-ttu-id="718aa-151">Varsayılan ad *admin*' dir.</span><span class="sxs-lookup"><span data-stu-id="718aa-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="718aa-152">Küme oturum açma parolası</span><span class="sxs-lookup"><span data-stu-id="718aa-152">Cluster login password</span></span>| <span data-ttu-id="718aa-153">Herhangi bir oturum açma parolası girin.</span><span class="sxs-lookup"><span data-stu-id="718aa-153">Enter any login password.</span></span> |
    |<span data-ttu-id="718aa-154">Secure Shell (SSH) Kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="718aa-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="718aa-155">SSH kullanıcı adını girin.</span><span class="sxs-lookup"><span data-stu-id="718aa-155">Enter the SSH username.</span></span> <span data-ttu-id="718aa-156">Varsayılan olarak, bu hesap *küme oturum açma Kullanıcı adı* hesabıyla aynı parolayı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="718aa-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="718aa-157">Ileri ' yi seçin: **depolama sayfasına devam** etmek Için **> Depolama >** .</span><span class="sxs-lookup"><span data-stu-id="718aa-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="718aa-158">**Depolama**bölümünde aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="718aa-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="718aa-159">Özellik</span><span class="sxs-lookup"><span data-stu-id="718aa-159">Property</span></span>  |<span data-ttu-id="718aa-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718aa-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="718aa-161">Birincil depolama türü</span><span class="sxs-lookup"><span data-stu-id="718aa-161">Primary storage type</span></span>|<span data-ttu-id="718aa-162">Varsayılan **Azure Storage**değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="718aa-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="718aa-163">Seçim yöntemi</span><span class="sxs-lookup"><span data-stu-id="718aa-163">Selection method</span></span>|<span data-ttu-id="718aa-164">Varsayılan değer **listesinden Seç ' i**kullanın.</span><span class="sxs-lookup"><span data-stu-id="718aa-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="718aa-165">Birincil depolama hesabı</span><span class="sxs-lookup"><span data-stu-id="718aa-165">Primary storage account</span></span>|<span data-ttu-id="718aa-166">Aboneliğinizi ve bu abonelik içindeki etkin depolama hesaplarınızdan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="718aa-167">Kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="718aa-167">Container</span></span>|<span data-ttu-id="718aa-168">Bu kapsayıcı, depolama hesabınızda, kümenizin uygulamanızı bulutta çalıştırmak için dosya aradığı belirli bir blob kapsayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="718aa-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="718aa-169">Kullanılabilir herhangi bir ad verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="718aa-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="718aa-170">**Gözden geçir + oluştur**altında **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="718aa-171">Kümenin oluşturulması yaklaşık 20 dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="718aa-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="718aa-172">Sonraki adıma devam edebilmeniz için önce kümenin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="718aa-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="718aa-173">Uygulamanızı yayınlama</span><span class="sxs-lookup"><span data-stu-id="718aa-173">Publish your app</span></span>

<span data-ttu-id="718aa-174">Daha sonra, [Apache Spark için .net](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) sürümünde oluşturulan *mySparkApp* 'yi yayımlarsınız ve bu, Spark kümesine uygulamanızı çalıştırmak için gereken tüm dosyalara erişim sağlayan 10 dakikalık öğreticide çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="718aa-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="718aa-175">*MySparkApp*yayımlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="718aa-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="718aa-176">**Windows üzerinde:**</span><span class="sxs-lookup"><span data-stu-id="718aa-176">**On Windows:**</span></span>

   ```console
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

   <span data-ttu-id="718aa-177">**Linux 'ta:**</span><span class="sxs-lookup"><span data-stu-id="718aa-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.0 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="718aa-178">Bunları HDInsight kümenize kolayca yükleyebilmeniz için, yayımlanmış uygulama dosyalarınızı Zip halinde aşağıdaki görevleri yapın.</span><span class="sxs-lookup"><span data-stu-id="718aa-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span>

   <span data-ttu-id="718aa-179">**Windows üzerinde:**</span><span class="sxs-lookup"><span data-stu-id="718aa-179">**On Windows:**</span></span>

   <span data-ttu-id="718aa-180">*MySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64*dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="718aa-180">Navigate to *mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64*.</span></span> <span data-ttu-id="718aa-181">Ardından, **Yayımla** klasörüne sağ tıklayıp **> Sıkıştırılmış (daraltılmış) klasöre gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-181">Then, right-click on **Publish** folder and select **Send to > Compressed (zipped) folder**.</span></span> <span data-ttu-id="718aa-182">Yeni klasörü **Publish. zip**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="718aa-182">Name the new folder **publish.zip**.</span></span>

   <span data-ttu-id="718aa-183">**Linux 'ta aşağıdaki komutu çalıştırın:**</span><span class="sxs-lookup"><span data-stu-id="718aa-183">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="718aa-184">Azure 'a dosya yükleme</span><span class="sxs-lookup"><span data-stu-id="718aa-184">Upload files to Azure</span></span>

<span data-ttu-id="718aa-185">Ardından, aşağıdaki beş dosyayı kümenizin depolaması için seçtiğiniz blob kapsayıcısına yüklemek için Azure Depolama Gezgini kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="718aa-185">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="718aa-186">Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="718aa-186">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="718aa-187">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="718aa-187">install-worker.sh</span></span>
* <span data-ttu-id="718aa-188">Yayımla. zip</span><span class="sxs-lookup"><span data-stu-id="718aa-188">publish.zip</span></span>
* <span data-ttu-id="718aa-189">Microsoft-Spark-2.3. x-0.3.0. jar</span><span class="sxs-lookup"><span data-stu-id="718aa-189">microsoft-spark-2.3.x-0.3.0.jar</span></span>
* <span data-ttu-id="718aa-190">Input. txt.</span><span class="sxs-lookup"><span data-stu-id="718aa-190">input.txt.</span></span>

1. <span data-ttu-id="718aa-191">Azure Depolama Gezgini açın ve sol menüden depolama hesabınıza gidin.</span><span class="sxs-lookup"><span data-stu-id="718aa-191">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="718aa-192">Depolama hesabınızdaki **BLOB kapsayıcıları** altındaki kümeniz için blob kapsayıcısının ayrıntılarına gidin.</span><span class="sxs-lookup"><span data-stu-id="718aa-192">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="718aa-193">*Microsoft. spark. Worker* , yazdığınız kullanıcı tanımlı Işlevler (UDF 'ler) gibi uygulamanızı Apache Spark yürütmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="718aa-193">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="718aa-194">[Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz)öğesini indirin.</span><span class="sxs-lookup"><span data-stu-id="718aa-194">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v0.3.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.3.0.tar.gz).</span></span> <span data-ttu-id="718aa-195">Ardından, çalışanı karşıya yüklemek için Azure Depolama Gezgini **karşıya yükle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-195">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Dosyaları Azure Depolama Gezgini karşıya yükleme](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="718aa-197">*İnstall-Worker.sh* , Apache Spark bağımlı dosyaları için .net ' i kümenizin düğümlerine kopyalamanızı sağlayan bir betiktir.</span><span class="sxs-lookup"><span data-stu-id="718aa-197">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="718aa-198">Yerel bilgisayarınızı **install-Worker.sh** adlı yeni bir dosya oluşturun ve GitHub 'da bulunan [install-Worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="718aa-198">Create a new file named **install-worker.sh** your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="718aa-199">Sonra, blob kapsayıcınıza *install-Worker.sh* yükleyin.</span><span class="sxs-lookup"><span data-stu-id="718aa-199">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="718aa-200">Kümenizin, uygulamanızın yayımlanan dosyalarını içeren Publish. zip dosyasına ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="718aa-200">Your cluster needs the publish.zip file that contains your app's published files.</span></span> <span data-ttu-id="718aa-201">Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**ve **Publish. zip**dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="718aa-201">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="718aa-202">Sonra *Publish. zip* ' i blob kapsayıcınıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="718aa-202">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="718aa-203">Kümeniz, bir jar dosyasına paketlenmiş uygulama koduna ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="718aa-203">Your cluster needs the application code that was packaged into a jar file.</span></span> <span data-ttu-id="718aa-204">Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp 3.0/Ubuntu. 16.04-x64**ve **Microsoft-Spark-2.3. x-0.3.0. jar**konumunu bulun.</span><span class="sxs-lookup"><span data-stu-id="718aa-204">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.0/ubuntu.16.04-x64**, and locate **microsoft-spark-2.3.x-0.3.0.jar**.</span></span> <span data-ttu-id="718aa-205">Ardından, JAR dosyasını blob kapsayıcınıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="718aa-205">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="718aa-206">Birden çok. jar dosyası olabilir (örneğin, 2.3. x ve 2,4. x Spark sürümü için).</span><span class="sxs-lookup"><span data-stu-id="718aa-206">There may be multiple .jar files (for versions 2.3.x and 2.4.x of Spark).</span></span> <span data-ttu-id="718aa-207">Küme oluşturma sırasında seçtiğiniz Spark sürümü ile eşleşen. jar dosyasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="718aa-207">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="718aa-208">Örneğin, küme oluşturma sırasında Spark 2.3.2 ' yı seçtiyseniz *Microsoft-Spark-2.3. x-0.3.0. jar* öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-208">For example, choose *microsoft-spark-2.3.x-0.3.0.jar* if you chose Spark 2.3.2 during cluster creation.</span></span>

6. <span data-ttu-id="718aa-209">Kümenizin uygulamanıza giriş yapması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="718aa-209">Your cluster needs the input to your app.</span></span> <span data-ttu-id="718aa-210">**MySparkApp** dizininize gidin ve **input. txt dosyasını**bulun.</span><span class="sxs-lookup"><span data-stu-id="718aa-210">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="718aa-211">Giriş dosyanızı blob kabınızda **Kullanıcı/sshuser** dizinine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="718aa-211">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="718aa-212">SSH aracılığıyla kümenize bağlanırsınız ve bu klasör, kümenizin girişi için bakacağı yerdir.</span><span class="sxs-lookup"><span data-stu-id="718aa-212">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="718aa-213">*Input. txt* dosyası, belirli bir dizine yüklenen tek dosyadır.</span><span class="sxs-lookup"><span data-stu-id="718aa-213">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="718aa-214">HDInsight betiği eylemini Çalıştır</span><span class="sxs-lookup"><span data-stu-id="718aa-214">Run the HDInsight script action</span></span>

<span data-ttu-id="718aa-215">Kümeniz çalışır olduktan sonra dosyalarınızı Azure 'a yükledikten sonra kümede **install-Worker.sh** betiğini çalıştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="718aa-215">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="718aa-216">Azure portal HDInsight Spark kümenize gidin ve **betik eylemleri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-216">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="718aa-217">**+ Yeni Gönder** ' i seçin ve aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="718aa-217">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="718aa-218">Özellik</span><span class="sxs-lookup"><span data-stu-id="718aa-218">Property</span></span>  |<span data-ttu-id="718aa-219">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718aa-219">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="718aa-220">Betik türü</span><span class="sxs-lookup"><span data-stu-id="718aa-220">Script type</span></span> |<span data-ttu-id="718aa-221">Özel</span><span class="sxs-lookup"><span data-stu-id="718aa-221">Custom</span></span>|
   | <span data-ttu-id="718aa-222">Name</span><span class="sxs-lookup"><span data-stu-id="718aa-222">Name</span></span> | <span data-ttu-id="718aa-223">Çalışanı yükler</span><span class="sxs-lookup"><span data-stu-id="718aa-223">Install Worker</span></span>|
   | <span data-ttu-id="718aa-224">Bash betiği URI 'SI</span><span class="sxs-lookup"><span data-stu-id="718aa-224">Bash script URI</span></span> |https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh </br> <span data-ttu-id="718aa-225">Bu URI 'yi onaylamak için Azure Depolama Gezgini 'de install-worker.sh öğesine sağ tıklayın ve Özellikler ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-225">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="718aa-226">Düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="718aa-226">Node type(s)</span></span>| <span data-ttu-id="718aa-227">Çalışan</span><span class="sxs-lookup"><span data-stu-id="718aa-227">Worker</span></span>|
   | <span data-ttu-id="718aa-228">Parametreler</span><span class="sxs-lookup"><span data-stu-id="718aa-228">Parameters</span></span> | <span data-ttu-id="718aa-229">Mavisi</span><span class="sxs-lookup"><span data-stu-id="718aa-229">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.6.0.tar.gz </br> <span data-ttu-id="718aa-230">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="718aa-230">/usr/local/bin</span></span>

3. <span data-ttu-id="718aa-231">Komut dosyanızı göndermek için **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-231">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="718aa-232">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="718aa-232">Run your app</span></span>

1. <span data-ttu-id="718aa-233">Azure portal HDInsight Spark kümenize gidin ve ardından **SSH + küme oturumu aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-233">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="718aa-234">SSH oturum açma bilgilerini kopyalayın ve oturumu bir terminale yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="718aa-234">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="718aa-235">Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="718aa-235">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="718aa-236">Sizi Ubuntu ve Spark 'a yönlendiren iletiler görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="718aa-236">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="718aa-237">Uygulamanızı HDInsight kümenizde çalıştırmak için **Spark-gönder** komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="718aa-237">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="718aa-238">Örnek betikteki **myContainer** ve **mystorageaccount** ' ın blob Kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirilmesini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="718aa-238">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="718aa-239">Uygulamanız çalıştığında, Başlarken yerel çalıştırmasından konsola yazılan aynı sözcük sayısı tablosunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="718aa-239">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="718aa-240">Tebrikler, ilk .NET Apache Spark uygulamanızı bulutta çalıştırdık!</span><span class="sxs-lookup"><span data-stu-id="718aa-240">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="718aa-241">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="718aa-241">Clean up resources</span></span>

<span data-ttu-id="718aa-242">HDInsight, verileri Azure Storage 'a kaydeder, bu sayede bir kümeyi kullanımda olmadığında güvenle silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="718aa-242">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="718aa-243">Ayrıca, kullanımda olmadığı halde bir HDInsight kümesi için de ücretlendirilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="718aa-243">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="718aa-244">Kümenin ücretleri depolama ücretinden çok daha fazla olduğundan, kullanımda olmadıkları zaman kümeleri silmek ekonomik bir anlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="718aa-244">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="718aa-245">Kaynak grubu adını da seçerek kaynak grubu sayfasını açabilir ve **kaynak grubunu sil**' i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="718aa-245">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="718aa-246">Kaynak grubunu silerek, hem HDInsight Spark kümesini hem de varsayılan depolama hesabını silersiniz.</span><span class="sxs-lookup"><span data-stu-id="718aa-246">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="718aa-247">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="718aa-247">Next steps</span></span>

<span data-ttu-id="718aa-248">Bu öğreticide, .NET Apache Spark uygulamanızı Azure HDInsight 'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="718aa-248">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="718aa-249">HDInsight hakkında daha fazla bilgi edinmek için Azure HDInsight belgelerine geçin.</span><span class="sxs-lookup"><span data-stu-id="718aa-249">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="718aa-250">Azure HDInsight belgeleri</span><span class="sxs-lookup"><span data-stu-id="718aa-250">Azure HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
