---
title: Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark .NET 'i yükler
description: Azure HDInsight 'ın Jupyıter not defterlerine Apache Spark için .NET yüklemeyi öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 8110b87991e2f0253257faf19f383dec6cbd3853
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557209"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="ec8fe-103">Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="ec8fe-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="ec8fe-104">Bu makalede, Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark için .NET 'i nasıl yükleyeceğiniz öğretilir.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="ec8fe-105">Azure HDInsight kümelerinde Apache Spark için .NET 'i komut satırı ve Azure portal bir birleşimiyle dağıtabilirsiniz (daha fazla bilgi için bkz. [Azure HDInsight için .net Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)), ancak Not defterleri daha etkileşimli ve yinelemeli bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="ec8fe-106">Azure HDInsight kümeleri zaten Jupyıter not defteriyle birlikte geliyor, bu nedenle tüm yapmanız gerekir jupi not defterlerini Apache Spark için .NET çalıştıracak şekilde yapılandırmaktır.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="ec8fe-107">Jupyıter Not defterlerinizde Apache Spark için .NET kullanmak istiyorsanız, C# kod satırlarınızın satırını yürütmek için bir C# REPL gerekir ve gerektiğinde yürütme durumunu koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="ec8fe-108">[.Net TRY](https://github.com/dotnet/try) , RESMI .net REPL olarak tümleştirildi.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="ec8fe-109">Jupi Not defterleri deneyimi aracılığıyla Apache Spark için .NET etkinleştirmek istiyorsanız, [ambarı](/azure/hdinsight/hdinsight-hadoop-manage-ambari) aracılığıyla birkaç el ile adımları Izlemeniz ve HDInsight Spark kümesinde [betik eylemleri](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="ec8fe-110">Bu özellik *deneysel* ve HDInsight Spark ekibi tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="ec8fe-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ec8fe-111">Prerequisites</span></span>

<span data-ttu-id="ec8fe-112">Henüz bir tane yoksa [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-112">If you don't already have one, create an [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="ec8fe-113">[Azure Portal](https://portal.azure.com) ziyaret edin ve **+ kaynak oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="ec8fe-114">Yeni bir Azure HDInsight küme kaynağı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="ec8fe-115">Küme oluşturma sırasında **Spark 2,4** ve **HDI 4,0** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="ec8fe-116">Apache Spark için .NET 'i yükler</span><span class="sxs-lookup"><span data-stu-id="ec8fe-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="ec8fe-117">Azure portal, önceki adımda oluşturduğunuz **HDInsight Spark kümesini** seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="ec8fe-118">Livy sunucusunu durdur</span><span class="sxs-lookup"><span data-stu-id="ec8fe-118">Stop the Livy server</span></span>

1. <span data-ttu-id="ec8fe-119">Portalda **genel bakış**' ı seçin ve ardından **ambarı giriş**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="ec8fe-120">İstenirse, küme için oturum açma kimlik bilgilerini girin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="ec8fe-122">Sol gezinti menüsünden **Spark2** ' i SEÇIN ve **Spark2 Server için Livy**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="ec8fe-124">**Hn0 seç... Ana bilgisayar**.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-124">Select **hn0... host**.</span></span>

   ![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="ec8fe-126">**Spark2 Server Için Livy** ' ın yanındaki üç noktayı seçin ve **Durdur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="ec8fe-127">İstendiğinde, devam etmek için **Tamam** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="ec8fe-128">Spark2 Server için Lıvy 'ı durdurun.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="ec8fe-129">![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="ec8fe-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="ec8fe-130">Hn1 için önceki adımları tekrarlayın **... Ana bilgisayar**.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="ec8fe-131">HDInsight betik eylemi gönderme</span><span class="sxs-lookup"><span data-stu-id="ec8fe-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="ec8fe-132">, `install-interactive-notebook.sh` Apache Spark için .net yükleyen ve Apache Livy ve parlak Magic üzerinde değişiklik yapan bir betiktir.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="ec8fe-133">HDInsight 'a bir betik eylemi göndermeden önce oluşturmanız ve yüklemeniz gerekir `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="ec8fe-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="ec8fe-134">Yerel bilgisayarınızda **install-interactive-Notebook.sh** adlı yeni bir dosya oluşturun ve [install-interactive-Notebook.sh içeriğinin](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)içeriğini yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="ec8fe-135">Betiği, HDInsight kümesinden erişilebilen bir [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) 'ye yükleyin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-135">Upload the script to a [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="ec8fe-136">Örneğin, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="ec8fe-137">`install-interactive-notebook.sh` [HDInsight betik eylemlerini](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)kullanarak kümede çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="ec8fe-138">Azure portal HDI kümenize dönün ve soldaki seçeneklerden **betik eylemleri** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="ec8fe-139">HDInsight Spark kümenize Apache Spark REPL için .NET dağıtmak üzere bir betik eylemi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="ec8fe-140">Aşağıdaki ayarları kullanın:</span><span class="sxs-lookup"><span data-stu-id="ec8fe-140">Use the following settings:</span></span>

   |<span data-ttu-id="ec8fe-141">Özellik</span><span class="sxs-lookup"><span data-stu-id="ec8fe-141">Property</span></span>  |<span data-ttu-id="ec8fe-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec8fe-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="ec8fe-143">Betik türü</span><span class="sxs-lookup"><span data-stu-id="ec8fe-143">Script type</span></span> | <span data-ttu-id="ec8fe-144">Özel</span><span class="sxs-lookup"><span data-stu-id="ec8fe-144">Custom</span></span> |
   | <span data-ttu-id="ec8fe-145">Name</span><span class="sxs-lookup"><span data-stu-id="ec8fe-145">Name</span></span> | <span data-ttu-id="ec8fe-146">*Apache Spark etkileşimli not defteri deneyimi için .NET 'i yükler*</span><span class="sxs-lookup"><span data-stu-id="ec8fe-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="ec8fe-147">Bash betiği URI 'SI</span><span class="sxs-lookup"><span data-stu-id="ec8fe-147">Bash script URI</span></span> | <span data-ttu-id="ec8fe-148">Karşıya yüklediğiniz URI `install-interactive-notebook.sh` .</span><span class="sxs-lookup"><span data-stu-id="ec8fe-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="ec8fe-149">Düğüm türleri</span><span class="sxs-lookup"><span data-stu-id="ec8fe-149">Node type(s)</span></span>| <span data-ttu-id="ec8fe-150">Baş ve çalışan</span><span class="sxs-lookup"><span data-stu-id="ec8fe-150">Head and Worker</span></span> |
   | <span data-ttu-id="ec8fe-151">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec8fe-151">Parameters</span></span> | <span data-ttu-id="ec8fe-152">Apache Spark sürümü için .NET.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="ec8fe-153">[Apache Spark sürümleri için .net](https://github.com/dotnet/spark/releases)'i kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="ec8fe-154">Örneğin, Mini-mini DotNet sürüm 0.6.0 yüklemek istiyorsanız, bu durumda olur `0.6.0` .</span><span class="sxs-lookup"><span data-stu-id="ec8fe-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="ec8fe-155">Komut dosyası eyleminin durumunun yanında yeşil onay işaretleri görüntülendiğinde sonraki adıma geçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="ec8fe-156">Livy sunucusunu Başlat</span><span class="sxs-lookup"><span data-stu-id="ec8fe-156">Start the Livy server</span></span>

<span data-ttu-id="ec8fe-157">Konaklar **hn0** ve **Hn1**Için Spark2 Server Için [Livy](#stop-the-livy-server) 'ı **başlatmak** üzere ( **Durdur**yerine)</span><span class="sxs-lookup"><span data-stu-id="ec8fe-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="ec8fe-158">Spark varsayılan yapılandırmasını ayarlama</span><span class="sxs-lookup"><span data-stu-id="ec8fe-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="ec8fe-159">Portalda **genel bakış**' ı seçin ve ardından **ambarı giriş**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="ec8fe-160">İstendiğinde, küme için küme oturum açma kimlik bilgilerini girin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="ec8fe-161">**Spark2** ve **configs**öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="ec8fe-162">Ardından, **özel spark2-varsayılanlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-162">Then, select **Custom spark2-defaults**.</span></span>

   ![Yapılandırmaları ayarla](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="ec8fe-164">Spark varsayılan ayarlarını eklemek için **Özellik Ekle...** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![Özellik Ekle](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="ec8fe-166">Üç ayrı özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-166">There are three individual properties.</span></span> <span data-ttu-id="ec8fe-167">Tek bir özellik ekleme modunda **metin** özelliği türünü kullanarak bir seferde bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="ec8fe-168">Anahtar/değer değerlerinden önce veya sonra fazladan boşluk olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="ec8fe-169">**Özellik 1**</span><span class="sxs-lookup"><span data-stu-id="ec8fe-169">**Property 1**</span></span>
       * <span data-ttu-id="ec8fe-170">Anahtar&ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="ec8fe-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="ec8fe-171">Değer: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="ec8fe-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="ec8fe-172">**Özellik 2** Önceki betik eyleminde bulunan Apache Spark için .NET sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="ec8fe-173">Anahtar&ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="ec8fe-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="ec8fe-174">Değer: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="ec8fe-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="ec8fe-175">**Özellik 3**</span><span class="sxs-lookup"><span data-stu-id="ec8fe-175">**Property 3**</span></span>
       * <span data-ttu-id="ec8fe-176">Anahtar&ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="ec8fe-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="ec8fe-177">Değer: `try`</span><span class="sxs-lookup"><span data-stu-id="ec8fe-177">Value: `try`</span></span>

   <span data-ttu-id="ec8fe-178">Örneğin, aşağıdaki görüntü, özellik 1 ' i ekleme ayarını yakalar:</span><span class="sxs-lookup"><span data-stu-id="ec8fe-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![Yapılandırmaları ayarla](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="ec8fe-180">Üç Özellik eklendikten sonra **Kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="ec8fe-181">Yapılandırma önerilerinin uyarı ekranını görürseniz, **yıne de devam et**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="ec8fe-182">Etkilenen bileşenleri yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-182">Restart affected components.</span></span>

   <span data-ttu-id="ec8fe-183">Yeni özellikleri ekledikten sonra değişikliklerden etkilenen bileşenleri yeniden başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="ec8fe-184">En üstte **Yeniden Başlat**' ı seçin ve ardından açılan listeden **etkilenen tüm ' i yeniden başlatın** .</span><span class="sxs-lookup"><span data-stu-id="ec8fe-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![Yapılandırmaları ayarla](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="ec8fe-186">İstendiğinde, devam etmek için **Tümünü YENIDEN Başlat** ' ı seçin ve ardından **Tamam** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="ec8fe-187">İşleri Jupyter Not defteri aracılığıyla gönderme</span><span class="sxs-lookup"><span data-stu-id="ec8fe-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="ec8fe-188">Önceki adımları tamamladıktan sonra, şimdi de jupi Not defterleri aracılığıyla Apache Spark işlerinizi .NET için gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="ec8fe-189">Apache Spark Not defteri için yeni bir .NET oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="ec8fe-190">Azure portal HDI kümenizdeki bir Jupyter Not defteri başlatın.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Jupyter Notebook Başlat](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="ec8fe-192">Sonra **New**  >  bir not defteri oluşturmak için yeni **.net Spark (C#)** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="ec8fe-194">Apache Spark için .NET kullanarak işleri gönderme.</span><span class="sxs-lookup"><span data-stu-id="ec8fe-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="ec8fe-195">Bir DataFrame oluşturmak için aşağıdaki kod parçacığını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ec8fe-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Spark Işi gönder](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="ec8fe-197">Kullanıcı tanımlı bir işlev (UDF) kaydetmek ve UDF 'yi DataFrames ile kullanmak için aşağıdaki kod parçacığını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ec8fe-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Spark Işi gönder](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="ec8fe-199">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ec8fe-199">Next steps</span></span>

* [<span data-ttu-id="ec8fe-200">Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="ec8fe-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="ec8fe-201">HDInsight belgeleri</span><span class="sxs-lookup"><span data-stu-id="ec8fe-201">HDInsight Documentation</span></span>](/azure/hdinsight/)
