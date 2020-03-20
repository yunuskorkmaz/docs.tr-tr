---
title: Windows'da Apache Spark uygulaması için bir .NET oluşturma
description: Windows'da Apache Spark uygulaması için .NET'inizi nasıl oluşturacağınızı öğrenin.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185753"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Windows'da Apache Spark uygulaması için .NET uygulamanızı nasıl oluşturacağınızı öğrenin

Bu makalede, Windows'da Apache Spark uygulamaları için .NET'inizi nasıl oluşturabileceğinizöğretilir.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki ön koşulların tümüne zaten sahipseniz, [yapı](#build) adımlarına atlayın.

  1. .NET **[Core SDK'yı](https://dotnet.microsoft.com/download/dotnet-core/2.1)** indirin ve kurun `dotnet` - SDK'yı yüklemek araç zincirini yolunuza ekleyecek. .NET Core 2.1, 2.2 ve 3.1 desteklenir.
  2. **[Visual Studio 2019'u](https://www.visualstudio.com/downloads/)** yükleyin (Sürüm 16.3 veya sonrası). Topluluk sürümü tamamen ücretsizdir. Yüklemenizi yapılandırırken, bu bileşenleri en az olarak ekleyin:
     * .NET masaüstü geliştirme
       * Gerekli Tüm Bileşenler
         * .NET Framework 4.6.1 Geliştirme Araçları
     * .NET Core çoklu platform geliştirme
       * Gerekli Tüm Bileşenler
  3. **[Java 1.8'i yükleyin.](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**
     - İşletim sisteminiz için uygun sürümü seçin. Örneğin, Windows x64 makine için *jdk-8u201-windows-x64.exe.*
     - Yükleyiciyi kullanarak yükleyin ve komut `java` satırınızdan çalıştırabileceğinizi doğrulayın.
  4. **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)** yükleyin.
     - Karşıdan yükleme [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Yerel bir dizine ayıklayın. Örneğin, *C:\bin\apache-maven-3.6.0\*.
     - Apache Maven'i [PATH ortamı değişkenine](https://www.java.com/en/download/help/path.xml)ekleyin. Örneğin, *C:\bin\apache-maven-3.6.0\bin*.
     - Komut satırınızdan çalıştırabileceğinizi `mvn` doğrulayın.
  5. **[Apache Spark 2.3+ yükleyin.](https://spark.apache.org/downloads.html)**
     - [Apache Spark 2.3+](https://spark.apache.org/downloads.html) indirin ve 7 zip kullanarak yerel bir klasöre (örneğin, *C:\bin\spark-2.3.2-bin-hadoop2.7)\*ayıklayın. [7-zip](https://www.7-zip.org/) (Desteklenen kıvılcım versiyonları 2.3.*, 2.4.0, 2.4.1, 2.4.3 ve 2.4.4)
     - Yeni bir [ortam değişkeni](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`ekleyin. Örneğin, *C:\bin\spark-2.3.2-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - [PATH ortamı değişkeninize](https://www.java.com/en/download/help/path.xml)Apache Spark ekleyin. Örneğin, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Komut satırınızdan çalıştırabileceğinizi `spark-shell` doğrulayın.
        Örnek konsol çıkışı:

        ```
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. **[WinUtils'i](https://github.com/steveloughran/winutils)** yükleyin.
     - `winutils.exe` [WinUtils deposundan ikili indirin.](https://github.com/steveloughran/winutils) Spark dağıtımının derlenmiş olduğu Hadoop sürümünü seçmelisiniz. Exammple için, Spark 2.3.2 için hadoop-2.7.1 kullanın.
     - İkiliyi seçtiğiniz bir dizine kaydedin. `winutils.exe` Örneğin, *C:\hadoop\bin*.
     - Winutils.exe (çöp kutusu olmadan) ile dizin yansıtacak şekilde ayarlayın. `HADOOP_HOME` Örneğin, komut satırı kullanarak:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - PATH ortamı değişkenini ' eklenecek `%HADOOP_HOME%\bin`şekilde ayarlayın Örneğin, komut satırLarını kullanarak:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Bir sonraki bölüme `dotnet`geçmeden `java` `mvn`önce `spark-shell` komut satırınızdan , , , çalıştırabildiğinizden emin olun. Daha iyi bir yol olduğunu mu düşünüyorsun? [Bir sorun açın](https://github.com/dotnet/spark/issues) ve katkıda bulunmakiçin çekinmeyin.

> [!NOTE]
> Herhangi bir ortam değişkeni güncelleştirilmişse komut satırının yeni bir örneği gerekebilir.

## <a name="build"></a>Oluşturma

Bu kılavuzun geri kalanı için, Apache Spark deposu için .NET'i makinenize klonlamış olmanız gerekir. Klonlanmış depo için istediğiniz yeri seçebilirsiniz. Örneğin, *C:\github\dotnet-spark\*.

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Apache Scala uzantıları katmanı için .NET oluştur

Bir .NET başvurusu gönderdiğinizde , .NET for Apache Spark'ın Scala'da yazılmış olması gereken mantık Scala'da yazılıdır ve isteklerinizi nasıl işleyeceğinizi bildirir (örneğin, yeni bir Kıvılcım Oturumu oluşturma isteği, .NET tarafından JVM tarafına veri aktarımı isteği vb.). Bu mantık [Spark Scala Kaynak Kodu için .NET](https://github.com/dotnet/spark/tree/master/src/scala)bulunabilir.

.NET Framework veya .NET Core kullanıyor sanız, Apache Spark Scala uzantı katmanı için .NET'i oluşturmanız gerekir:

```powershell
cd src\scala
mvn clean package
```

Desteklenen Spark sürümleri için oluşturulan JAR'ları görmelisiniz:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Kıvılcım örnek uygulamaları için .NET'i oluşturun

Bu bölümde, Apache Spark için .NET [için örnek uygulamaların](https://github.com/dotnet/spark/tree/master/examples) nasıl oluşturulabildiği açıklanmaktadır. Bu adımlar, Kıvılcım uygulaması için herhangi bir .NET için genel oluşturma işlemini anlamada yardımcı olacaktır.

#### <a name="using-visual-studio-for-net-framework"></a>.NET Framework için Visual Studio'u kullanma

  1. Visual `src\csharp\Microsoft.Spark.sln` Studio'da açın `Microsoft.Spark.CSharp.Examples` ve `examples` projeyi klasörün altında oluşturun (bu da .NET ciltleme projesini oluşturur). İsterseniz, `Microsoft.Spark.Examples` projeye kendi kodunuzu yazabilirsiniz (bu örnekteki 'input_file.json' ile veri çerçevesi oluşturmak istediğiniz verilerin yer verdiği bir json dosyasıdır):
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     Yapı başarılı olduktan sonra, çıktı dizininde üretilen uygun ikilileri görürsünüz.
     Örnek konsol çıkışı:

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a>.NET Core için .NET Çekirdek CLI'yi kullanma

> [!NOTE]
> Şu anda Spark .NET için .NET Core yapılarını otomatikleştirmek üzerinde çalışıyoruz. O zamana kadar, bazı adımları el ile gerçekleştirmedeki sabrınız için teşekkür ederiz.

  1. İşçiyi oluşturun:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Örnek konsol çıkışı:

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. Örnekleri oluşturun:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Örnek konsol çıkışı:

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a>Kıvılcım örnek uygulamaları için .NET'i çalıştırın

Örnekleri oluşturduğunuzda, .NET Framework `spark-submit` veya .NET Core'u hedefleyip hedeflemediğinize bakılmaksızın bunları çalıştırmak yoluyla olacaktır. [Önkoşullar](#prerequisites) bölümünü takip ettiğinizden ve Apache Spark'ı yüklediğinizden emin olun.

  1. İkilinin `DOTNET_WORKER_DIR` `PATH` oluşturulduğu yolu içerecek şekilde ayarlayın (örneğin, *C:\github\dotnet\spark\artlar\bin\Microsoft.Spark.Worker\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artlar\bin\Microsoft.Spark.Worker\Debug\Netcorenet2.1\win10-x64\net publish.NET):* `Microsoft.Spark.Worker`

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Powershell'i açın ve uygulama ikilinizin oluşturulduğu dizine gidin (örneğin, *C:\github\dotnet\spark\artifaks\bin\Microsoft.Spark.CSharp.Examples\Debug\net461* for .NET Framework, *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* for .NET Core için:

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. Uygulamanızı çalıştırmak temel yapıyı izler:

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Çalıştırabileceğiniz bazı örnekler şunlardır:

     - **[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven erişilebilir)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (kavanoz lar sağlandı)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
