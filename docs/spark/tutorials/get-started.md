---
title: Apache Spark için .NET ile başlayın
description: Windows, MacOS ve Ubuntu'da .NET Core'u kullanarak Apache Spark uygulaması için bir .NET'in nasıl çalıştırılabildiğini keşfedin.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187540"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile başlayın

Bu öğretici, Windows, MacOS ve Ubuntu'da .NET Core'u kullanarak Apache Spark için bir .NET uygulamasını nasıl çalıştırabileceğinizi öğretir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> * Apache Spark için ortamınızı .NET'e hazırlayın
> * Apache Spark uygulaması için ilk .NET'inizi yazın
> * Apache Spark uygulaması için basit .NET'inizi oluşturun ve çalıştırın

## <a name="prepare-your-environment"></a>Ortamınızı hazırlama

Uygulamanızı yazmaya başlamadan önce bazı ön koşul bağımlılıkları ayarlamanız gerekir. Komut satırı `dotnet`ortamınızdan `mvn` `spark-shell` , , , `java`çalıştırabiliyorsanız, ortamınız zaten hazırlanmıştır ve bir sonraki bölüme atlayabilirsiniz. Komutların hiçbirini veya tamamını çalıştıramıyorsanız, aşağıdaki adımları yapın.

### <a name="1-install-net"></a>1. Yükleyin .NET

.NET uygulamaları oluşturmaya başlamak için .NET SDK'yı (Yazılım Geliştirme Kiti) indirmeniz ve yüklemeniz gerekir.

[.NET Core SDK'yı](https://dotnet.microsoft.com/download/dotnet-core/3.1)indirin ve kurun. SDK'nın yüklenmesi, araç zincirini `dotnet` PATH'inize ekler.

.NET Core SDK'yı yükledikten sonra, yeni bir komut `dotnet`istemi veya terminal açın ve çalıştırın.

Komut çalışır ve dotnet nasıl kullanılacağı hakkında bilgi yazdırırsa, bir sonraki adıma taşıyabilirsiniz. Bir `'dotnet' is not recognized as an internal or external command` hata alırsanız, komutu çalıştırmadan önce **yeni** bir komut istemi veya terminal açtığınıza emin olun.

### <a name="2-install-java"></a>2. Java Yükle

Windows ve MacOS için [Java 8.1'i](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) veya Ubuntu için [OpenJDK 8'i](https://openjdk.java.net/install/) yükleyin.

İşletim sisteminiz için uygun sürümü seçin. Örneğin, windows x64 makinesi için **jdk-8u201-windows-x64.exe** veya MacOS için **jdk-8u231-macosx-x64.dmg'yi** seçin. Ardından, yüklemeyi `java` doğrulamak için komutu kullanın.

![Java İndir](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. Sıkıştırma yazılımı yükleyin

Apache Spark sıkıştırılmış .tgz dosyası olarak indirilir. Dosyayı ayıklamak için [7-Zip](https://www.7-zip.org/) veya [WinZip](https://www.winzip.com/)gibi bir çıkarma programı kullanın.

### <a name="4-install-apache-spark"></a>4. Apache Spark yükleyin

[Apache Spark'ı indirin ve kurun.](https://spark.apache.org/downloads.html) Sürüm 2.3.* veya 2.4.0, 2.4.1, 2.4.3 veya 2.4.4 (.NET for Apache Spark'ın diğer sürümleriyle uyumlu değildir) arasından seçim yapmanız gerekir.

Aşağıdaki adımlarda kullanılan komutlar, [Apache Spark 2.4.1'i indirdiğinizi ve yüklediğinizi](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz)varsayar. Farklı bir sürüm kullanmak istiyorsanız, **2.4.1'i** uygun sürüm numarasıyla değiştirin. **Ardından,.katran** dosyasını ve Apache Spark dosyalarını ayıklayın.

İç içe **.katran** dosyasını ayıklamak için:

* İndirdiğiniz **kıvılcım-2.4.1-bin-hadoop2.7.tgz** dosyasını bulun.
* Dosyaya sağ tıklayın ve **burada 7-Zip -> Extract**seçin.
* **spark-2.4.1-bin-hadoop2.7.tar** indirdiğiniz **.tgz** dosyasının yanında oluşturulur.

Apache Spark dosyalarını ayıklamak için:

* Sağ tıklayın **spark-2.4.1-bin-hadoop2.7.tar** ve seçin **7-Zip -> Extract dosyaları...**
* **Alana Ekstre'ye** **C:\bin** girin.
* Alana Ekstresinin altındaki onay kutusunun **işaretini** kaldırın.
* **Tamam'ı**seçin.
* Apache Kıvılcım dosyaları C:\bin\spark-2.4.1-bin-hadoop2.7\

![Kıvılcım Yükle](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

**Windows'da**Apache Spark'ı bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

**MacOS** ve **Ubuntu'da**Apache Spark'ı bulmak için kullanılan ortam değişkenlerini ayarlamak için aşağıdaki komutları çalıştırın:

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Her şeyi yükledikten ve ortam değişkenlerinizi ayarladıktan **sonra, yeni** bir komut istemi veya terminal açın ve aşağıdaki komutu çalıştırın:

`%SPARK_HOME%\bin\spark-submit --version`

Komut sürüyor ve sürüm bilgilerini yazdırıyorsa, bir sonraki adıma geçebilirsiniz.

Bir `'spark-submit' is not recognized as an internal or external command` hata alırsanız, **yeni** bir komut istemi açtığınıza emin olun.

### <a name="5-install-net-for-apache-spark"></a>5. Apache Spark için .NET yükle

Apache Spark GitHub için .NET'ten [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) sürümünden indirin. Örneğin bir Windows makinesindeyseniz ve .NET Core'u kullanmayı planlıyorsanız, [Windows x64 netcoreapp3.1 sürümünden yararlanın.](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip)

Microsoft.Spark.Worker ayıklamak için:

* İndirdiğiniz **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** dosyasını bulun.
* Sağ tıklayın ve **7-Zip -> Extract dosyaları seçin...**.
* **Alana Ekstre'ye** **C:\bin** girin.
* Alana Ekstresinin altındaki onay kutusunun **işaretini** kaldırın.
* **Tamam'ı**seçin.

![Yükle .NET Kıvılcım](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. WinUtils'i yükleyin (yalnızca Windows)

.NET Apache Spark için WinUtils Apache Spark yanında yüklü olması gerekir. [Karşıdan yükleme winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Sonra WinUtils'i **C:\bin\spark-2.4.1-bin-hadoop2.7\bin'e**kopyalayın.

> [!NOTE]
> Spark yükleme klasör adının sonunda açıklamalı hadoop'un farklı bir sürümünü kullanıyorsanız, Hadoop sürümünüzle uyumlu [WinUtils sürümünü seçin.](https://github.com/steveloughran/winutils)

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. DOTNET_WORKER_DIR ayarlayın ve bağımlılıkları kontrol edin

Apache Spark için .NET'i bulmak için .NET uygulamaları tarafından kullanılan `DOTNET_WORKER_DIR` Çevre Değişkenini ayarlamak için aşağıdaki komutlardan birini çalıştırın.

Windows'da, yeni bir [ortam değişkeni](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` oluşturun ve Microsoft.Spark.Worker'ı indirip ayıkladığınız `C:\bin\Microsoft.Spark.Worker\`dizine ayarlayın (örneğin, ). **Windows**

**MacOS'ta,** Microsoft.Spark.Worker'ı indirip ayıkladığınız dizine (örneğin `export DOTNET_WORKER_DIR <your_path>` *~/bin/Microsoft.Spark.Worker/ )* kullanarak yeni bir ortam değişkeni oluşturun ve ayarlayın.

**Ubuntu'da,** yeni bir [ortam değişkeni](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` oluşturun ve Microsoft.Spark.Worker'ı indirip ayıkladığınız dizine ayarlayın (örneğin, *~/bin/Microsoft.Spark.Worker).*

Son olarak, bir sonraki bölüme `mvn` `spark-shell` geçmeden önce komut satırınızdan , , , `dotnet` `java`çalıştırabileceğinizi iki kez kontrol edin.

## <a name="write-a-net-for-apache-spark-app"></a>Apache Spark uygulaması için bir .NET yazın

### <a name="1-create-a-console-app"></a>1. Konsol uygulaması oluşturma

Komut istemi veya terminalinizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

Komut `dotnet` sizin için `new` bir `console` tür uygulaması oluşturur. Parametre, `-o` uygulamanızın depolandığı *mySparkApp* adında bir dizin oluşturur ve gerekli dosyalarla doldurulur. Komut, `cd mySparkApp` dizini yeni oluşturduğunuz uygulama dizinine değiştirir.

### <a name="2-install-nuget-package"></a>2. NuGet paketini yükleyin

Bir uygulamada Apache Spark için .NET'i kullanmak için Microsoft.Spark paketini yükleyin. Komut istemiveya terminalinizde aşağıdaki komutu çalıştırın:

`dotnet add package Microsoft.Spark --version 0.8.0`

### <a name="3-code-your-app"></a>3. Uygulamanızı kodlayın

Visual Studio Code veya herhangi bir metin düzenleyicisinde *Program.cs* açın ve kodun tümünün yerine aşağıdakileri girin:

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
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

### <a name="4-create-and-add-a-data-file"></a>4. Veri dosyası oluşturma ve ekleme

Komut isteminizi veya terminalinizi açın ve uygulama klasörünüze gidin.

```bash
cd <your-app-output-directory>
```

Uygulamanız metin satırları içeren bir dosyayı işler. *mySparkApp* dizininde aşağıdaki metni içeren bir *giriş.txt* dosyası oluşturun:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Apache Spark uygulaması için .NET'inizi çalıştırın

1. Uygulamanızı oluşturmak için aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet build
   ```

2. Apache Spark'ta çalışmak üzere başvurunuzu göndermek için aşağıdaki komutu çalıştırın:

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > Bu komut, Apache Spark'ı indirdiğinizi ve kullanabilmek `spark-submit`için PATH ortamı değişkeninize eklediğinizi varsayar. Aksi takdirde, tam yolu kullanmanız gerekir (örneğin, *C:\bin\apache-spark\bin\spark-gönder* veya *~/kıvılcım/bin/spark-gönder).*

3. Uygulamanız çalıştığında, *input.txt* dosyasının sözcük sayısı verileri konsola yazılır.

Tebrikler! Apache Spark uygulaması için bir .NET'i başarıyla yazıp çalıştırdın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Windows ortamınızı Apache Spark için .NET'e hazırlayın
> * Apache Spark uygulaması için ilk .NET'inizi yazın
> * Apache Spark uygulaması için basit .NET'inizi oluşturun ve çalıştırın

Yukarıdaki adımları açıklayan bir video görmek [için, Apache Spark 101 video serisi için .NET](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App)çıkış.

Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.
> [!div class="nextstepaction"]
> [.NET Apache Spark Kaynakları için](../resources/index.md)
