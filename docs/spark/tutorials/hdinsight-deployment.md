---
title: Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma
description: HDInsight için bir .NET Apache Spark uygulamasının nasıl dağıtılacağını öğrenin.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f7a3b0c0d972d5cb6dbc6eea818fe794c5060eae
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687916"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a><span data-ttu-id="063f5-103">Öğretici: Azure HDInsight 'a Apache Spark uygulaması için .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="063f5-103">Tutorial: Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>

<span data-ttu-id="063f5-104">Bu öğreticide, Azure HDInsight kümesi aracılığıyla Apache Spark için .NET uygulamanızı buluta nasıl dağıtacağınız öğretilir.</span><span class="sxs-lookup"><span data-stu-id="063f5-104">This tutorial teaches you how to deploy your .NET for Apache Spark app to the cloud through an Azure HDInsight cluster.</span></span> <span data-ttu-id="063f5-105">HDInsight 'ta Spark kümeleri Azure depolama ve Azure Data Lake Storage uyumlu olduğundan, HDInsight, Azure 'da Spark kümesi oluşturmayı ve yapılandırmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="063f5-105">HDInsight makes it easier to create and configure a Spark cluster in Azure since Spark clusters in HDInsight are compatible with Azure Storage and Azure Data Lake Storage.</span></span>

<span data-ttu-id="063f5-106">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="063f5-106">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="063f5-107">Azure Depolama Gezgini kullanarak depolama hesaplarınıza erişin.</span><span class="sxs-lookup"><span data-stu-id="063f5-107">Access your storage accounts using Azure Storage Explorer.</span></span>
> * <span data-ttu-id="063f5-108">Azure HDInsight kümesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="063f5-108">Create an Azure HDInsight cluster.</span></span>
> * <span data-ttu-id="063f5-109">Apache Spark için .NET uygulamanızı yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="063f5-109">Publish your .NET for Apache Spark app.</span></span>
> * <span data-ttu-id="063f5-110">HDInsight betik eylemi oluşturun ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="063f5-110">Create and run an HDInsight script action.</span></span>
> * <span data-ttu-id="063f5-111">HDInsight kümesinde Apache Spark uygulaması için bir .NET çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="063f5-111">Run a .NET for Apache Spark app on an HDInsight cluster.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="063f5-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="063f5-112">Prerequisites</span></span>

<span data-ttu-id="063f5-113">Başlamadan önce, aşağıdaki görevleri yapın:</span><span class="sxs-lookup"><span data-stu-id="063f5-113">Before you start, do the following tasks:</span></span>

* <span data-ttu-id="063f5-114">Azure aboneliğiniz yoksa [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="063f5-114">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/dotnet/).</span></span>
* <span data-ttu-id="063f5-115">[Azure portalında](https://portal.azure.com/) oturum açın.</span><span class="sxs-lookup"><span data-stu-id="063f5-115">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
* <span data-ttu-id="063f5-116">[Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409)veya [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) bilgisayarınıza Azure Depolama Gezgini ' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="063f5-116">Install Azure Storage Explorer on your [Windows](https://go.microsoft.com/fwlink/?LinkId=708343&clcid=0x409), [Linux](https://go.microsoft.com/fwlink/?LinkId=722418&clcid=0x409), or [MacOS](https://go.microsoft.com/fwlink/?LinkId=708342&clcid=0x409) computer.</span></span>
* <span data-ttu-id="063f5-117">[Apache Spark için .net ' i doldurun-10 dakikalık öğreticide kullanmaya başlayın](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .</span><span class="sxs-lookup"><span data-stu-id="063f5-117">Complete the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial.</span></span>

## <a name="access-your-storage-accounts"></a><span data-ttu-id="063f5-118">Depolama hesaplarınıza erişin</span><span class="sxs-lookup"><span data-stu-id="063f5-118">Access your storage accounts</span></span>

1. <span data-ttu-id="063f5-119">Azure Depolama Gezgini açın.</span><span class="sxs-lookup"><span data-stu-id="063f5-119">Open Azure Storage Explorer.</span></span>

2. <span data-ttu-id="063f5-120">Sol menüden **Hesap Ekle** ' yi seçin ve Azure hesabınızda oturum açın.</span><span class="sxs-lookup"><span data-stu-id="063f5-120">Select **Add Account** on the left menu, and sign in to your Azure account.</span></span>

    ![Depolama Gezgini Azure hesabında oturum açın](./media/hdinsight-deployment/signin-azure-storage-explorer.png)

   <span data-ttu-id="063f5-122">Oturum açtıktan sonra, sahip olduğunuz tüm depolama hesaplarını ve depolama hesaplarınıza yüklediğiniz kaynakları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="063f5-122">After you sign in, you should see all storage accounts you have and any resources you have uploaded to your storage accounts.</span></span>

## <a name="create-an-hdinsight-cluster"></a><span data-ttu-id="063f5-123">HDInsight kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="063f5-123">Create an HDInsight cluster</span></span>

> [!IMPORTANT]
> <span data-ttu-id="063f5-124">HDInsight kümelerinin faturalandırılması, kullanmadığınız olsalar dahi, dakikada eşit olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="063f5-124">Billing for HDInsight clusters is prorated per minute, even if you're not using them.</span></span> <span data-ttu-id="063f5-125">Kullanmayı bitirdikten sonra kümenizi sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="063f5-125">Be sure to delete your cluster after you have finished using it.</span></span> <span data-ttu-id="063f5-126">Daha fazla bilgi için Bu öğreticinin [Temizleme kaynakları](#clean-up-resources) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="063f5-126">For more information, see the [Clean up resources](#clean-up-resources) section of this tutorial.</span></span>

1. <span data-ttu-id="063f5-127">[Azure Portal](https://portal.azure.com)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="063f5-127">Visit the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="063f5-128">**+ Kaynak oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-128">Select **+ Create a resource**.</span></span> <span data-ttu-id="063f5-129">Ardından **analiz** kategorisinden **HDInsight** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-129">Then, select **HDInsight** from the **Analytics** category.</span></span>

    ![Azure portal HDInsight kaynağı oluşturma](./media/hdinsight-deployment/create-hdinsight-resource.png)

3. <span data-ttu-id="063f5-131">**Temel Bilgiler** bölümünde aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="063f5-131">Under **Basics**, provide the following values:</span></span>

    |<span data-ttu-id="063f5-132">Özellik</span><span class="sxs-lookup"><span data-stu-id="063f5-132">Property</span></span>  |<span data-ttu-id="063f5-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="063f5-133">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="063f5-134">Abonelik</span><span class="sxs-lookup"><span data-stu-id="063f5-134">Subscription</span></span>  | <span data-ttu-id="063f5-135">Açılan listeden, etkin Azure aboneliklerinizden birini seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-135">From the drop-down, choose one of your active Azure subscriptions.</span></span> |
    |<span data-ttu-id="063f5-136">Kaynak grubu</span><span class="sxs-lookup"><span data-stu-id="063f5-136">Resource group</span></span> | <span data-ttu-id="063f5-137">Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-137">Specify whether you want to create a new resource group or use an existing one.</span></span> <span data-ttu-id="063f5-138">Kaynak grubu, bir Azure çözümüne ilişkin kaynakları tutan bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="063f5-138">A resource group is a container that holds related resources for an Azure solution.</span></span> |
    |<span data-ttu-id="063f5-139">Küme adı</span><span class="sxs-lookup"><span data-stu-id="063f5-139">Cluster name</span></span> | <span data-ttu-id="063f5-140">HDInsight Spark kümenize bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="063f5-140">Give a name to your HDInsight Spark cluster.</span></span>|
    |<span data-ttu-id="063f5-141">Konum</span><span class="sxs-lookup"><span data-stu-id="063f5-141">Location</span></span>   | <span data-ttu-id="063f5-142">Kaynak grubu için bir konum seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-142">Select a location for the resource group.</span></span> <span data-ttu-id="063f5-143">Şablon hem kümeyi oluşturmak için hem de varsayılan küme depolaması için bu konumu kullanır.</span><span class="sxs-lookup"><span data-stu-id="063f5-143">The template uses this location for creating the cluster as well as for the default cluster storage.</span></span> |
    |<span data-ttu-id="063f5-144">Küme türü</span><span class="sxs-lookup"><span data-stu-id="063f5-144">Cluster type</span></span>| <span data-ttu-id="063f5-145">Küme türü olarak **Spark** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-145">Select **Spark** as the cluster type.</span></span>|
    |<span data-ttu-id="063f5-146">Küme sürümü</span><span class="sxs-lookup"><span data-stu-id="063f5-146">Cluster version</span></span>|<span data-ttu-id="063f5-147">Bu alan, küme türü seçildikten sonra varsayılan sürüm ile oto doldurulur.</span><span class="sxs-lookup"><span data-stu-id="063f5-147">This field will autopopulate with the default version once the cluster type has been selected.</span></span> <span data-ttu-id="063f5-148">Spark 'ın 2,3 veya 2,4 sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-148">Select a 2.3 or 2.4 version of Spark.</span></span>|
    |<span data-ttu-id="063f5-149">Küme oturum açma kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="063f5-149">Cluster login username</span></span>| <span data-ttu-id="063f5-150">Küme oturum açma kullanıcı adını girin.</span><span class="sxs-lookup"><span data-stu-id="063f5-150">Enter the cluster login username.</span></span>  <span data-ttu-id="063f5-151">Varsayılan ad, *admin* şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="063f5-151">The default name is *admin*.</span></span> |
    |<span data-ttu-id="063f5-152">Küme oturum açma parolası</span><span class="sxs-lookup"><span data-stu-id="063f5-152">Cluster login password</span></span>| <span data-ttu-id="063f5-153">Herhangi bir oturum açma parolası girin.</span><span class="sxs-lookup"><span data-stu-id="063f5-153">Enter any login password.</span></span> |
    |<span data-ttu-id="063f5-154">Secure Shell (SSH) kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="063f5-154">Secure Shell (SSH) username</span></span>| <span data-ttu-id="063f5-155">SSH kullanıcı adını girin.</span><span class="sxs-lookup"><span data-stu-id="063f5-155">Enter the SSH username.</span></span> <span data-ttu-id="063f5-156">Varsayılan olarak bu hesap, *Küme Oturum Açma kullanıcı adı* hesabıyla aynı parolayı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="063f5-156">By default, this account shares the same password as the *Cluster Login username* account.</span></span> |

4. <span data-ttu-id="063f5-157">Ileri ' yi seçin: **depolama sayfasına devam** etmek için **depolama >>** .</span><span class="sxs-lookup"><span data-stu-id="063f5-157">Select **Next: Storage >>** to continue to the **Storage** page.</span></span> <span data-ttu-id="063f5-158">**Depolama** bölümünde aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="063f5-158">Under **Storage**, provide the following values:</span></span>

    |<span data-ttu-id="063f5-159">Özellik</span><span class="sxs-lookup"><span data-stu-id="063f5-159">Property</span></span>  |<span data-ttu-id="063f5-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="063f5-160">Description</span></span>  |
    |---------|---------|
    |<span data-ttu-id="063f5-161">Birincil depolama türü</span><span class="sxs-lookup"><span data-stu-id="063f5-161">Primary storage type</span></span>|<span data-ttu-id="063f5-162">Varsayılan **Azure Storage** değerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="063f5-162">Use the default value **Azure Storage**.</span></span>|
    |<span data-ttu-id="063f5-163">Seçim yöntemi</span><span class="sxs-lookup"><span data-stu-id="063f5-163">Selection method</span></span>|<span data-ttu-id="063f5-164">Varsayılan değer **listesinden Seç ' i** kullanın.</span><span class="sxs-lookup"><span data-stu-id="063f5-164">Use the default value **Select from list**.</span></span>|
    |<span data-ttu-id="063f5-165">Birincil depolama hesabı</span><span class="sxs-lookup"><span data-stu-id="063f5-165">Primary storage account</span></span>|<span data-ttu-id="063f5-166">Aboneliğinizi ve bu abonelik içindeki etkin depolama hesaplarınızdan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-166">Choose your subscription and one of your active storage accounts within that subscription.</span></span>|
    |<span data-ttu-id="063f5-167">Kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="063f5-167">Container</span></span>|<span data-ttu-id="063f5-168">Bu kapsayıcı, depolama hesabınızda, kümenizin uygulamanızı bulutta çalıştırmak için dosya aradığı belirli bir blob kapsayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="063f5-168">This container is the specific blob container in your storage account where your cluster looks for files to run your app in the cloud.</span></span> <span data-ttu-id="063f5-169">Kullanılabilir herhangi bir ad verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="063f5-169">You can give it any available name.</span></span>|

5. <span data-ttu-id="063f5-170">**Gözden geçir + oluştur** altında **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-170">Under **Review + create**, select **Create**.</span></span> <span data-ttu-id="063f5-171">Kümenin oluşturulması yaklaşık 20 dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="063f5-171">It takes about 20 minutes to create the cluster.</span></span> <span data-ttu-id="063f5-172">Sonraki adıma devam edebilmeniz için önce kümenin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="063f5-172">The cluster must be created before you can continue to the next step.</span></span>

## <a name="publish-your-app"></a><span data-ttu-id="063f5-173">Uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="063f5-173">Publish your app</span></span>

<span data-ttu-id="063f5-174">Daha sonra, [Apache Spark için .net](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) sürümünde oluşturulan *mySparkApp* 'yi yayımlarsınız ve bu, Spark kümesine uygulamanızı çalıştırmak için gereken tüm dosyalara erişim sağlayan 10 dakikalık öğreticide çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="063f5-174">Next, you publish the *mySparkApp* created in the [.NET for Apache Spark - Get Started in 10-Minutes](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) tutorial, which gives your Spark cluster access to all the files it needs to run your app.</span></span>

1. <span data-ttu-id="063f5-175">*MySparkApp* yayımlamak için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="063f5-175">Run the following commands to publish the *mySparkApp*:</span></span>

   <span data-ttu-id="063f5-176">**Windows 'da:**</span><span class="sxs-lookup"><span data-stu-id="063f5-176">**On Windows:**</span></span>

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r win-x64
   ```

   <span data-ttu-id="063f5-177">**Linux 'ta:**</span><span class="sxs-lookup"><span data-stu-id="063f5-177">**On Linux:**</span></span>

   ```bash
   cd mySparkApp
   foo@bar:~/path/to/app$ dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. <span data-ttu-id="063f5-178">Bunları HDInsight kümenize kolayca yükleyebilmeniz için, yayımlanmış uygulama dosyalarınızı Zip halinde aşağıdaki görevleri yapın.</span><span class="sxs-lookup"><span data-stu-id="063f5-178">Do the following tasks to zip your published app files so that you can easily upload them to your HDInsight cluster.</span></span> <span data-ttu-id="063f5-179">Yayımlama klasörünün içeriği, örneğin, 1. Adım sonucu oluşturulan *publish.zip* .</span><span class="sxs-lookup"><span data-stu-id="063f5-179">Zip the contents of the publish folder, *publish.zip* for example, that was created as a result of Step 1.</span></span> <span data-ttu-id="063f5-180">Tüm derlemelerin ZIP dosyasının ilk katmanında olması ve ara klasör katmanı olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="063f5-180">All the assemblies should be in the first layer of the ZIP file and there should be no intermediate folder layer.</span></span> <span data-ttu-id="063f5-181">Bu, *publish.zip* ayıkladığınızda tüm derlemelerin geçerli çalışma dizininize ayıklandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="063f5-181">This means when you unzip *publish.zip*, all assemblies are extracted into your current working directory.</span></span>

   <span data-ttu-id="063f5-182">**Windows 'da:**</span><span class="sxs-lookup"><span data-stu-id="063f5-182">**On Windows:**</span></span>

   <span data-ttu-id="063f5-183">Dosyayı yayımlanan tüm ikili dosyalarla bin dizinine ayıklamak için 7-zip veya WinZip gibi bir ayıklama programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="063f5-183">Use an extraction program, like 7-Zip or WinZip, to extract the file into the bin directory with all the published binaries.</span></span>

   <span data-ttu-id="063f5-184">**Linux 'ta aşağıdaki komutu çalıştırın:**</span><span class="sxs-lookup"><span data-stu-id="063f5-184">**On Linux, run the following command:**</span></span>

   ```bash
   zip -r publish.zip
   ```

## <a name="upload-files-to-azure"></a><span data-ttu-id="063f5-185">Azure 'a dosya yükleme</span><span class="sxs-lookup"><span data-stu-id="063f5-185">Upload files to Azure</span></span>

<span data-ttu-id="063f5-186">Ardından, aşağıdaki beş dosyayı kümenizin depolaması için seçtiğiniz blob kapsayıcısına yüklemek için Azure Depolama Gezgini kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="063f5-186">Next, you use the Azure Storage Explorer to upload the following five files to the blob container you chose for your cluster's storage:</span></span>

* <span data-ttu-id="063f5-187">Microsoft. spark. Worker</span><span class="sxs-lookup"><span data-stu-id="063f5-187">Microsoft.Spark.Worker</span></span>
* <span data-ttu-id="063f5-188">install-worker.sh</span><span class="sxs-lookup"><span data-stu-id="063f5-188">install-worker.sh</span></span>
* <span data-ttu-id="063f5-189">publish.zip</span><span class="sxs-lookup"><span data-stu-id="063f5-189">publish.zip</span></span>
* <span data-ttu-id="063f5-190">Microsoft-Spark-2-4_ 2.11-1.0.0. jar</span><span class="sxs-lookup"><span data-stu-id="063f5-190">microsoft-spark-2-4_2.11-1.0.0.jar</span></span>
* <span data-ttu-id="063f5-191">input.txt</span><span class="sxs-lookup"><span data-stu-id="063f5-191">input.txt</span></span>

1. <span data-ttu-id="063f5-192">Azure Depolama Gezgini açın ve sol menüden depolama hesabınıza gidin.</span><span class="sxs-lookup"><span data-stu-id="063f5-192">Open Azure Storage Explorer and navigate to your storage account from the left menu.</span></span> <span data-ttu-id="063f5-193">Depolama hesabınızdaki **BLOB kapsayıcıları** altındaki kümeniz için blob kapsayıcısının ayrıntılarına gidin.</span><span class="sxs-lookup"><span data-stu-id="063f5-193">Drill down to the blob container for your cluster under **Blob Containers** in your storage account.</span></span>

2. <span data-ttu-id="063f5-194">*Microsoft. spark. Worker* , yazdığınız kullanıcı tanımlı Işlevler (UDF 'ler) gibi uygulamanızı Apache Spark yürütmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="063f5-194">*Microsoft.Spark.Worker* helps Apache Spark execute your app, such as any user-defined functions (UDFs) you may have written.</span></span> <span data-ttu-id="063f5-195">[Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz)öğesini indirin.</span><span class="sxs-lookup"><span data-stu-id="063f5-195">Download [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz).</span></span> <span data-ttu-id="063f5-196">Ardından, çalışanı karşıya yüklemek için Azure Depolama Gezgini **karşıya yükle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-196">Then, select **Upload** in Azure Storage Explorer to upload the worker.</span></span>

   ![Dosyaları Azure Depolama Gezgini karşıya yükleme](./media/hdinsight-deployment/upload-files-to-storage.png)

3. <span data-ttu-id="063f5-198">*İnstall-Worker.sh* , Apache Spark bağımlı dosyaları için .net ' i kümenizin düğümlerine kopyalamanızı sağlayan bir betiktir.</span><span class="sxs-lookup"><span data-stu-id="063f5-198">The *install-worker.sh* is a script that lets you copy .NET for Apache Spark dependent files into the nodes of your cluster.</span></span>

   <span data-ttu-id="063f5-199">Yerel bilgisayarınızda **install-Worker.sh** adlı yeni bir dosya oluşturun ve GitHub 'da bulunan [install-Worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="063f5-199">Create a new file named **install-worker.sh** in your local computer, and paste the [install-worker.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/install-worker.sh) located on GitHub.</span></span> <span data-ttu-id="063f5-200">Sonra, blob kapsayıcınıza *install-Worker.sh* yükleyin.</span><span class="sxs-lookup"><span data-stu-id="063f5-200">Then, upload *install-worker.sh* to your blob container.</span></span>

4. <span data-ttu-id="063f5-201">Kümeniz, uygulamanızın yayımlanan dosyalarını içeren *publish.zip* dosyasına ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="063f5-201">Your cluster needs the *publish.zip* file that contains your app's published files.</span></span> <span data-ttu-id="063f5-202">Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp 3.1/Ubuntu. 16.04-x64** ve **publish.zip** bulun.</span><span class="sxs-lookup"><span data-stu-id="063f5-202">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **publish.zip**.</span></span> <span data-ttu-id="063f5-203">Sonra *publish.zip* blob kapsayıcınıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="063f5-203">Then upload *publish.zip* to your blob container.</span></span>

5. <span data-ttu-id="063f5-204">Kümeniz, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet 'in bir parçası olarak sunulan ve uygulamanızın derleme çıkış dizininde birlikte bulunan bir jar olarak paketlenmiş uygulama koduna ihtiyaç duyuyor.</span><span class="sxs-lookup"><span data-stu-id="063f5-204">Your cluster needs the application code that is packaged as a jar, included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) nuget and colocated in your app's build output directory.</span></span> <span data-ttu-id="063f5-205">Yayınlanan klasörünüze gidin, **mySparkApp/bin/Release/netcoreapp 3.1/Ubuntu. 16.04-x64** ve **Microsoft-Spark-2-4_ 2.11-1.0.0. jar** konumunu bulun.</span><span class="sxs-lookup"><span data-stu-id="063f5-205">Navigate to your published folder, **mySparkApp/bin/Release/netcoreapp3.1/ubuntu.16.04-x64**, and locate **microsoft-spark-2-4_2.11-1.0.0.jar**.</span></span> <span data-ttu-id="063f5-206">Ardından, JAR dosyasını blob kapsayıcınıza yükleyin.</span><span class="sxs-lookup"><span data-stu-id="063f5-206">Then, upload the jar file to your blob container.</span></span>

   <span data-ttu-id="063f5-207">Birden fazla. jar dosyası olabilir (2.3. x, 2,4. x ve 3.0. x Spark sürümü için).</span><span class="sxs-lookup"><span data-stu-id="063f5-207">There may be multiple .jar files (for versions 2.3.x, 2.4.x and 3.0.x of Spark).</span></span> <span data-ttu-id="063f5-208">Küme oluşturma sırasında seçtiğiniz Spark sürümü ile eşleşen. jar dosyasını seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="063f5-208">You need to choose the .jar file that matches the version of Spark you chose during cluster creation.</span></span> <span data-ttu-id="063f5-209">Örneğin, küme oluşturma sırasında Spark 2,4 ' i seçtiyseniz *Microsoft-Spark-2-4_ 2.11-1.0.0. jar* öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-209">For example, choose *microsoft-spark-2-4_2.11-1.0.0.jar* if you chose Spark 2.4 during cluster creation.</span></span>

6. <span data-ttu-id="063f5-210">Kümenizin uygulamanıza giriş yapması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="063f5-210">Your cluster needs the input to your app.</span></span> <span data-ttu-id="063f5-211">**MySparkApp** dizininize gidin ve **input.txt** bulun.</span><span class="sxs-lookup"><span data-stu-id="063f5-211">Navigate to your **mySparkApp** directory and locate **input.txt**.</span></span> <span data-ttu-id="063f5-212">Giriş dosyanızı blob kabınızda **Kullanıcı/sshuser** dizinine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="063f5-212">Upload your input file to the **user/sshuser** directory in your blob container.</span></span> <span data-ttu-id="063f5-213">SSH aracılığıyla kümenize bağlanırsınız ve bu klasör, kümenizin girişi için bakacağı yerdir.</span><span class="sxs-lookup"><span data-stu-id="063f5-213">You will be connecting to your cluster through ssh, and this folder is where your cluster looks for its input.</span></span> <span data-ttu-id="063f5-214">*input.txt* dosyası, belirli bir dizine yüklenen tek dosyadır.</span><span class="sxs-lookup"><span data-stu-id="063f5-214">The *input.txt* file is the only file uploaded to a specific directory.</span></span>

## <a name="run-the-hdinsight-script-action"></a><span data-ttu-id="063f5-215">HDInsight betiği eylemini Çalıştır</span><span class="sxs-lookup"><span data-stu-id="063f5-215">Run the HDInsight script action</span></span>

<span data-ttu-id="063f5-216">Kümeniz çalışır olduktan sonra dosyalarınızı Azure 'a yükledikten sonra kümede **install-Worker.sh** betiğini çalıştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="063f5-216">Once your cluster is running and you've uploaded your files to Azure, you run the **install-worker.sh** script on the cluster.</span></span>

1. <span data-ttu-id="063f5-217">Azure portal HDInsight Spark kümenize gidin ve **betik eylemleri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-217">Navigate to your HDInsight Spark cluster in Azure portal, and then select **Script actions**.</span></span>

2. <span data-ttu-id="063f5-218">**+ Yeni Gönder** ' i seçin ve aşağıdaki değerleri sağlayın:</span><span class="sxs-lookup"><span data-stu-id="063f5-218">Select **+ Submit new** and provide the following values:</span></span>

   |<span data-ttu-id="063f5-219">Özellik</span><span class="sxs-lookup"><span data-stu-id="063f5-219">Property</span></span>  |<span data-ttu-id="063f5-220">Açıklama</span><span class="sxs-lookup"><span data-stu-id="063f5-220">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="063f5-221">Betik türü</span><span class="sxs-lookup"><span data-stu-id="063f5-221">Script type</span></span> |<span data-ttu-id="063f5-222">Özel</span><span class="sxs-lookup"><span data-stu-id="063f5-222">Custom</span></span>|
   | <span data-ttu-id="063f5-223">Name</span><span class="sxs-lookup"><span data-stu-id="063f5-223">Name</span></span> | <span data-ttu-id="063f5-224">Çalışanı yükler</span><span class="sxs-lookup"><span data-stu-id="063f5-224">Install Worker</span></span>|
   | <span data-ttu-id="063f5-225">Bash betiği URI 'SI</span><span class="sxs-lookup"><span data-stu-id="063f5-225">Bash script URI</span></span> |`https://mystorageaccount.blob.core.windows.net/mycontainer/install-worker.sh` </br> <span data-ttu-id="063f5-226">Bu URI 'yi onaylamak için Azure Depolama Gezgini 'de install-worker.sh öğesine sağ tıklayın ve Özellikler ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-226">To confirm this URI, right-click on install-worker.sh in Azure Storage Explorer and select Properties.</span></span> |
   | <span data-ttu-id="063f5-227">Düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="063f5-227">Node type(s)</span></span>| <span data-ttu-id="063f5-228">Indan</span><span class="sxs-lookup"><span data-stu-id="063f5-228">Worker</span></span>|
   | <span data-ttu-id="063f5-229">Parametreler</span><span class="sxs-lookup"><span data-stu-id="063f5-229">Parameters</span></span> | <span data-ttu-id="063f5-230">azure</span><span class="sxs-lookup"><span data-stu-id="063f5-230">azure</span></span> </br> wasbs://mycontainer@myStorageAccount.blob.core.windows.net/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz </br> <span data-ttu-id="063f5-231">/usr/local/bin</span><span class="sxs-lookup"><span data-stu-id="063f5-231">/usr/local/bin</span></span>

3. <span data-ttu-id="063f5-232">Komut dosyanızı göndermek için **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-232">Select **Create** to submit your script.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="063f5-233">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="063f5-233">Run your app</span></span>

1. <span data-ttu-id="063f5-234">Azure portal HDInsight Spark kümenize gidin ve ardından **SSH + küme oturumu aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-234">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="063f5-235">SSH oturum açma bilgilerini kopyalayın ve oturumu bir terminale yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="063f5-235">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="063f5-236">Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="063f5-236">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="063f5-237">Sizi Ubuntu ve Spark 'a yönlendiren iletiler görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="063f5-237">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="063f5-238">Uygulamanızı HDInsight kümenizde çalıştırmak için **Spark-gönder** komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="063f5-238">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="063f5-239">Örnek betikteki **myContainer** ve **mystorageaccount** ' ın blob Kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirilmesini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="063f5-239">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2-4_2.11-1.0.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

   <span data-ttu-id="063f5-240">Uygulamanız çalıştığında, Başlarken yerel çalıştırmasından konsola yazılan aynı sözcük sayısı tablosunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="063f5-240">When your app runs, you see the same word count table from the getting started local run written to the console.</span></span> <span data-ttu-id="063f5-241">Tebrikler, ilk .NET Apache Spark uygulamanızı bulutta çalıştırdık!</span><span class="sxs-lookup"><span data-stu-id="063f5-241">Congratulations, you've run your first .NET for Apache Spark application in the cloud!</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="063f5-242">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="063f5-242">Clean up resources</span></span>

<span data-ttu-id="063f5-243">HDInsight, verileri Azure Storage 'a kaydeder, bu sayede bir kümeyi kullanımda olmadığında güvenle silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="063f5-243">HDInsight saves your data in Azure Storage, so you can safely delete a cluster when it is not in use.</span></span> <span data-ttu-id="063f5-244">Ayrıca, kullanılmıyorken dahi HDInsight kümesi için sizden ücret kesilir.</span><span class="sxs-lookup"><span data-stu-id="063f5-244">You are also charged for an HDInsight cluster, even when it is not in use.</span></span> <span data-ttu-id="063f5-245">Küme ücretleri depolama ücretlerinin birkaç katı olduğundan, kullanılmadığında kümelerin silinmesi mantıklı olandır.</span><span class="sxs-lookup"><span data-stu-id="063f5-245">Since the charges for the cluster are many times more than the charges for storage, it makes economic sense to delete clusters when they are not in use.</span></span>

<span data-ttu-id="063f5-246">Kaynak grubu adını seçerek de kaynak grubu sayfasını açabilir ve sonra **Kaynak grubunu sil**’i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="063f5-246">You can also select the resource group name to open the resource group page, and then select **Delete resource group**.</span></span> <span data-ttu-id="063f5-247">Kaynak grubunu silerek hem HDInsight Spark kümesini hem de varsayılan depolama hesabını silersiniz.</span><span class="sxs-lookup"><span data-stu-id="063f5-247">By deleting the resource group, you delete both the HDInsight Spark cluster, and the default storage account.</span></span>

## <a name="next-steps"></a><span data-ttu-id="063f5-248">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="063f5-248">Next steps</span></span>

<span data-ttu-id="063f5-249">Bu öğreticide, .NET Apache Spark uygulamanızı Azure HDInsight 'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="063f5-249">In this tutorial, you deployed your .NET for Apache Spark application to Azure HDInsight.</span></span> <span data-ttu-id="063f5-250">HDInsight hakkında daha fazla bilgi edinmek için Azure HDInsight belgelerine geçin.</span><span class="sxs-lookup"><span data-stu-id="063f5-250">To learn more about HDInsight, continue to the Azure HDInsight Documentation.</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="063f5-251">[Azure HDInsight](../how-to-guides/hdinsight-deploy-methods.md) 
>  üzerinde işleri uzaktan gönderme [Azure HDInsight belgeleri](/azure/hdinsight/)</span><span class="sxs-lookup"><span data-stu-id="063f5-251">[Submit jobs remotely on Azure HDInsight](../how-to-guides/hdinsight-deploy-methods.md)
[Azure HDInsight Documentation](/azure/hdinsight/)</span></span>
