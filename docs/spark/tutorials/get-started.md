---
title: Apache Spark için .NET ile çalışmaya başlama
description: Windows, macOS ve Ubuntu 'da .NET Core kullanarak Apache Spark uygulaması için .NET çalıştırmayı öğrenin.
ms.date: 09/17/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 7afb35c9d02db1d1ee2bf04d565f79588b00695e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866042"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile çalışmaya başlama

Bu öğreticide, Windows, macOS ve Ubuntu 'da .NET Core kullanarak Apache Spark uygulaması için .NET nasıl çalıştırabileceğiniz öğretilir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Apache Spark için ortamınızı .NET için hazırlama
> * İlk .NET Apache Spark uygulamanızı yazma
> * Apache Spark için .NET uygulamanızı derleyin ve çalıştırın

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prepare-your-environment"></a>Ortamınızı hazırlama

Uygulamanızı yazmaya başlamadan önce bazı önkoşul bağımlılıklarını ayarlamanız gerekir. `dotnet` `java` `spark-shell` Komut satırı ortamınızdan çalıştırırsanız, ortamınız zaten hazırlanmışsa bir sonraki bölüme atlayabilirsiniz. Komutlardan herhangi birini veya tümünü çalıştırabiliyorsanız, aşağıdaki adımları uygulayın.

### <a name="1-install-net"></a>1. .NET 'i yükler

.NET uygulamaları oluşturmaya başlamak için .NET SDK 'sını (yazılım geliştirme seti) indirmeniz ve yüklemeniz gerekir.

[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1)indirin ve yükleyin. SDK 'Yı yüklemek `dotnet` yolunuza toolzincirini ekler.

.NET Core SDK yükledikten sonra, yeni bir komut istemi veya Terminal açın ve çalıştırın `dotnet` .

Komut çalışır ve DotNet kullanımı hakkında bilgi içeriyorsa, bir sonraki adıma geçebilir. Bir `'dotnet' is not recognized as an internal or external command` hata alırsanız, komutu çalıştırmadan önce **Yeni** bir komut istemi veya Terminal açtığınızdan emin olun.

### <a name="2-install-java"></a>2. Java 'Yı Install

Windows ve macOS için [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) veya Ubuntu Için [OpenJDK 8](https://openjdk.java.net/install/) ' i yükler.

İşletim sisteminiz için uygun sürümü seçin. Örneğin, bir Windows x64 makinesi için **jdk-8u201-windows-x64.exe** (aşağıda gösterildiği gibi) veya MacOS için **JDK-8u231-macosx-x64. dmg** ' yi seçin. Sonra, `java` yüklemeyi doğrulamak için komutunu kullanın.

![Java Indirme](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. sıkıştırma yazılımını yükler

Apache Spark, sıkıştırılmış. tgz dosyası olarak indirilir. Dosyayı ayıklamak için [7-zip](https://www.7-zip.org/) veya [WinZip](https://www.winzip.com/)gibi bir ayıklama programı kullanın.

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

Apache Spark bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın. Windows 'ta, komut istemi 'ni yönetici modunda çalıştırdığınızdan emin olun.

#### <a name="windows"></a>[Windows](#tab/windows)

```console
setx /M HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx /M PATH "%PATH%;%HADOOP_HOME%;%SPARK_HOME%\bin"
```

#### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

---

Her şeyi yükledikten ve ortam değişkenlerinizi ayarladıktan sonra, **Yeni** bir komut istemi veya Terminal açın ve şu komutu çalıştırın:

```text
spark-submit --version
```

Komut çalışır ve sürüm bilgilerini yazdırıyorsa, sonraki adıma geçebilirsiniz.

Bir `'spark-submit' is not recognized as an internal or external command` hata alırsanız, **Yeni** bir komut istemi açtığınızdan emin olun.

### <a name="5-install-net-for-apache-spark"></a>5. Apache Spark için .NET 'i yükler

Apache Spark GitHub için .NET 'ten [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) sürümünü indirin. Örneğin, bir Windows makinesi kullanıyorsanız ve .NET Core 'u kullanmayı planlıyorsanız, [Windows x64 netcoreapp 3.1 sürümünü indirin](https://github.com/dotnet/spark/releases).

Microsoft. spark. Worker öğesini ayıklamak için:

* İndirdiğiniz **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** dosyasını bulun.
* Sağ tıklayıp **7-ZIP-> dosyaları ayıkla ' yı seçin...**
* **Ayıkla** alanına **c:\Bin** yazın.
* **Ayıkla** alanının altındaki onay kutusunun işaretini kaldırın.
* **Tamam**’ı seçin.

![.NET Spark 'ı yükler](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. WinUtils 'i (yalnızca Windows) yükler

Apache Spark için .NET, Apache Spark birlikte WinUtils 'in yüklenmesini gerektirir. [winutils.exeindirin ](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Ardından, WinUtils 'ı **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**'e kopyalayın.

> [!NOTE]
> Spark install klasörünüzün adının sonunda açıklanan farklı bir Hadoop sürümü kullanıyorsanız, Hadoop sürümünüzle uyumlu olan [WinUtils sürümünü seçin](https://github.com/steveloughran/winutils) .

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. DOTNET_WORKER_DIR ayarla ve bağımlılıkları denetle

`DOTNET_WORKER_DIR`.NET uygulamaları tarafından Apache Spark .net bulmak için kullanılan ortam değişkenini ayarlamak için aşağıdaki komutlardan birini çalıştırın. `<PATH-DOTNET_WORKER_DIR>`' İ indirdiğiniz ve ayıkladığınız dizinle değiştirdiğinizden emin olun `Microsoft.Spark.Worker` . Windows 'ta, komut istemi 'ni yönetici modunda çalıştırdığınızdan emin olun.

#### <a name="windows"></a>[Windows](#tab/windows)

```console
setx /M DOTNET_WORKER_DIR <PATH-DOTNET-WORKER-DIR>
```

#### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
export DOTNET_WORKER_DIR=<PATH-DOTNET-WORKER-DIR>
```

---

Son olarak, bir `dotnet` `java` `spark-shell` sonraki bölüme geçmeden önce komut satırınızdan, ve ' yi çalıştırıp çalıştırabileceğinizi iki kez kontrol edin.

## <a name="write-a-net-for-apache-spark-app"></a>Apache Spark uygulaması için .NET yazma

### <a name="1-create-a-console-app"></a>1. konsol uygulaması oluşturma

Komut isteminizde veya terminalinizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:

```dotnetcli
dotnet new console -o MySparkApp
cd MySparkApp
```

`dotnet`Komut `new` sizin için türünde bir uygulama oluşturur `console` . `-o`Parametresi, uygulamanızın depolandığı *MySparkApp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur. `cd MySparkApp`Komut, dizini oluşturduğunuz uygulama dizini olarak değiştirir.

### <a name="2-install-nuget-package"></a>2. NuGet paketini yükler

.NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için. Komut isteminizde veya terminalinizde aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet add package Microsoft.Spark
```

> [!NOTE]
> Bu öğretici, `Microsoft.Spark` Aksi belirtilmediği takdirde NuGet paketinin en son sürümünü kullanır.

### <a name="3-write-your-app"></a>3. uygulamanızı yazma

Visual Studio Code veya herhangi bir metin düzenleyicisinde *program.cs* açın ve kodun tümünü aşağıdaki kodla değiştirin:

```csharp
using Microsoft.Spark.Sql;
using static Microsoft.Spark.Sql.Functions;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create Spark session
            SparkSession spark =
                SparkSession
                    .Builder()
                    .AppName("word_count_sample")
                    .GetOrCreate();

            // Create initial DataFrame
            string filePath = args[0];
            DataFrame dataFrame = spark.Read().Text(filePath);

            //Count words
            DataFrame words =
                dataFrame
                    .Select(Split(Col("value")," ").Alias("words"))
                    .Select(Explode(Col("words")).Alias("word"))
                    .GroupBy("word")
                    .Count()
                    .OrderBy(Col("count").Desc());

            // Display results
            words.Show();

            // Stop Spark session
            spark.Stop();
        }
    }
}
```

[Mini oturum](xref:Microsoft.Spark.Sql.SparkSession) , uygulamanızın bağlamını ve bilgilerini yöneten Apache Spark uygulamaların giriş noktası. [Metin](xref:Microsoft.Spark.Sql.DataFrameReader.Text%2A) yöntemini kullanarak, tarafından belirtilen dosyadaki metin verileri `filePath` bir veri [çerçevesine](xref:Microsoft.Spark.Sql.DataFrame)okunurdur. DataFrame, verileri bir adlandırılmış sütunlar kümesiyle düzenlemenin bir yoludur. Daha sonra, dosyadaki cümleleri ayırmak için bir dizi dönüştürme uygulanır, sözcüklerin her birini gruplayın, onları Sayın ve azalan sırada sıralayın. Bu işlemlerin sonucu, başka bir veri çerçevesinde saklanır. Bu noktada, Apache Spark geç için .NET verileri değerlendirirken hiçbir işlem gerçekleşmediğini unutmayın. Bu işlem [,](xref:Microsoft.Spark.Sql.DataFrame.Show%2A) `words` dönüştürülmüş veri çerçevesinin içeriğini, yukarıdaki satırlarda tanımlanan işlemleri konsola görüntülemek için olarak çağırılır. Spark oturumuna artık gerek kalmadığında, oturumunuzu durdurmak için [stop](xref:Microsoft.Spark.Sql.SparkSession.Stop%2A) metodunu kullanın.

### <a name="4-create-data-file"></a>4. veri dosyası oluştur

Uygulamanız metin satırları içeren bir dosyayı işler. *MySparkApp* dizininizde aşağıdaki metni içeren *input.txt* dosyası adlı bir dosya oluşturun:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

Değişiklikleri kaydedin ve dosyayı kapatın.

## <a name="run-your-net-for-apache-spark-app"></a>Apache Spark uygulamanızı .NET için çalıştırın

Uygulamanızı derlemek için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet build
```

Yapı çıkış dizininize gidin ve `spark-submit` uygulamanızı Apache Spark çalışacak şekilde göndermek için komutunu kullanın. `<version>`' In .net çalışanınız sürümü ile ve `<path-of-input.txt>` *input.txt* dosyanın yolu ile değiştirdiğinizden emin olun.

### <a name="windows"></a>[Windows](#tab/windows)

```console
spark-submit ^
--class org.apache.spark.deploy.dotnet.DotnetRunner ^
--master local ^
microsoft-spark-2.4.x-<version>.jar ^
dotnet MySparkApp.dll <path-of-input.txt>
```

### <a name="maclinux"></a>[Mac/Linux](#tab/linux)

```bash
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master local \
microsoft-spark-2.4.x-<version>.jar \
dotnet MySparkApp.dll <path-of-input.txt>
```

---

> [!NOTE]
> Bu komut Apache Spark indirdiğinizi ve bunu kullanabilmeniz için PATH ortam değişkenine eklediğinizi varsayar `spark-submit` . Aksi takdirde, tam yolu kullanmanız gerekir (örneğin, *C:\bin\apache-spark\bin\spark-Submit* veya *~/Spark/bin/Spark-Submit*).

Uygulamanız çalıştırıldığında, *input.txt* dosyanın sözcük sayısı verisi konsola yazılır.

```console
+------+-----+
|  word|count|
+------+-----+
|  .NET|    3|
|Apache|    2|
|   app|    2|
|  This|    2|
| Spark|    2|
| World|    1|
|counts|    1|
|   for|    1|
| words|    1|
|  with|    1|
| Hello|    1|
|  uses|    1|
+------+-----+
```

Tebrikler! Apache Spark uygulaması için bir .NET başarıyla yazıldı ve çalıştırdınız.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Apache Spark için ortamınızı .NET için hazırlama
> * İlk .NET Apache Spark uygulamanızı yazma
> * Apache Spark için .NET uygulamanızı derleyin ve çalıştırın

Yukarıdaki adımları açıklayan bir videoyu görmek için, [Apache Spark 101 video serisine yönelik .net](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)' i inceleyin.

Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.
> [!div class="nextstepaction"]
> [Apache Spark kaynakları için .NET](../resources/index.md)
