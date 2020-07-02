---
title: Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark .NET 'i yükler
description: Azure HDInsight 'ın Jupyıter not defterlerine Apache Spark için .NET yüklemeyi öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617749"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark .NET 'i yükler

Bu makalede, Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark için .NET 'i nasıl yükleyeceğiniz öğretilir. Azure HDInsight kümelerinde Apache Spark için .NET 'i komut satırı ve Azure portal bir birleşimiyle dağıtabilirsiniz (daha fazla bilgi için bkz. [Azure HDInsight için .net Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)), ancak Not defterleri daha etkileşimli ve yinelemeli bir deneyim sağlar.

Azure HDInsight kümeleri zaten Jupyıter not defteriyle birlikte geliyor, bu nedenle tüm yapmanız gerekir jupi not defterlerini Apache Spark için .NET çalıştıracak şekilde yapılandırmaktır. Jupyıter Not defterlerinizde Apache Spark için .NET kullanmak istiyorsanız, C# kod satırlarınızın satırını yürütmek için bir C# REPL gerekir ve gerektiğinde yürütme durumunu koruyabilirsiniz. [.Net TRY](https://github.com/dotnet/try) , RESMI .net REPL olarak tümleştirildi.

Jupi Not defterleri deneyimi aracılığıyla Apache Spark için .NET etkinleştirmek istiyorsanız, [ambarı](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) aracılığıyla birkaç el ile adımları Izlemeniz ve HDInsight Spark kümesinde [betik eylemleri](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) göndermeniz gerekir.

> [!NOTE]
> Bu özellik *deneysel* ve HDInsight Spark ekibi tarafından desteklenmiyor.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Ön koşullar

Henüz bir tane yoksa [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) kümesi oluşturun.

1. [Azure Portal](https://portal.azure.com) ziyaret edin ve **+ kaynak oluştur**' u seçin.

1. Yeni bir Azure HDInsight küme kaynağı oluşturun. Küme oluşturma sırasında **Spark 2,4** ve **HDI 4,0** öğesini seçin.

## <a name="install-net-for-apache-spark"></a>Apache Spark için .NET 'i yükler

Azure portal, önceki adımda oluşturduğunuz **HDInsight Spark kümesini** seçin.

### <a name="stop-the-livy-server"></a>Livy sunucusunu durdur

1. Portalda **genel bakış**' ı seçin ve ardından **ambarı giriş**' i seçin. İstenirse, küme için oturum açma kimlik bilgilerini girin.

   ![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/select-ambari.png)

2. Sol gezinti menüsünden **Spark2** ' i SEÇIN ve **Spark2 Server için Livy**' ı seçin.

   ![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/select-livyserver.png)

3. **Hn0 seç... Ana bilgisayar**.

   ![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/select-host.png)

4. **Spark2 Server Için Livy** ' ın yanındaki üç noktayı seçin ve **Durdur**' u seçin. İstendiğinde, devam etmek için **Tamam** ' ı seçin.

   Spark2 Server için Lıvy 'ı durdurun.
   ![Livy sunucusunu durdur](./media/hdinsight-notebook-installation/stop-server.png)

5. Hn1 için önceki adımları tekrarlayın **... Ana bilgisayar**.

### <a name="submit-an-hdinsight-script-action"></a>HDInsight betik eylemi gönderme

1. , `install-interactive-notebook.sh` Apache Spark için .net yükleyen ve Apache Livy ve parlak Magic üzerinde değişiklik yapan bir betiktir. HDInsight 'a bir betik eylemi göndermeden önce oluşturmanız ve yüklemeniz gerekir `install-interactive-notebook.sh` .

   Yerel bilgisayarınızda **install-interactive-Notebook.sh** adlı yeni bir dosya oluşturun ve [install-interactive-Notebook.sh içeriğinin](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)içeriğini yapıştırın.

   Betiği, HDInsight kümesinden erişilebilen bir [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) 'ye yükleyin. Örneğin, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. `install-interactive-notebook.sh` [HDInsight betik eylemlerini](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)kullanarak kümede çalıştırın.

   Azure portal HDI kümenize dönün ve soldaki seçeneklerden **betik eylemleri** ' ni seçin. HDInsight Spark kümenize Apache Spark REPL için .NET dağıtmak üzere bir betik eylemi gönderilir. Aşağıdaki ayarları kullanın:

   |Özellik  |Açıklama  |
   |---------|---------|
   | Betik türü | Özel |
   | Name | *Apache Spark etkileşimli not defteri deneyimi için .NET 'i yükler* |
   | Bash betiği URI 'SI | Karşıya yüklediğiniz URI `install-interactive-notebook.sh` . |
   | Düğüm türleri| Baş ve çalışan |
   | Parametreler | Apache Spark sürümü için .NET. [Apache Spark sürümleri için .net](https://github.com/dotnet/spark/releases)'i kontrol edebilirsiniz. Örneğin, Mini-mini DotNet sürüm 0.6.0 yüklemek istiyorsanız, bu durumda olur `0.6.0` .

   Komut dosyası eyleminin durumunun yanında yeşil onay işaretleri görüntülendiğinde sonraki adıma geçin.

### <a name="start-the-livy-server"></a>Livy sunucusunu Başlat

Konaklar **hn0** ve **Hn1**Için Spark2 Server Için [Livy](#stop-the-livy-server) 'ı **başlatmak** üzere ( **Durdur**yerine)

### <a name="set-up-spark-default-configurations"></a>Spark varsayılan yapılandırmasını ayarlama

1. Portalda **genel bakış**' ı seçin ve ardından **ambarı giriş**' i seçin. İstendiğinde, küme için küme oturum açma kimlik bilgilerini girin.

2. **Spark2** ve **configs**öğesini seçin. Ardından, **özel spark2-varsayılanlar**' ı seçin.

   ![Yapılandırmaları ayarla](./media/hdinsight-notebook-installation/spark-configs.png)

3. Spark varsayılan ayarlarını eklemek için **Özellik Ekle...** öğesini seçin.

   ![Özellik Ekle](./media/hdinsight-notebook-installation/add-property.png)

   Üç ayrı özellik vardır. Tek bir özellik ekleme modunda **metin** özelliği türünü kullanarak bir seferde bir tane ekleyin. Anahtar/değer değerlerinden önce veya sonra fazladan boşluk olmadığından emin olun.

   * **Özellik 1**
       * Anahtar&ensp;&ensp;`spark.dotnet.shell.command`
       * Değer:`/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Özellik 2** Önceki betik eyleminde bulunan Apache Spark için .NET sürümünü kullanın.
       * Anahtar&ensp;&ensp;`spark.dotnet.packages`
       * Değer:`["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`

   * **Özellik 3**
       * Anahtar&ensp;&ensp;`spark.dotnet.interpreter`
       * Değer:`try`

   Örneğin, aşağıdaki görüntü, özellik 1 ' i ekleme ayarını yakalar:

   ![Yapılandırmaları ayarla](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Üç Özellik eklendikten sonra **Kaydet**' i seçin. Yapılandırma önerilerinin uyarı ekranını görürseniz, **yıne de devam et**' i seçin.

4. Etkilenen bileşenleri yeniden başlatın.

   Yeni özellikleri ekledikten sonra değişikliklerden etkilenen bileşenleri yeniden başlatmanız gerekir. En üstte **Yeniden Başlat**' ı seçin ve ardından açılan listeden **etkilenen tüm ' i yeniden başlatın** .

   ![Yapılandırmaları ayarla](./media/hdinsight-notebook-installation/restart-affected.png)

   İstendiğinde, devam etmek için **Tümünü YENIDEN Başlat** ' ı seçin ve ardından **Tamam** ' a tıklayın.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>İşleri Jupyter Not defteri aracılığıyla gönderme

Önceki adımları tamamladıktan sonra, şimdi de jupi Not defterleri aracılığıyla Apache Spark işlerinizi .NET için gönderebilirsiniz.

1. Apache Spark Not defteri için yeni bir .NET oluşturun. Azure portal HDI kümenizdeki bir Jupyter Not defteri başlatın.

   ![Jupyter Notebook Başlat](./media/hdinsight-notebook-installation/launch-notebook.png)

   Sonra **New**  >  bir not defteri oluşturmak için yeni **.net Spark (C#)** öğesini seçin.

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Apache Spark için .NET kullanarak işleri gönderme.

   Bir DataFrame oluşturmak için aşağıdaki kod parçacığını kullanın:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Spark Işi gönder](./media/hdinsight-notebook-installation/create-df.png)

   Kullanıcı tanımlı bir işlev (UDF) kaydetmek ve UDF 'yi DataFrames ile kullanmak için aşağıdaki kod parçacığını kullanın:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Spark Işi gönder](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Sonraki adımlar

* [Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)
* [HDInsight belgeleri](https://docs.microsoft.com/azure/hdinsight/)
