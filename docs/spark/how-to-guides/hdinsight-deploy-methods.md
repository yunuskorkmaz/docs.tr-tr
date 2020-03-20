---
title: Azure HDInsight'a Apache Spark işi için bir .NET gönderme
description: Kıvılcım gönder ve Apache Livy'yi kullanarak Azure HDInsight'a Apache Spark için bir .NET işini nasıl göndereceğinizi öğrenin.
ms.date: 11/19/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 83359f7f613b500a4ce121ce1612cda0ad1191ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185792"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Azure HDInsight'a Apache Spark işi için bir .NET gönderme

Apache Spark için .NET işinizi HDInsight'a `spark-submit` ve Apache Livy'ye dağıtmanın iki yolu vardır.

## <a name="deploy-using-spark-submit"></a>Kıvılcım gönder'i kullanarak dağıtma

Apache [Spark](https://spark.apache.org/docs/latest/submitting-applications.html) işleri için .NET'i Azure HDInsight'a göndermek için kıvılcım gönder komutunu kullanabilirsiniz.

1. Azure portalında HDInsight Spark kümenize gidin ve ardından **SSH + Cluster oturum açma'yı**seçin.

2. Ssh giriş bilgilerini kopyalayın ve girişi bir terminale yapıştırın. Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın. Ubuntu ve Spark'a hoş geldin mesajları görmelisin.

3. UYGULAMANIZI HDInsight kümenizde çalıştırmak için **kıvılcım gönder** komutunu kullanın. Örnek komut dosyasındaki **mycontainer** ve **mystorage account'u** blob kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirmeyi unutmayın. Ayrıca, dağıtım için `microsoft-spark-2.3.x-0.6.0.jar` kullandığınız uygun kavanoz dosyasıyla değiştirdiğinden emin olun. `2.3.x`Apache Spark sürümünü temsil `0.6.0` eder ve [Apache Spark işçisi için .NET](https://github.com/dotnet/spark/releases)sürümünü temsil eder.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Apache Livy kullanarak dağıtın

[Apache Livy](https://livy.incubator.apache.org/),Apache Spark REST API'yi kullanarak Apache Spark işleri için .NET'i bir Azure HDInsight Spark kümesine gönderebilirsiniz. Daha fazla bilgi için, [Apache Livy ile Uzak işleri](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-livy-rest-interface)bakın.

Aşağıdaki komutu Kullanarak Linux `curl`üzerinde çalıştırabilirsiniz:

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile başlayın](../tutorials/get-started.md)
* [Azure HDInsight'a Apache Spark uygulaması için bir .NET dağıtma](../tutorials/hdinsight-deployment.md)
* [HDInsight Dokümantasyon](https://docs.microsoft.com/azure/hdinsight/)
