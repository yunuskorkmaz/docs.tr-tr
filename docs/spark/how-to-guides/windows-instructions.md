---
title: Windows 'da Apache Spark uygulaması için .NET oluşturma
description: Windows 'da Apache Spark için .NET uygulamanızı nasıl oluşturacağınızı öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: d355380e92235e799d366dca02eaf8450f563f33
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609284"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Windows 'da Apache Spark için .NET uygulamanızı nasıl oluşturacağınızı öğrenin

Bu makalede, Windows 'da Apache Spark uygulamalarınızı .NET için nasıl oluşturabileceğiniz öğretilir.

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki önkoşulların tümüne zaten sahipseniz, [derleme](#build) adımlarına atlayın.

  1. **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** indirme ve yükleme-SDK 'nın yüklenmesi, `dotnet` toolzincirini yolunuza ekler. .NET Core 2,1, 2,2 ve 3,1 desteklenir.
  2. **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (sürüm 16,3 veya üzeri) sürümünü yükler. Topluluk sürümü tamamen ücretsizdir. Yüklemenizi yapılandırırken bu bileşenleri en düşük düzeyde ekleyin:
     * .NET masaüstü geliştirme
       * Tüm gerekli bileşenler
         * .NET Framework 4.6.1 geliştirme araçları
     * .NET Core platformlar arası geliştirme
       * Tüm gerekli bileşenler
  3. **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**' i yükler.
     - İşletim sisteminiz için uygun sürümü seçin. Örneğin, Windows x64 makinesi için *jdk-8u201-windows-x64.exe* .
     - Yükleyiciyi kullanarak yükleme `java` yapın ve komut satırınızdan çalıştırabildiğinizi doğrulayın.
  4. **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)**'yi yükler.
     - [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip)indirin.
     - Yerel bir dizine ayıklayın. Örneğin, * C:\bin\apache-Maven-3.6.0 \* .
     - [Yol ortam değişkeninizin](https://www.java.com/en/download/help/path.xml)Apache Maven 'i ekleyin. Örneğin, *C:\bin\apache-Maven-3.6.0\Bin*.
     - Komut satırınızdan çalıştırabildiğinizi doğrulayın `mvn` .
  5. **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)**' yı yükler.
     - [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) indirin ve bu dosyayı yerel bir klasöre (örneğin, *C:\bin\spark-2.3.2-bin-hadoop2.7 \* ) [7-zip](https://www.7-zip.org/)kullanarak ayıklayın. (Desteklenen Spark sürümleri 2,3.*, 2.4.0, 2.4.1, 2.4.3 ve 2.4.4)
     - Yeni bir [ortam değişkeni](https://www.java.com/en/download/help/path.xml) ekleyin `SPARK_HOME` . Örneğin, * C:\bin\spark-2.3.2-bin-hadoop2.7 \* .

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - [Path ortam değişkeninizin](https://www.java.com/en/download/help/path.xml)Apache Spark ekleyin. Örneğin, *C:\bin\spark-2.3.2-bin-hadoop2.7\bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Komut satırınızdan çalıştırabildiğinizi doğrulayın `spark-shell` .
        Örnek konsol çıkışı:

        ```output
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

  6. **[Winutils](https://github.com/steveloughran/winutils)**'i yükler.
     - `winutils.exe` [Winutils deposundan](https://github.com/steveloughran/winutils)ikili indirin. Spark dağıtımının derlenmiş olduğu Hadoop sürümünü seçmeniz gerekir. Exammple için, Spark 2.3.2 için Hadoop-2.7.1 kullanın.
     - `winutils.exe`İkiliyi istediğiniz dizine kaydedin. Örneğin, *C:\hadoop\bin*.
     - `HADOOP_HOME`winutils.exe (bin olmadan) dizini yansıtacak şekilde ayarlanır. Örneğin, komut satırını kullanarak:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - PATH ortam değişkenini içerecek şekilde ayarlayın `%HADOOP_HOME%\bin` . Örneğin, komut satırını kullanarak:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Bir `dotnet` `java` `mvn` `spark-shell` sonraki bölüme geçmeden önce komut satırınızdan,,,,,,,,,, ' i çalıştırabildiğinizden emin olun. Daha iyi bir yol var mı? [Bir sorun açın](https://github.com/dotnet/spark/issues) ve katkıda bulunmak için ücretsizdir.

> [!NOTE]
> Bir ortam değişkeni güncelleştirilirse, komut satırının yeni bir örneği gerekli olabilir.

## <a name="build"></a>Oluşturma

Bu kılavuzun geri kalanı için, .NET Apache Spark deposunu makinenize Klonladığınız bir işlem olması gerekir. Kopyalanmış depo için herhangi bir konum seçebilirsiniz. Örneğin, * C:\github\dotnet-Spark \* .

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Apache Spark Scala uzantıları katmanı için .NET derleme

Bir .NET uygulaması gönderdiğinizde, Apache Spark için .NET, isteklerinizi nasıl işleyeceğinizi (örneğin, yeni bir Spark oturumu oluşturma isteği, .NET tarafından JVM tarafına veri aktarma isteği vb.) Apache Spark bildiren gerekli mantığa sahiptir. Bu mantık, [.net Spark Scala kaynak kodunda](https://github.com/dotnet/spark/tree/master/src/scala)bulunabilir.

.NET Framework veya .NET Core 'u kullanıp kullanmadığına bakılmaksızın, Apache Spark Scala uzantı katmanı için .NET oluşturmanız gerekir:

```powershell
cd src\scala
mvn clean package
```

Desteklenen Spark sürümleri için oluşturulan JARs ' i görmeniz gerekir:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Spark örnek uygulamaları için .NET oluşturun

Bu bölümde, Apache Spark için .NET [örnek uygulamalarının](https://github.com/dotnet/spark/tree/master/examples) nasıl oluşturulacağı açıklanmaktadır. Bu adımlar, tüm Spark uygulamaları için tüm .NET oluşturma sürecini kavramaya yardımcı olur.

#### <a name="using-visual-studio-for-net-framework"></a>.NET Framework için Visual Studio 'Yu kullanma

  1. `src\csharp\Microsoft.Spark.sln`Visual Studio 'da açın ve `Microsoft.Spark.CSharp.Examples` projeyi klasörün altında oluşturun `examples` (Bu işlem, .net bağlamaları projesini de oluşturur). İsterseniz, projeye kendi kodunuzu yazabilirsiniz `Microsoft.Spark.Examples` (Bu örnekteki ' input_file.json ', veri çerçevesini oluşturmak istediğiniz verileri içeren bir JSON dosyasıdır):
  
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

     Derleme başarılı olduktan sonra çıktı dizininde oluşturulan uygun ikili dosyaları görürsünüz.
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

#### <a name="using-net-core-cli-for-net-core"></a>.NET Core için .NET Core CLI kullanma

> [!NOTE]
> Şu anda spark .NET için .NET Core derlemelerini otomatikleştirmede çalışıyoruz. Bu süre kadar, bazı adımları el ile gerçekleştirmede size teşekkür ederiz.

  1. Çalışanı oluşturun:

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

## <a name="run-the-net-for-spark-sample-applications"></a>Spark örnek uygulamaları için .NET çalıştırın

Örnekleri oluşturduktan sonra, `spark-submit` .NET Framework veya .NET Core 'u hedeflemenize bakılmaksızın bunların çalıştırılması gerekir. [Önkoşul](#prerequisites) bölümünü izlediğinizden ve Apache Spark yüklediğinizden emin olun.

  1. Ya da `DOTNET_WORKER_DIR` `PATH` ortam değişkenini, ikilinin oluşturulduğu yolu içerecek şekilde ayarlayın `Microsoft.Spark.Worker` (örneğin, *C:\GITHUB\DOTNET\SPARK\ARTIFACTS\BIN\MICROSOFT.spark.WORKER\DEBUG\NET461* for .NET Framework, .NET Core için *C:\github\dotnet-spark\artifacts\bin\Microsoft.spark.Worker\Debug\netcoreapp2.1\win10-x64\publish* ):

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. PowerShell 'i açın ve uygulama ikilisinin oluşturulduğu dizine gidin (örneğin, .NET Framework için *C:\github\dotnet\spark\artifacts\bin\Microsoft.spark.CSharp.Examples\Debug\net461* , .NET Core için *C:\github\dotnet-spark\artifacts\bin\Microsoft.spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish* ):

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

     Şunları çalıştırabilmeniz için bazı örnekler aşağıda verilmiştir:

     - **[Microsoft.Spark.Examples.Sql.Batch. Basit](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft. spark. Examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft. spark. Examples. Sql. streaming. StructuredKafkaWordCount (Maven erişilebilir)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft. spark. Examples. Sql. streaming. StructuredKafkaWordCount (jars sağlanmış)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
