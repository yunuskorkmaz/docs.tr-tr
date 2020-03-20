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
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Azure HDInsight Spark kümelerinde Jupyter dizüstü bilgisayarlarda Apache Spark için .NET'i yükleyin

Bu makalede, Azure HDInsight Spark kümelerinde Jupyter dizüstü bilgisayarlarda Apache Spark için .NET'i nasıl yükleyeceğiniz öğretilir. Komut satırı ve Azure portalının bir birleşimi aracılığıyla Azure HDInsight kümelerinde Apache Spark için .NET dağıtabilirsiniz (daha fazla bilgi için, [Apache Spark uygulaması için bir .NET uygulamasını Azure HDInsight'a nasıl dağıtacağınız](../tutorials/hdinsight-deployment.md)hakkında bilgi edinin) ancak not defterleri daha etkileşimli ve yinelemeli bir deneyim sağlar.

Azure HDInsight kümeleri zaten Jupyter dizüstü bilgisayarlarla birlikte gelir, bu nedenle tek yapmanız gereken Jupyter dizüstü bilgisayarlarını Apache Spark için .NET çalışacak şekilde yapılandırmaktır. Jupyter not defterlerinizde Apache Spark için .NET'i kullanmak için C# kodunuzu satır satır yürütmek ve gerektiğinde yürütme durumunu korumak için c# REPL gerekir. [Try .NET](https://github.com/dotnet/try) resmi .NET REPL olarak entegre edilmiştir.

Jupyter Notebooks deneyimi aracılığıyla .NET for Apache Spark'ı etkinleştirmek için [Ambari'de](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) birkaç el ile adım izlemeniz ve HDInsight Spark kümesinde [komut dosyası eylemleri](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) göndermeniz gerekir.

> [!NOTE]
> Bu özellik *deneyseldir* ve HDInsight Spark ekibi tarafından desteklenmez.

## <a name="prerequisites"></a>Önkoşullar

Zaten bir kümeniz yoksa, bir [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-hdinsight-spark-cluster) kümesi oluşturun.

1. Azure [portalını](https://portal.azure.com) ziyaret edin ve **+ Kaynak Oluştur'u**seçin.

1. Yeni bir Azure HDInsight küme kaynağı oluşturun. Küme oluşturma sırasında **Spark 2.4** ve **HDI 4.0'ı** seçin.

## <a name="install-net-for-apache-spark"></a>Apache Spark için .NET'i yükleyin

Azure portalında, önceki adımda oluşturduğunuz **HDInsight Spark kümesini** seçin.

### <a name="stop-the-livy-server"></a>Livy sunucusunu durdur

1. Portaldan Genel **Bakış'ı**seçin ve ardından **Ambari home'u**seçin. İstenirse, kümenin giriş kimlik bilgilerini girin.

   ![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/select-ambari.png)

2. Sol daki gezinme menüsünden **Spark2'yi** seçin ve **SPARK2 SERVER İçİn LIVY'yi**seçin.

   ![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/select-livyserver.png)

3. **HN0'yi seçin... ana bilgisayar**.

   ![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/select-host.png)

4. **Spark2 Server için Livy'nin** yanındaki elipsleri seçin ve **Durdur'u**seçin. İstendiğinde, devam etmek için **Tamam'ı** seçin.

   Spark2 Server için Livy'yi durdurun.
   ![Livy Server'ı Durdur](./media/hdinsight-notebook-installation/stop-server.png)

5. hn1 için önceki adımları **tekrarlayın... ana bilgisayar**.

### <a name="submit-an-hdinsight-script-action"></a>HDInsight komut dosyası eylemi gönderme

1. Apache `install-interactive-notebook.sh` Spark için .NET'i yükleyen ve Apache Livy ve sparkmagic'te değişiklikler yapan bir komut dosyasıdır. HDInsight'a bir komut dosyası eylemi göndermeden `install-interactive-notebook.sh`önce, oluşturmanız ve yüklemeniz gerekir.

   Yerel bilgisayarınızda **install-interactive-notebook.sh** adlı yeni bir dosya oluşturun ve [install-interactive-notebook.sh içeriğinin içeriğini](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)yapıştırın.

   Komut dosyasını HDInsight kümesinden erişilebilen bir [URI'ye](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) yükleyin. Örneğin, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. `install-interactive-notebook.sh` [HDInsight Script Eylemleri'ni](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)kullanarak kümede çalıştırın.

   Azure portalındaki HDI kümenize dönün ve soldaki seçeneklerden **Komut Dosyası eylemlerini** seçin. HDInsight Spark kümenizde Apache Spark REPL için .NET'i dağıtmak için bir komut dosyası eylemi gönderirsiniz. Aşağıdaki ayarları kullanın:

   |Özellik  |Açıklama  |
   |---------|---------|
   | Komut dosyası türü | Özel |
   | Adı | *Apache Spark İnteraktif Dizüstü Bilgisayar Deneyimi için .NET'i yükleyin* |
   | Bash script URI | Yüklediğiniz `install-interactive-notebook.sh`URI. |
   | Düğüm türü(ler)| Baş ve İşçi |
   | Parametreler | .NET Apache Spark sürümü için. [Apache Spark sürümleri için .NET'i](https://github.com/dotnet/spark/releases)kontrol edebilirsiniz. Örneğin, Sparkdotnet sürüm 0.6.0 yüklemek istiyorsanız o `0.6.0`zaman olacaktır .

   Komut dosyası eyleminin durumunun yanında yeşil onay işaretleri göründüğünde bir sonraki adıma geçin.

### <a name="start-the-livy-server"></a>Livy sunucusunu başlatın

Ev sahipleri **için Spark2** Server için Livy'yi **başlat** **(Durdurmak**yerine) başlata stop [Livy sunucu](#stop-the-livy-server) bölümündeki yönergeleri izleyin. **hn1**

### <a name="set-up-spark-default-configurations"></a>Spark varsayılan yapılandırmalarını ayarlama

1. Portaldan Genel **Bakış'ı**seçin ve ardından **Ambari home'u**seçin. İstendiğinde, küme için küme oturum açma kimlik bilgilerini girin.

2. **Spark2** ve **CONFIGS'ı**seçin. Ardından, **Özel spark2-varsayılanları**seçin.

   ![Configs'i Ayarla](./media/hdinsight-notebook-installation/spark-configs.png)

3. Spark varsayılan ayarlarını eklemek için **Özellik Ekle...'yi** seçin.

   ![Özellik Ekle](./media/hdinsight-notebook-installation/add-property.png)

   Üç ayrı özellik vardır. Tek özellik ekleme modunda **TEXT** özellik türünü kullanarak teker teker ekleyin. Anahtarlardan/değerlerden herhangi birinde veya sonrasında fazladan boşluk bırakmadığınızdan kontrol edin.

   * **Özellik 1**
       * Anahtar:&ensp;&ensp;`spark.dotnet.shell.command`
       * Değer:`/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Özellik 2** Önceki komut dosyası eylemine dahil ettiğiniz Apache Spark için .NET sürümünü kullanın.
       * Anahtar:&ensp;&ensp;`spark.dotnet.packages`
       * Değer:`["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Özellik 3**
       * Anahtar:&ensp;&ensp;`spark.dotnet.interpreter`
       * Değer:`try`

   Örneğin, aşağıdaki görüntü özellik 1 eklemek için ayar yakalar:

   ![Configs'i Ayarla](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Üç özellik ekledikten sonra **KAYDET'i**seçin. Config önerilerinin bir uyarı ekranı görürseniz, **DEVAM EDİ'yi**seçin.

4. Etkilenen bileşenleri yeniden başlatın.

   Yeni özellikleri ekledikten sonra, değişikliklerden etkilenen bileşenleri yeniden başlatmanız gerekir. En **üstte, YENIDEN BAŞLAT'ı**ve ardından açılan noktadan Etkilenen Tüm'leri **Yeniden Başlat'ı** seçin.

   ![Configs'i Ayarla](./media/hdinsight-notebook-installation/restart-affected.png)

   İstendiğinde, devam etmek için **ONAYLA TÜMÜNÜ** ONAYLA'yı seçin ve ardından bitirmek için **Tamam'ı** tıklatın.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Jupyter dizüstü bilgisayarı aracılığıyla iş gönderme

Önceki adımları tamamladıktan sonra, artık .NET'inizi Apache Spark işleri için Jupyter dizüstü bilgisayarlar aracılığıyla gönderebilirsiniz.

1. Apache Spark dizüstü bilgisayar için yeni bir .NET oluşturun. Azure portalında HDI kümenizden bir Jupyter dizüstü bilgisayar başlatın.

   ![Jupyter Notebook'u başlat](./media/hdinsight-notebook-installation/launch-notebook.png)

   Ardından, not defteri oluşturmak için **Yeni** > **.NET Spark (C#)** seçeneğini belirleyin.

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Apache Spark için .NET'i kullanarak iş gönderin.

   DataFrame oluşturmak için aşağıdaki kod parçacıklarını kullanın:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Kıvılcım İşi Gönder](./media/hdinsight-notebook-installation/create-df.png)

   Kullanıcı tanımlı bir işlevi (UDF) kaydetmek ve UDF'yi DataFrames ile kullanmak için aşağıdaki kod parçacıklarını kullanın:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Kıvılcım İşi Gönder](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Sonraki adımlar

* [Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma](../tutorials/hdinsight-deployment.md)
* [HDInsight Dokümantasyon](https://docs.microsoft.com/azure/hdinsight/)
