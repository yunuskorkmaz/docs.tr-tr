---
title: Apache Spark için .NET ile çalışmaya başlama
description: Windows 'da .NET Core kullanarak Apache Spark uygulaması için .NET çalıştırmayı öğrenin.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 679ee7660e96504768a781e1e384acab80362736
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743208"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile çalışmaya başlama

Bu öğreticide, Windows 'da .NET Core kullanarak Apache Spark bir uygulama için nasıl bir .NET çalıştırılacağı öğretilir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:

> [!div class="checklist"]
>
> * .NET için Windows ortamınızı Apache Spark için hazırlayın
> * İlk .NET Apache Spark uygulamanızı yazma
> * Apache Spark uygulamanızı basit .NET için derleyin ve çalıştırın

## <a name="prepare-your-environment"></a>Ortamınızı hazırlama

Uygulamanızı yazmaya başlamadan önce bazı önkoşul bağımlılıklarını ayarlamanız gerekir. Komut satırı ortamınızdan `dotnet`, `java`, `mvn``spark-shell` çalıştırabiliyorsanız, ortamınız zaten hazırlanmışsa ve sonraki bölüme atlayabilirsiniz. Komutlardan herhangi birini veya tümünü çalıştırabiliyorsanız, aşağıdaki adımları uygulayın.

### <a name="1-install-net"></a>1. .NET 'i yükler

.NET uygulamaları oluşturmaya başlamak için .NET SDK 'sını (yazılım geliştirme seti) indirmeniz ve yüklemeniz gerekir.

[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0)indirin ve yükleyin. SDK yükleme, yolunuza `dotnet` toolzincirini ekler.

.NET Core SDK yükledikten sonra, yeni bir komut istemi açın ve `dotnet`çalıştırın.

Komut çalışır ve DotNet kullanımı hakkında bilgi içeriyorsa, bir sonraki adıma geçebilir. `'dotnet' is not recognized as an internal or external command` hatası alırsanız, komutu çalıştırmadan önce **Yeni** bir komut istemi açtığınızdan emin olun.

### <a name="2-install-java"></a>2. Java 'Yı Install

[Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)' i yükler.

İşletim sisteminiz için uygun sürümü seçin. Örneğin, bir Windows x64 makinesi için **JDK-8u201-Windows-x64. exe** ' yi seçin. Ardından, yüklemeyi doğrulamak için `java` komutunu kullanın.

![Java Indirme](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a>3.7-zip ' i yükler

Apache Spark, sıkıştırılmış. tgz dosyası olarak indirilir. Dosyayı ayıklamak için 7-zip gibi bir ayıklama programı kullanın.

* [7 ZIP indiriyi](https://www.7-zip.org/)ziyaret edin.
* Sayfadaki ilk tabloda, işletim sisteminize bağlı olarak 32 bit x86 veya 64 bit x64 indirmeyi seçin.
* Yükleme tamamlandığında, yükleyiciyi çalıştırın.

![7Zip Indir](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a>4. Apache Spark yüklemesi

[Apache Spark indirin ve yükleyin](https://spark.apache.org/downloads.html). 2,3. * veya 2.4.0, 2.4.1, 2.4.3 veya 2.4.4 (.NET Apache Spark Apache Spark diğer sürümleriyle uyumlu değildir) arasından seçim yapmanız gerekir.

Aşağıdaki adımlarda kullanılan komutlar, [2.4.1 Apache Spark indirdiğiniz ve yüklediğiniz](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)varsayılır. Farklı bir sürüm kullanmak istiyorsanız, **2.4.1** değerini uygun sürüm numarasıyla değiştirin. Ardından, **. tar** dosyasını ve Apache Spark dosyalarını ayıklayın.

İç içe geçmiş **. tar** dosyasını ayıklamak için:

* İndirdiğiniz **Spark-2.4.1-bin-Hadoop 2.7. tgz** dosyasını bulun.
* Dosyaya sağ tıklayın ve **7-ZIP-> buradan Ayıkla**' yı seçin.
* **Spark-2.4.1-bin-Hadoop 2.7. tar** , indirdiğiniz **. tgz** dosyası ile birlikte oluşturulur.

Apache Spark dosyalarını ayıklamak için:

* **Spark-2.4.1-bin-Hadoop 2.7. tar** öğesine sağ tıklayın ve **7-ZIP-> dosyaları ayıkla ' yı seçin...**
* **Ayıkla** alanına **c:\Bin** yazın.
* **Ayıkla** alanının altındaki onay kutusunun işaretini kaldırın.
* **Tamam**’ı seçin.
* Apache Spark dosyaları C:\bin\spark-2.4.1-bin-hadoop2.7\ ' ye ayıklanır

![Spark 'ı yükler](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Apache Spark bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Her şeyi yükledikten ve ortam değişkenlerinizi ayarladıktan sonra, **Yeni** bir komut istemi açın ve aşağıdaki komutu çalıştırın:

`%SPARK_HOME%\bin\spark-submit --version`

Komut çalışır ve sürüm bilgilerini yazdırıyorsa, sonraki adıma geçebilirsiniz.

`'spark-submit' is not recognized as an internal or external command` bir hata alırsanız, **Yeni** bir komut istemi açtığınızdan emin olun.

### <a name="5-install-net-for-apache-spark"></a>5. Apache Spark için .NET 'i yükler

Apache Spark GitHub için .NET 'ten [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) sürümünü indirin. Örneğin, bir Windows makinesi kullanıyorsanız ve .NET Core 'u kullanmayı planlıyorsanız, [Windows x64 netcoreapp 2.1 sürümünü indirin](https://github.com/dotnet/spark/releases/download/v0.6.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).

Microsoft. spark. Worker öğesini ayıklamak için:

* İndirdiğiniz **Microsoft. spark. Worker. netcoreapp 2.1. Win-x64-0.6.0. zip** dosyasını bulun.
* Sağ tıklayıp **7 ZIP-> dosyaları ayıkla ' yı seçin...**
* **Ayıkla** alanına **c:\Bin** yazın.
* **Ayıkla** alanının altındaki onay kutusunun işaretini kaldırın.
* **Tamam**’ı seçin.

![.NET Spark 'ı yükler](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a>6. WinUtils 'i yükler

Apache Spark için .NET, Apache Spark birlikte WinUtils 'in yüklenmesini gerektirir. [Winutils. exe dosyasını indirin](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Ardından, WinUtils 'ı **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**'e kopyalayın.

> [!NOTE]
> Spark install klasörünüzün adının sonunda açıklanan farklı bir Hadoop sürümü kullanıyorsanız, Hadoop sürümünüzle uyumlu olan [WinUtils sürümünü seçin](https://github.com/steveloughran/winutils) .

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. DOTNET_WORKER_DIR ayarla ve bağımlılıkları denetle

.NET uygulamaları tarafından Apache Spark .NET konumunu bulmak üzere kullanılan `DOTNET_WORKER_DIR` ortam değişkenini ayarlamak için aşağıdaki komutu çalıştırın:

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

Son olarak, bir sonraki bölüme geçmeden önce komut satırınızdan `dotnet`, `java`, `mvn``spark-shell` çalıştırıp çalıştırabileceğinizi iki kez kontrol edin.

## <a name="write-a-net-for-apache-spark-app"></a>Apache Spark uygulaması için .NET yazma

### <a name="1-create-a-console-app"></a>1. konsol uygulaması oluşturma

Komut istemindeki yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

`dotnet` komutu sizin için `console` türünde bir `new` uygulaması oluşturur. `-o` parametresi, uygulamanızın depolandığı *mySparkApp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur. `cd mySparkApp` komutu, dizini yeni oluşturduğunuz uygulama diziniyle değiştirir.

### <a name="2-install-nuget-package"></a>2. NuGet paketini yükler

.NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için. Komut isteminde aşağıdaki komutu çalıştırın:

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a>3. uygulamanızı kodlayın

Visual Studio Code veya herhangi bir metin düzenleyicisinde *program.cs* açın ve kodun tümünü aşağıdaki kodla değiştirin:

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-add-data-file"></a>4. veri dosyası Ekle

Uygulamanız metin satırları içeren bir dosyayı işler. *MySparkApp* dizininizde aşağıdaki metni içeren bir *input. txt* dosyası oluşturun:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Apache Spark uygulamanızı .NET için çalıştırın

1. Uygulamanızı derlemek için aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet build
   ```

2. Apache Spark üzerinde çalışacak uygulamanızı göndermek için aşağıdaki komutu çalıştırın:

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. Uygulamanız çalıştırıldığında, *Input. txt* dosyasının sözcük sayısı verisi konsola yazılır.

Tebrikler! Apache Spark uygulaması için bir .NET başarıyla yazıldı ve çalıştırdınız.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * .NET için Windows ortamınızı Apache Spark için hazırlayın
> * İlk .NET Apache Spark uygulamanızı yazma
> * Apache Spark uygulamanızı basit .NET için derleyin ve çalıştırın

Yukarıdaki adımları açıklayan bir videoyu görmek için, [Apache Spark 101 video serisi için .net](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)'i kullanıma alın.

Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.
> [!div class="nextstepaction"]
> [Apache Spark kaynakları için .NET](../resources/index.md)
