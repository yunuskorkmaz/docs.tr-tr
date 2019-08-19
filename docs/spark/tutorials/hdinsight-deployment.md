---
title: Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma
description: HDInsight için bir .NET Apache Spark uygulamasının nasıl dağıtılacağını öğrenin.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 4769c194520790ce217d46d1d3197b20742d4f1a
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "69577055"
---
# <a name="deploy-a-net-for-apache-spark-application-to-azure-hdinsight"></a>Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma

Bu öğreticide, Azure HDInsight 'a Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:

> [!div class="checklist"]
> * Microsoft. spark. Worker 'ı hazırla
> * Spark .NET uygulamanızı yayımlama
> * Uygulamanızı Azure HDInsight 'a dağıtma
> * Uygulamanızı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce aşağıdakileri yapın:

* [Azure Depolama Gezgini](https://azure.microsoft.com/features/storage-explorer/)indirin.
* [İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin. Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.

## <a name="prepare-worker-dependencies"></a>Çalışan bağımlılıklarını hazırlama

**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir. Bir C# UDF (Kullanıcı tanımlı işlev) yürütmek istediğinizde Spark 'ıN, UDF 'yi yürütmek IÇIN .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir. **Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.

1. Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.

   Örneğin, kullanmak `.NET for Apache Spark v0.1.0` `netcoreapp2.1`istiyorsanız [Microsoft. spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)dosyasını indirirsiniz.

2. Kümenizin `Microsoft.Spark.Worker.<release>.tar.gz` erişimi olan bir dağıtılmış dosya sistemine (örn., Ida, IDB, ADLS) yükleyin ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) .

## <a name="prepare-your-net-for-apache-spark-app"></a>Apache Spark uygulamanızı .NET 'e hazırlama

1. Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.

2. Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.

   Linux üzerinde aşağıdaki komutu çalıştırabilirsiniz.

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. Yayımlanan `<your app>.zip` dosyalar için üretin.

   Kullanarak `zip`Linux üzerinde aşağıdaki komutu çalıştırabilirsiniz.

   ```bash
   zip -r <your app>.zip .
   ```

4. Aşağıdakileri kümenizin erişimi olan bir dağıtılmış dosya sistemine (örn., IBir, ıDB, ADLS) yükleyin:

   * `microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.
   * `<your app>.zip`
   * Dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler) veya derlemeler (Kullanıcı tanımlı işlevlerinizi ya da `app` bağlı olduğunuz kitaplıkları içeren dll 'ler gibi) her bir yürütücünün çalışma dizinine yerleştirilecek.

## <a name="deploy-to-azure-hdinsight-spark"></a>Azure HDInsight Spark dağıtma

[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-overview) , bulutta bulunan ve kullanıcıların Azure 'da Spark kümeleri başlatma ve yapılandırmalarına olanak tanıyan Apache Spark Microsoft uygulamasıdır. [Azure depolama](https://azure.microsoft.com/services/storage/) veya [Azure Data Lake Storage](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2)depolanan verilerinizi işlemek için HDInsight Spark kümelerini kullanabilirsiniz.

> [!NOTE]
> Azure HDInsight Spark Linux tabanlıdır. Uygulamanızı Azure HDInsight Spark dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.

### <a name="deploy-microsoftsparkworker"></a>Microsoft. spark. Worker 'ı dağıtma

Bu adım kümeniz için yalnızca bir kere gereklidir.

`install-worker.sh` [HDInsight betik eylemlerini](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)kullanarak kümede çalıştırın.

|Ayar|Değer|
|-------|-----|
|Betik türü|Özel|
|Ad|Microsoft. spark. Worker 'ı yükler|
|Bash betiği URI 'SI|Karşıya yüklediğiniz `install-worker.sh`URI. Örneğin, `abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/install-worker.sh`|
|Düğüm türleri|Indan|
|Parametreler|`install-worker.sh`Parametreleri. Örneğin, Azure Data Lake Gen 2 ' `install-worker.sh` ye karşıya yüklenmişse, bu durumda `azure abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz /usr/local/bin`olur.|

![Betik eylemi resmi](./media/hdinsight-deployment/deployment-hdi-action-script.png)

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

İşinizi, veya Apache Livy kullanarak `spark-submit` Azure HDInsight 'a gönderebilirsiniz.

### <a name="use-spark-submit"></a>Spark-gönder kullan

Azure HDInsight 'a Apache Spark işleri için .NET göndermek için [Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.
 
1. `ssh`kümenizdeki baş düğümlerden birine ekleyin.

1. Şunu `spark-submit`Çalıştır:

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip <your app> <app arg 1> <app arg 2> ... <app arg n>
   ```

### <a name="use-apache-livy"></a>Apache Livy kullanın

Apache Spark işlerini bir Azure HDInsight Spark kümesine göndermek için Apache Spark REST API [Apache Livy](https://livy.incubator.apache.org/)'ı kullanabilirsiniz. Daha fazla bilgi için bkz. [Apache Livy Ile uzak işler](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Linux 'ta aşağıdaki komutu kullanarak `curl`çalıştırabilirsiniz:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, .NET Apache Spark uygulamanızı Azure HDInsight 'a dağıttınız. HDInsight hakkında daha fazla bilgi edinmek için Azure HDInsight belgelerine geçin.

> [!div class="nextstepaction"]
> [Azure HDInsight belgeleri](https://docs.microsoft.com/azure/hdinsight/)
