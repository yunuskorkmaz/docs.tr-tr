---
title: Azure HDInsight Spark kümelerinde Jupyter dizüstü bilgisayarlarda Apache Spark için .NET'i yükleyin
description: Azure HDInsight'ın Jupyter Notebook'larına Apache Spark için .NET'i nasıl yükleyeceğinizi öğrenin.
ms.date: 03/13/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 32047efcde093a3752bdd59baa88896d1547b93e
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546756"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="2b5d3-103">Azure HDInsight Spark kümelerinde Jupyter dizüstü bilgisayarlarda Apache Spark için .NET'i yükleyin</span><span class="sxs-lookup"><span data-stu-id="2b5d3-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="2b5d3-104">Bu makalede, Azure HDInsight Spark kümelerinde Jupyter dizüstü bilgisayarlarda Apache Spark için .NET'i nasıl yükleyeceğiniz öğretilir.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="2b5d3-105">Komut satırı ve Azure portalının bir birleşimi aracılığıyla Azure HDInsight kümelerinde Apache Spark için .NET dağıtabilirsiniz (daha fazla bilgi için, [Apache Spark uygulaması için bir .NET uygulamasını Azure HDInsight'a nasıl dağıtacağınız](../tutorials/hdinsight-deployment.md)hakkında bilgi edinin) ancak not defterleri daha etkileşimli ve yinelemeli bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="2b5d3-106">Azure HDInsight kümeleri zaten Jupyter dizüstü bilgisayarlarla birlikte gelir, bu nedenle tek yapmanız gereken Jupyter dizüstü bilgisayarlarını Apache Spark için .NET çalışacak şekilde yapılandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="2b5d3-107">Jupyter not defterlerinizde Apache Spark için .NET'i kullanmak için C# kodunuzu satır satır yürütmek ve gerektiğinde yürütme durumunu korumak için c# REPL gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="2b5d3-108">[Try .NET](https://github.com/dotnet/try) resmi .NET REPL olarak entegre edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="2b5d3-109">Jupyter Notebooks deneyimi aracılığıyla .NET for Apache Spark'ı etkinleştirmek için [Ambari'de](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) birkaç el ile adım izlemeniz ve HDInsight Spark kümesinde [komut dosyası eylemleri](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="2b5d3-110">Bu özellik *deneyseldir* ve HDInsight Spark ekibi tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2b5d3-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2b5d3-111">Prerequisites</span></span>

<span data-ttu-id="2b5d3-112">Zaten bir kümeniz yoksa, bir [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster) kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster) cluster.</span></span>

1. <span data-ttu-id="2b5d3-113">Azure [portalını](https://portal.azure.com) ziyaret edin ve **+ Kaynak Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="2b5d3-114">Yeni bir Azure HDInsight küme kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="2b5d3-115">Küme oluşturma sırasında **Spark 2.4** ve **HDI 4.0'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="2b5d3-116">Apache Spark için .NET'i yükleyin</span><span class="sxs-lookup"><span data-stu-id="2b5d3-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="2b5d3-117">Azure portalında, önceki adımda oluşturduğunuz **HDInsight Spark kümesini** seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="2b5d3-118">Livy sunucusunu durdur</span><span class="sxs-lookup"><span data-stu-id="2b5d3-118">Stop the Livy server</span></span>

1. <span data-ttu-id="2b5d3-119">Portaldan Genel **Bakış'ı**seçin ve ardından **Ambari home'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="2b5d3-120">İstenirse, kümenin giriş kimlik bilgilerini girin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="2b5d3-122">Sol daki gezinme menüsünden **Spark2'yi** seçin ve **SPARK2 SERVER İçİn LIVY'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="2b5d3-124">**HN0'yi seçin... ana bilgisayar**.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-124">Select **hn0... host**.</span></span>

   ![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="2b5d3-126">**Spark2 Server için Livy'nin** yanındaki elipsleri seçin ve **Durdur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="2b5d3-127">İstendiğinde, devam etmek için **Tamam'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="2b5d3-128">Spark2 Server için Livy'yi durdurun.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="2b5d3-129">![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="2b5d3-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="2b5d3-130">hn1 için önceki adımları **tekrarlayın... ana bilgisayar**.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="2b5d3-131">HDInsight komut dosyası eylemi gönderme</span><span class="sxs-lookup"><span data-stu-id="2b5d3-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="2b5d3-132">Apache `install-interactive-notebook.sh` Spark için .NET'i yükleyen ve Apache Livy ve sparkmagic'te değişiklikler yapan bir komut dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="2b5d3-133">HDInsight'a bir komut dosyası eylemi göndermeden `install-interactive-notebook.sh`önce, oluşturmanız ve yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="2b5d3-134">Yerel bilgisayarınızda **install-interactive-notebook.sh** adlı yeni bir dosya oluşturun ve [install-interactive-notebook.sh içeriğinin içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="2b5d3-135">Komut dosyasını HDInsight kümesinden erişilebilen bir [URI'ye](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="2b5d3-136">Örneğin, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="2b5d3-137">`install-interactive-notebook.sh` [HDInsight Script Eylemleri'ni](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)kullanarak kümede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="2b5d3-138">Azure portalındaki HDI kümenize dönün ve soldaki seçeneklerden **Komut Dosyası eylemlerini** seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="2b5d3-139">HDInsight Spark kümenizde Apache Spark REPL için .NET'i dağıtmak için bir komut dosyası eylemi gönderirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="2b5d3-140">Aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="2b5d3-140">Use the following settings:</span></span>

   |<span data-ttu-id="2b5d3-141">Özellik</span><span class="sxs-lookup"><span data-stu-id="2b5d3-141">Property</span></span>  |<span data-ttu-id="2b5d3-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b5d3-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="2b5d3-143">Komut dosyası türü</span><span class="sxs-lookup"><span data-stu-id="2b5d3-143">Script type</span></span> | <span data-ttu-id="2b5d3-144">Özel</span><span class="sxs-lookup"><span data-stu-id="2b5d3-144">Custom</span></span> |
   | <span data-ttu-id="2b5d3-145">Adı</span><span class="sxs-lookup"><span data-stu-id="2b5d3-145">Name</span></span> | <span data-ttu-id="2b5d3-146">*Apache Spark İnteraktif Dizüstü Bilgisayar Deneyimi için .NET'i yükleyin*</span><span class="sxs-lookup"><span data-stu-id="2b5d3-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="2b5d3-147">Bash script URI</span><span class="sxs-lookup"><span data-stu-id="2b5d3-147">Bash script URI</span></span> | <span data-ttu-id="2b5d3-148">Yüklediğiniz `install-interactive-notebook.sh`URI.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="2b5d3-149">Düğüm türü(ler)</span><span class="sxs-lookup"><span data-stu-id="2b5d3-149">Node type(s)</span></span>| <span data-ttu-id="2b5d3-150">Baş ve İşçi</span><span class="sxs-lookup"><span data-stu-id="2b5d3-150">Head and Worker</span></span> |
   | <span data-ttu-id="2b5d3-151">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b5d3-151">Parameters</span></span> | <span data-ttu-id="2b5d3-152">.NET Apache Spark sürümü için.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="2b5d3-153">[Apache Spark sürümleri için .NET'i](https://github.com/dotnet/spark/releases)kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="2b5d3-154">Örneğin, Sparkdotnet sürüm 0.6.0 yüklemek istiyorsanız o `0.6.0`zaman olacaktır .</span><span class="sxs-lookup"><span data-stu-id="2b5d3-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="2b5d3-155">Komut dosyası eyleminin durumunun yanında yeşil onay işaretleri göründüğünde bir sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="2b5d3-156">Livy sunucusunu başlatın</span><span class="sxs-lookup"><span data-stu-id="2b5d3-156">Start the Livy server</span></span>

<span data-ttu-id="2b5d3-157">Ev sahipleri **için Spark2** Server için Livy'yi **başlat** **(Durdurmak**yerine) başlata stop [Livy sunucu](#stop-the-livy-server) bölümündeki yönergeleri izleyin. **hn1**</span><span class="sxs-lookup"><span data-stu-id="2b5d3-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="2b5d3-158">Spark varsayılan yapılandırmalarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="2b5d3-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="2b5d3-159">Portaldan Genel **Bakış'ı**seçin ve ardından **Ambari home'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="2b5d3-160">İstendiğinde, küme için küme oturum açma kimlik bilgilerini girin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="2b5d3-161">**Spark2** ve **CONFIGS'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="2b5d3-162">Ardından, **Özel spark2-varsayılanları**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Configs'i Ayarla](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="2b5d3-164">Spark varsayılan ayarlarını eklemek için **Özellik Ekle...'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Özellik Ekle](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="2b5d3-166">Üç ayrı özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-166">There are three individual properties.</span></span> <span data-ttu-id="2b5d3-167">Tek özellik ekleme modunda **TEXT** özellik türünü kullanarak teker teker ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="2b5d3-168">Anahtarlardan/değerlerden herhangi birinde veya sonrasında fazladan boşluk bırakmadığınızdan kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="2b5d3-169">**Özellik 1**</span><span class="sxs-lookup"><span data-stu-id="2b5d3-169">**Property 1**</span></span>
       * <span data-ttu-id="2b5d3-170">Anahtar:&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="2b5d3-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="2b5d3-171">Değer:`/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="2b5d3-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="2b5d3-172">**Özellik 2** Önceki komut dosyası eylemine dahil ettiğiniz Apache Spark için .NET sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="2b5d3-173">Anahtar:&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="2b5d3-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="2b5d3-174">Değer:`["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="2b5d3-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="2b5d3-175">**Özellik 3**</span><span class="sxs-lookup"><span data-stu-id="2b5d3-175">**Property 3**</span></span>
       * <span data-ttu-id="2b5d3-176">Anahtar:&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="2b5d3-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="2b5d3-177">Değer:`try`</span><span class="sxs-lookup"><span data-stu-id="2b5d3-177">Value: `try`</span></span>

   <span data-ttu-id="2b5d3-178">Örneğin, aşağıdaki görüntü özellik 1 eklemek için ayar yakalar:</span><span class="sxs-lookup"><span data-stu-id="2b5d3-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Configs'i Ayarla](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="2b5d3-180">Üç özellik ekledikten sonra **KAYDET'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="2b5d3-181">Config önerilerinin bir uyarı ekranı görürseniz, **DEVAM EDİ'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="2b5d3-182">Etkilenen bileşenleri yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-182">Restart affected components.</span></span>

   <span data-ttu-id="2b5d3-183">Yeni özellikleri ekledikten sonra, değişikliklerden etkilenen bileşenleri yeniden başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="2b5d3-184">En **üstte, YENIDEN BAŞLAT'ı**ve ardından açılan noktadan Etkilenen Tüm'leri **Yeniden Başlat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Configs'i Ayarla](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="2b5d3-186">İstendiğinde, devam etmek için **ONAYLA TÜMÜNÜ** ONAYLA'yı seçin ve ardından bitirmek için **Tamam'ı** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="2b5d3-187">Jupyter dizüstü bilgisayarı aracılığıyla iş gönderme</span><span class="sxs-lookup"><span data-stu-id="2b5d3-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="2b5d3-188">Önceki adımları tamamladıktan sonra, artık .NET'inizi Apache Spark işleri için Jupyter dizüstü bilgisayarlar aracılığıyla gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="2b5d3-189">Apache Spark dizüstü bilgisayar için yeni bir .NET oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="2b5d3-190">Azure portalında HDI kümenizden bir Jupyter dizüstü bilgisayar başlatın.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Jupyter Notebook'u başlat](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="2b5d3-192">Ardından, not defteri oluşturmak için **Yeni** > **.NET Spark (C#)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="2b5d3-194">Apache Spark için .NET'i kullanarak iş gönderin.</span><span class="sxs-lookup"><span data-stu-id="2b5d3-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="2b5d3-195">DataFrame oluşturmak için aşağıdaki kod parçacıklarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="2b5d3-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Kıvılcım İşi Gönder](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="2b5d3-197">Kullanıcı tanımlı bir işlevi (UDF) kaydetmek ve UDF'yi DataFrames ile kullanmak için aşağıdaki kod parçacıklarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="2b5d3-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Kıvılcım İşi Gönder](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="2b5d3-199">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2b5d3-199">Next steps</span></span>

* [<span data-ttu-id="2b5d3-200">Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="2b5d3-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="2b5d3-201">HDInsight Dokümantasyon</span><span class="sxs-lookup"><span data-stu-id="2b5d3-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
