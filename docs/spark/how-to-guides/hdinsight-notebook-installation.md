---
title: Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark .NET 'i yükler
description: Azure HDInsight 'ın Jupyıter not defterlerine Apache Spark için .NET yüklemeyi öğrenin.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: b84d61c29d2b2aa7a9fee20a8af9f3eee23f7e8b
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605483"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a>Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark .NET 'i yükler

Bu makalede, Azure HDInsight Spark kümelerinde Jupyıter not defterlerine Apache Spark için .NET 'i nasıl yükleyeceğiniz öğretilir. Azure HDInsight kümelerinde Apache Spark için .NET 'i komut satırı ve Azure portal bir birleşimiyle dağıtabilirsiniz (daha fazla bilgi için bkz. [Azure HDInsight için .net Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)), ancak Not defterleri daha etkileşimli ve yinelemeli bir deneyim sağlar.

Azure HDInsight kümeleri zaten Jupyıter not defteriyle birlikte geliyor, bu nedenle tüm yapmanız gerekir jupi not defterlerini Apache Spark için .NET çalıştıracak şekilde yapılandırmaktır. Jupyıter Not defterlerinizde Apache Spark için .NET kullanmak istiyorsanız, C# kod satırlarınızın satırını yürütmek için bir C# REPL gerekir ve gerektiğinde yürütme durumunu koruyabilirsiniz. [.Net TRY](https://github.com/dotnet/try) , RESMI .net REPL olarak tümleştirildi.

Jupi Not defterleri deneyimi aracılığıyla Apache Spark için .NET etkinleştirmek istiyorsanız, [ambarı](/azure/hdinsight/hdinsight-hadoop-manage-ambari) aracılığıyla birkaç el ile adımları Izlemeniz ve HDInsight Spark kümesinde [betik eylemleri](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) göndermeniz gerekir.

> [!NOTE]
> Bu özellik *deneysel* ve HDInsight Spark ekibi tarafından desteklenmiyor.

## <a name="prerequisites"></a>Önkoşullar

Henüz bir tane yoksa [Azure HDInsight Spark](/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) kümesi oluşturun.

1. [Azure Portal](https://portal.azure.com) ziyaret edin ve **+ kaynak oluştur**' u seçin.

1. Yeni bir Azure HDInsight küme kaynağı oluşturun. Küme oluşturma sırasında **Spark 2,4** ve **HDI 4,0** öğesini seçin.

## <a name="install-net-for-apache-spark"></a>Apache Spark için .NET 'i yükler

Azure portal, önceki adımda oluşturduğunuz **HDInsight Spark kümesini** seçin.

### <a name="stop-the-livy-server"></a>Livy sunucusunu durdur

1. Portalda **genel bakış**' ı seçin ve ardından **ambarı giriş**' i seçin. İstenirse, küme için oturum açma kimlik bilgilerini girin.

   ![Küme panoları altında ambarı giriş ' i seçin](./media/hdinsight-notebook-installation/select-ambari.png)

2. Sol gezinti menüsünden **Spark2** ' i SEÇIN ve **Spark2 Server için Livy**' ı seçin.

   ![Spark2 sunucusu için Livy seçin](./media/hdinsight-notebook-installation/select-livyserver.png)

3. **Hn0 seç... Ana bilgisayar**.

   !["Hno..." gösteren konaklar seçildiğinde](./media/hdinsight-notebook-installation/select-host.png)

4. **Spark2 Server Için Livy** ' ın yanındaki üç noktayı seçin ve **Durdur**' u seçin. İstendiğinde, devam etmek için **Tamam** ' ı seçin.

   Spark2 Server için Lıvy 'ı durdurun.
   ![Üç noktayı seçin ve ardından Durdur](./media/hdinsight-notebook-installation/stop-server.png)

5. Hn1 için önceki adımları tekrarlayın **... Ana bilgisayar**.

### <a name="submit-an-hdinsight-script-action"></a>HDInsight betik eylemi gönderme

1. , `install-interactive-notebook.sh` Apache Spark için .net yükleyen ve Apache Livy ve parlak Magic üzerinde değişiklik yapan bir betiktir. HDInsight 'a bir betik eylemi göndermeden önce oluşturmanız ve yüklemeniz gerekir `install-interactive-notebook.sh` .

   Yerel bilgisayarınızda **install-interactive-Notebook.sh** adlı yeni bir dosya oluşturun ve [install-interactive-Notebook.sh içeriğinin](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)içeriğini yapıştırın.

   Betiği, HDInsight kümesinden erişilebilen bir [URI](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) 'ye yükleyin. Örneğin, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.

2. `install-interactive-notebook.sh` [HDInsight betik eylemlerini](/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)kullanarak kümede çalıştırın.

   Azure portal HDI kümenize dönün ve soldaki seçeneklerden **betik eylemleri** ' ni seçin. HDInsight Spark kümenize Apache Spark REPL için .NET dağıtmak üzere bir betik eylemi gönderilir. Aşağıdaki ayarları kullanın:

   |Özellik  |Açıklama  |
   |---------|---------|
   | Betik türü | Özel |
   | Name | *Apache Spark etkileşimli not defteri deneyimi için .NET 'i yükler* |
   | Bash betiği URI 'SI | Karşıya yüklediğiniz URI `install-interactive-notebook.sh` . |
   | Düğüm türleri| Baş ve çalışan |
   | Parametreler | Apache Spark sürümü için .NET. [Apache Spark sürümleri için .net](https://github.com/dotnet/spark/releases)'i kontrol edebilirsiniz. Örneğin, Mini-mini DotNet sürüm 1.0.0 yüklemek istiyorsanız, bu durumda olur `1.0.0` .

   Komut dosyası eyleminin durumunun yanında yeşil onay işaretleri görüntülendiğinde sonraki adıma geçin.

### <a name="start-the-livy-server"></a>Livy sunucusunu Başlat

Konaklar **hn0** ve **Hn1** Için Spark2 Server Için [Livy](#stop-the-livy-server) 'ı **başlatmak** üzere ( **Durdur** yerine)

### <a name="set-up-spark-default-configurations"></a>Spark varsayılan yapılandırmasını ayarlama

1. Portalda **genel bakış**' ı seçin ve ardından **ambarı giriş**' i seçin. İstendiğinde, küme için küme oturum açma kimlik bilgilerini girin.

2. **Spark2** ve **configs** öğesini seçin. Ardından, **özel spark2-varsayılanlar**' ı seçin.

   ![Ambarı 'nda configs sekmesi](./media/hdinsight-notebook-installation/spark-configs.png)

3. Spark varsayılan ayarlarını eklemek için **Özellik Ekle** ' yi seçin.

   ![Özellik Ekle](./media/hdinsight-notebook-installation/add-property.png)

   Üç ayrı özellik vardır. Tek bir özellik ekleme modunda **metin** özelliği türünü kullanarak bir seferde bir tane ekleyin. Anahtar/değer değerlerinden önce veya sonra fazladan boşluk olmadığından emin olun.

   * **Özellik 1**
       * Anahtar&ensp;&ensp;`spark.dotnet.shell.command`
       * Değer: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`

   * **Özellik 2** Önceki betik eyleminde bulunan Apache Spark için .NET sürümünü kullanın.
       * Anahtar&ensp;&ensp;`spark.dotnet.packages`
       * Değer: `["nuget: Microsoft.Spark, 1.0.0", "nuget: Microsoft.Spark.Extensions.Delta, 1.0.0"]`

   * **Özellik 3**
       * Anahtar&ensp;&ensp;`spark.dotnet.interpreter`
       * Değer: `try`

   Örneğin, aşağıdaki görüntü, özellik 1 ' i ekleme ayarını yakalar:

   ![Metin özelliği Ekle](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   Üç Özellik eklendikten sonra **Kaydet**' i seçin. Yapılandırma önerilerinin uyarı ekranını görürseniz, **yıne de devam et**' i seçin.

4. Etkilenen bileşenleri yeniden başlatın.

   Yeni özellikleri ekledikten sonra değişikliklerden etkilenen bileşenleri yeniden başlatmanız gerekir. En üstte **Yeniden Başlat**' ı seçin ve ardından açılan listeden **etkilenen tüm ' i yeniden başlatın** .

   ![Yeniden başlatma > configs sekmesi, etkilenen tüm vurgulanmış vurgulanmış olarak yeniden Başlat](./media/hdinsight-notebook-installation/restart-affected.png)

   İstendiğinde, devam etmek için **Tümünü YENIDEN Başlat** ' ı seçin ve ardından **Tamam** ' a tıklayın.

## <a name="submit-jobs-through-a-jupyter-notebook"></a>Jupyter Notebook aracılığıyla iş gönderme

Önceki adımları tamamladıktan sonra, şimdi de jupi Not defterleri aracılığıyla Apache Spark işlerinizi .NET için gönderebilirsiniz.

1. Apache Spark Not defteri için yeni bir .NET oluşturun. Azure portal HDI kümenizdeki bir Jupyter Notebook başlatın.

   ![Jupyter Notebook Başlat](./media/hdinsight-notebook-installation/launch-notebook.png)

   Sonra   >  bir not defteri oluşturmak için yeni **.net Spark (C#)** öğesini seçin.

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. Apache Spark için .NET kullanarak işleri gönderme.

   Bir DataFrame oluşturmak için aşağıdaki kod parçacığını kullanın:

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Komut yürütmeyi gösteren bir DataFrame oluştur](./media/hdinsight-notebook-installation/create-df.png)

   Kullanıcı tanımlı bir işlev (UDF) kaydetmek ve UDF 'yi DataFrames ile kullanmak için aşağıdaki kod parçacığını kullanın:

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![UDF kaydetme ve kullanma](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a>Sonraki adımlar

* [Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)
* [HDInsight belgeleri](/azure/hdinsight/)
