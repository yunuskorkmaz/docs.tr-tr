---
title: Apache Spark için .NET ile çalışmaya başlama
description: Windows 'da .NET Core kullanarak Apache Spark uygulaması için .NET çalıştırmayı öğrenin.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 19efc8412d834d73069c61e1cc1ccd9e5eb8593b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774371"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile çalışmaya başlama

Bu öğreticide, Windows 'da .NET Core kullanarak Apache Spark bir uygulama için nasıl bir .NET çalıştırılacağı öğretilir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:

> [!div class="checklist"]
>
> * .NET için Windows ortamınızı Apache Spark için hazırlayın
> * **Microsoft. spark. Worker** 'ı indirin
> * Apache Spark uygulama için basit bir .NET oluşturun ve çalıştırın

## <a name="prepare-your-environment"></a>Ortamınızı hazırlama

Başlamadan önce, komut satırınızdan `dotnet`, `java`, `mvn`, `spark-shell` ' ü çalıştıradığınızdan emin olun. Ortamınız zaten hazırlanmışsa bir sonraki bölüme atlayabilirsiniz. Komutlardan herhangi birini veya tümünü çalıştıradıysanız aşağıdaki adımları izleyin.

1. [.NET Core 2.1 x SDK 'sını](https://dotnet.microsoft.com/download/dotnet-core/2.1)indirip yükleyin. SDK yükleme, yolunuza `dotnet` araç zinciri ekler. Yüklemeyi doğrulamak için `dotnet --version` PowerShell komutunu kullanın.

2. En son güncelleştirmelerle [Visual studio 2017](https://www.visualstudio.com/downloads/) veya [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) ' ü yükler. Community, Professional veya Enterprise 'u kullanabilirsiniz. Topluluk sürümü ücretsizdir.

   Yükleme sırasında aşağıdaki iş yüklerini seçin:
      * .NET masaüstü geliştirme
          * Tüm gerekli bileşenler
          * .NET Framework 4.6.1 geliştirme araçları
      * .NET Core platformlar arası geliştirme
          * Tüm gerekli bileşenler

3. [Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)' i yükler.

    * İşletim sisteminiz için uygun sürümü seçin. Örneğin, bir Windows x64 makinesi için **JDK-8u201-Windows-x64. exe** ' yi seçin.
    * Yüklemeyi doğrulamak için `java -version` PowerShell komutunu kullanın.

4. [Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)'yi yükler.
    * [Apache Maven 3.6.2](http://mirror.metrocast.net/apache/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.zip)indirin.
    * Yerel bir dizine ayıklayın. Örneğin, `c:\bin\apache-maven-3.6.2\`.
    * [Yol ortam değişkeninizin](https://www.java.com/en/download/help/path.xml)Apache Maven 'i ekleyin. @No__t_0 çıkardıysanız, yolunuza `c:\bin\apache-maven-3.6.2\bin` eklersiniz.
    * Yüklemeyi doğrulamak için `mvn -version` PowerShell komutunu kullanın.

5. [Apache Spark 2.3 +](https://spark.apache.org/downloads.html)' yı yükler. Apache Spark 2,4 + desteklenmez.
    * [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) indirin ve [7-zip](https://www.7-zip.org/) veya [WinZip](https://www.winzip.com/)gibi bir araç kullanarak yerel bir klasöre ayıklayın. Örneğin, `c:\bin\spark-2.3.2-bin-hadoop2.7\` ' a ayıklayabilirsiniz.
    * [Path ortam değişkeninizin](https://www.java.com/en/download/help/path.xml)Apache Spark ekleyin. @No__t_0 çıkardıysanız, yolunuza `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` eklersiniz.
    * @No__t_1 adlı [Yeni bir ortam değişkeni](https://www.java.com/en/download/help/path.xml) ekleyin. @No__t_0 çıkardıysanız, **değişken değeri**için `C:\bin\spark-2.3.2-bin-hadoop2.7\` kullanın.
    * Komut satırınızdan `spark-shell` çalıştırabildiğinizi doğrulayın.

6. [Winutils](https://github.com/steveloughran/winutils)'i ayarlayın.
    * Winutils **. exe** Ikili dosyasını [winutils deposundan](https://github.com/steveloughran/winutils)indirin. Spark dağıtımının derlenmiş olduğu Hadoop sürümünü seçin. Örneğin, **Spark 2.3.2**için **Hadoop-2.7.1** kullanırsınız. Hadoop sürümü, Spark install klasörünüzün adının sonunda açıklanmalıdır.
    * **Winutils. exe** ikilisini istediğiniz bir dizine kaydedin. Örneğin, `c:\hadoop\bin`.
    * @No__t_0, `bin` olmadan **winutils. exe** ile dizini yansıtacak şekilde ayarlayın. Örneğin, `c:\hadoop`.
    * PATH ortam değişkenini `%HADOOP_HOME%\bin` içerecek şekilde ayarlayın.

Bir sonraki bölüme geçmeden önce komut satırınızdan `dotnet`, `java`, `mvn`, `spark-shell` ' ü çalıştırıp çalıştırabileceğinizi iki kez denetleyin.

## <a name="download-the-microsoftsparkworker-release"></a>Microsoft. spark. Worker sürümünü indirin

1. [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) sürümünü, Apache Spark GitHub yayınları sayfasından yerel makinenize indirin. Örneğin, `c:\bin\Microsoft.Spark.Worker\` yoluna indirebilirsiniz.

2. @No__t_1 adlı [Yeni bir ortam değişkeni](https://www.java.com/en/download/help/path.xml) oluşturun ve bunu **Microsoft. spark. Worker**' i indirdiğiniz ve ayıkladığınız dizine ayarlayın. Örneğin, `c:\bin\Microsoft.Spark.Worker`.

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Apache Spark GitHub deposunun .NET kopyasını kopyalama

Apache Spark deposunu makinenize kopyalamak için aşağıdaki [GitBash](https://gitforwindows.org/) komutunu kullanın.

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Apache Spark uygulaması için .NET yazma

1. **Visual Studio 'yu** açın ve **Dosya > Yeni Proje > konsol uygulaması (.NET Core) oluştur**' a gidin. Uygulamayı **Merhaba Spark**olarak adlandırın.

2. [Microsoft. Spark NuGet paketini](https://www.nuget.org/profiles/spark)yükler. NuGet paketlerini yükleme hakkında daha fazla bilgi için bkz. [NuGet paketini yüklemek Için farklı yollar](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).

3. **Çözüm Gezgini**' de, **program.cs** açın ve aşağıdaki C# kodu yazın:

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. Çözümü oluşturun.

## <a name="run-your-net-for-apache-spark-app"></a>Apache Spark uygulamanızı .NET için çalıştırın

1. **PowerShell** 'i açın ve dizini uygulamanızın depolandığı klasöre değiştirin.

   ```powershell
   cd <your-app-output-directory>
   ```

2. Şu içerikle **kişiler. JSON** adlı bir dosya oluşturun:

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. Uygulamanızı çalıştırmak için aşağıdaki PowerShell komutunu kullanın:

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

Mühendisi! Apache Spark uygulaması için bir .NET başarıyla yazıldı ve çalıştırdınız.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, nasıl yapılacağını öğrendiniz:
> [!div class="checklist"]
>
> * .NET için Windows ortamınızı Apache Spark için hazırlayın
> * **Microsoft. spark. Worker** 'ı indirin
> * Apache Spark uygulama için basit bir .NET oluşturun ve çalıştırın

Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.
> [!div class="nextstepaction"]
> [Apache Spark kaynakları için .NET](../resources/index.md)
