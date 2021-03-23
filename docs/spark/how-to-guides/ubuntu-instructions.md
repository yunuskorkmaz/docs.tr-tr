---
title: Ubuntu üzerinde Apache Spark uygulaması için .NET oluşturma
description: Ubuntu 'da Apache Spark için .NET uygulamanızı nasıl oluşturacağınızı öğrenin
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 300c858a76ba31650615bde70c951e383e9e0436
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875336"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-ubuntu"></a>Ubuntu 'da Apache Spark için .NET uygulamanızı nasıl oluşturacağınızı öğrenin

Bu makalede, Ubuntu üzerinde Apache Spark uygulamalarınızı .NET için nasıl oluşturabileceğiniz öğretilir.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki önkoşulların tümüne zaten sahipseniz, [derleme](#build) adımlarına atlayın.

1. **[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1)** 'sını indirin ve yükleyin-SDK 'yı yüklemek `dotnet` yolunuza toolzincirini ekler.  .NET Core 2,1, 2,2 ve 3,1 desteklenir.

2. **[OpenJDK 8](https://openjdk.java.net/install/)**' i yükler.

   - Aşağıdaki komutu kullanabilirsiniz:

   ```bash
   sudo apt install openjdk-8-jdk
   ```

   * Komut satırınızdan çalıştırabildiğinizi doğrulayın `java` .

      Örnek Java-sürüm çıkışı:

      ```bash
      openjdk version "1.8.0_191"
      OpenJDK Runtime Environment (build 1.8.0_191-8u191-b12-2ubuntu0.18.04.1-b12)
      OpenJDK 64-Bit Server VM (build 25.191-b12, mixed mode)
      ```

   * Zaten birden fazla OpenJDK sürümü yüklüyse ve OpenJDK 8 ' i seçmek istiyorsanız aşağıdaki komutu kullanın:

      ```bash
      sudo update-alternatives --config java
      ```

3. **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**'yi yükler.

   * Şu komutu çalıştırın:

      ```bash
      mkdir -p ~/bin/maven
      cd ~/bin/maven
      wget https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz
      tar -xvzf apache-maven-3.6.0-bin.tar.gz
      ln -s apache-maven-3.6.0 current
      export M2_HOME=~/bin/maven/current
      export PATH=${M2_HOME}/bin:${PATH}
      source ~/.bashrc
      ```

       Terminalinizi kapattığınızda bu ortam değişkenlerinin kaybolacağını unutmayın. Değişikliklerin kalıcı olmasını istiyorsanız, `export` satırları `~/.bashrc` dosyanıza ekleyin.

   * Komut satırınızdan çalıştırabildiğinizi doğrulayın `mvn`

       Örnek MVN sürümü çıkışı:

       ```output
       Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-24T18:41:47Z)
       Maven home: ~/bin/apache-maven-3.6.0
       Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre
       Default locale: en, platform encoding: UTF-8
       OS name: "linux", version: "4.4.0-17763-microsoft", arch: "amd64", family: "unix"
       ```

4. **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**' yı yükler.
[Apache Spark 2.3 +](https://spark.apache.org/downloads.html) indirin ve yerel bir klasöre ayıklayın (ör. `~/bin/spark-3.0.1-bin-hadoop2.7` ). (Desteklenen Spark sürümleri 2,3. *, 2.4.0, 2.4.1, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 3.0.0 ve 3.0.1)

   ```bash
   tar -xvzf /path/to/spark-3.0.1-bin-hadoop2.7.tgz -C ~/bin/spark-3.0.1-bin-hadoop2.7
   ```

   * Gerekli [ortam değişkenlerini](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` (ör. `~/bin/spark-3.0.1-bin-hadoop2.7/` ) ve `PATH` (örn. `$SPARK_HOME/bin:$PATH` ) ekleyin

      ```bash
      export SPARK_HOME=~/bin/spark-3.0.1-hadoop2.7
      export PATH="$SPARK_HOME/bin:$PATH"
      source ~/.bashrc
      ```

      Terminalinizi kapattığınızda bu ortam değişkenlerinin kaybolacağını unutmayın. Değişikliklerin kalıcı olmasını istiyorsanız, `export` satırları `~/.bashrc` dosyanıza ekleyin.

   * Komut satırınızdan çalıştırabildiğinizi doğrulayın `spark-shell` .

      Örnek konsol çıkışı:

      ```
      Welcome to
            ____              __
           / __/__  ___ _____/ /__
          _\ \/ _ \/ _ `/ __/  '_/
         /___/ .__/\_,_/_/ /_/\_\   version 3.0.1
            /_/

      Using Scala version 2.12.10 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
      Type in expressions to have them evaluated.
      Type :help for more information.

      scala> sc
      res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
      ```

Bir `dotnet` `java` `mvn` `spark-shell` sonraki bölüme geçmeden önce komut satırınızdan,,,,,, ' i çalıştırabildiğinizden emin olun. Daha iyi bir yol var mı? Lütfen [bir sorun açıp](https://github.com/dotnet/spark/issues) katkıda bulunmaktan çekinmeyin.

## <a name="build"></a>Derleme

Bu kılavuzun geri kalanında, .NET Apache Spark deposunu makinenize Klonladığınız için, örneğin, `~/dotnet.spark/` .

```bash
git clone https://github.com/dotnet/spark.git ~/dotnet.spark
```

### <a name="build-net-for-spark-scala-extensions-layer"></a>Spark Scala uzantıları katmanı için .NET derleme

.NET uygulaması gönderdiğinizde, Apache Spark için .NET, isteklerinizi nasıl işleyeceğinizi (örneğin, yeni bir Spark oturumu oluşturma isteği, .NET tarafından JVM 'ye veri aktarma isteği vb.) Apache Spark bildiren gerekli mantığı içerir. Bu mantık, [Apache Spark Scala kaynak kodu için .net](https://github.com/dotnet/spark/tree/main/src/scala)içinde bulunabilir.

Sonraki adım, Apache Spark Scala uzantı katmanını .NET için derlemenize yöneliktir:

```bash
cd src/scala
mvn clean package
```

Desteklenen Spark sürümleri için oluşturulan JARs ' i görmeniz gerekir:

* `microsoft-spark-2-3\target\microsoft-spark-2-3_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-2-4\target\microsoft-spark-2-4_2.11-<spark-dotnet-version>.jar`
* `microsoft-spark-3-0\target\microsoft-spark-3-0_2.12-<spark-dotnet-version>.jar`

### <a name="build-net-sample-applications-using-net-core-cli"></a>.NET Core CLI kullanarak .NET örnek uygulamaları oluşturun

Bu bölümde, Apache Spark için .NET [örnek uygulamalarının](https://github.com/dotnet/spark/tree/main/examples) nasıl oluşturulacağı açıklanmaktadır. Bu adımlar, tüm Spark uygulamaları için tüm .NET oluşturma sürecini kavramaya yardımcı olur.

1. Çalışanı oluşturun:

   ```dotnetcli
   cd ~/dotnet.spark/src/csharp/Microsoft.Spark.Worker/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   Örnek konsol çıkışı:

   ```bash
   user@machine:/home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 36.03 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark.Worker/Microsoft.Spark.Worker.csproj.
      Restore completed in 35.94 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.Worker.dll
      Microsoft.Spark.Worker -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```

2. Örnekleri oluşturun:

   ```dotnetcli
   cd ~/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/
   dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   ```

   Örnek konsol çıkışı:

   ```bash
   user@machine:/home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples$ dotnet publish -f netcoreapp3.1 -r ubuntu.18.04-x64
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

      Restore completed in 37.11 ms for /home/user/dotnet.spark/src/csharp/Microsoft.Spark/Microsoft.Spark.csproj.
      Restore completed in 281.63 ms for /home/user/dotnet.spark/examples/Microsoft.Spark.CSharp.Examples/Microsoft.Spark.CSharp.Examples.csproj.
      Microsoft.Spark -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark/Debug/netstandard2.1/Microsoft.Spark.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/Microsoft.Spark.CSharp.Examples.dll
      Microsoft.Spark.CSharp.Examples -> /home/user/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish/
   ```  

## <a name="run-the-net-for-spark-sample-applications"></a>Spark örnek uygulamaları için .NET çalıştırın

Örnekleri derleyip, `spark-submit` .NET Core uygulamalarınızı göndermek için kullanabilirsiniz. [Önkoşul](#prerequisites) bölümünü izlediğinizden ve Apache Spark yüklediğinizden emin olun.

1. `DOTNET_WORKER_DIR`Veya `PATH` ortam değişkenini, `Microsoft.Spark.Worker` ikilinin oluşturulduğu yolu (örn.) içerecek şekilde ayarlayın `~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish` .

   ```bash
   export DOTNET_WORKER_DIR=~/dotnet.spark/artifacts/bin/Microsoft.Spark.Worker/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

2. Bir Terminal açın ve uygulama ikilisinin oluşturulduğu dizine gidin (ör. `~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish` ).

   ```bash
   cd ~/dotnet.spark/artifacts/bin/Microsoft.Spark.CSharp.Examples/Debug/netcoreapp3.1/ubuntu.18.04-x64/publish
   ```

3. Uygulamanızı çalıştırmak temel yapıyı izler:

   ```bash
   spark-submit \
     [--jars <any-jars-your-app-is-dependent-on>] \
     --class org.apache.spark.deploy.dotnet.DotnetRunner \
     --master local \
     <path-to-microsoft-spark-jar> \
     <path-to-your-app-binary> <argument(s)-to-your-app>
   ```

   Şunları çalıştırabilmeniz için bazı örnekler aşağıda verilmiştir:

   * **[Microsoft.Spark.Examples.Sql.Batch. Basit](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Batch.Basic $SPARK_HOME/examples/src/main/resources/people.json
      ```

   * **[Microsoft. spark. Examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

      ```bash
      spark-submit \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredNetworkWordCount localhost 9999
      ```

   * **[Microsoft. spark. Examples. Sql. streaming. StructuredKafkaWordCount (Maven erişilebilir)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
      ```

   * **[Microsoft. spark. Examples. Sql. streaming. StructuredKafkaWordCount (jars sağlanmış)](https://github.com/dotnet/spark/blob/main/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

      ```bash
      spark-submit \
      --jars path/to/net.jpountz.lz4/lz4-1.3.0.jar,path/to/org.apache.kafka/kafka-clients-0.10.0.1.jar,path/to/org.apache.spark/spark-sql-kafka-0-10_2.11-2.3.2.jar,`path/to/org.slf4j/slf4j-api-1.7.6.jar,path/to/org.spark-project.spark/unused-1.0.0.jar,path/to/org.xerial.snappy/snappy-java-1.1.2.6.jar \
      --class org.apache.spark.deploy.dotnet.DotnetRunner \
      --master local \
      ~/dotnet.spark/src/scala/microsoft-spark-<version>/target/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
      Microsoft.Spark.CSharp.Examples Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
       ```
