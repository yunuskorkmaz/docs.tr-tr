---
title: Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama
description: Windows 'da Apache Spark için .NET uygulamanızı nasıl ayıklayacağınızı öğrenin.
ms.date: 08/15/2019
ms.topic: how-to
ms.custom: mvc
ms.openlocfilehash: 08142bd45c475ddd131053213ebdea5f843fa736
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69667660"
---
# <a name="debug-a-net-for-apache-spark-application"></a>Apache Spark uygulama için bir .NET hatası ayıklama

Bu nasıl yapılır, Windows 'da Apache Spark uygulaması ve Scala kodu için .NET uygulamanızda hata ayıklamak üzere çalıştırmanız gereken komutları sağlar.

## <a name="debug-your-application"></a>Uygulamanızda hata ayıklama

Yeni bir komut istemi penceresi açın, aşağıdakileri çalıştırın:

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

Komutu çalıştırdığınızda aşağıdaki çıktıyı görürsünüz:

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

Bu hata ayıklama modunda, `DotnetRunner` .NET uygulamasını başlatamaz, ancak bağlanmasını bekler. Bu komut istemi penceresini açık bırakın.

Artık uygulamanızda hata ayıklamak için, .NET uygulamanızı herhangi bir hata ayıklayıcı ile çalıştırabilirsiniz.

## <a name="debug-scala-code"></a>Scala kodunda hata ayıklama

`DotnetRunner` Ya`DotnetBackendHandler`da gibi Scala tarafı kodunda hata ayıklaması yapmanız gerekiyorsa, aşağıdaki komutu çalıştırın:

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

Komutu çalıştırdıktan sonra, [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)kullanarak çalışan işleme bir hata ayıklayıcı ekleyin.

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
* [Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)
* [Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı](../tutorials/databricks-deployment.md)
* [Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma](../tutorials/amazon-emr-spark-deployment.md)