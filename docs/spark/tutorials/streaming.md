---
title: Apache Spark öğretici için .NET ile Yapılandırılmış Akış
description: Bu eğitimde, Spark Structured Streaming için Apache Spark için .NET'i nasıl kullanacağınızı öğreneceksiniz.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186507"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile Yapılandırılmış Akış

Bu öğretici, Apache Spark için .NET kullanarak Spark Yapılandırılmış Akışı nasıl çağıracağınız öğretilir. Spark Structured Streaming, Apache Spark'ın gerçek zamanlı veri akışlarını işlemek için verdiği destektir. Akış işleme, canlı verilerin üretilirken analiz edilmesi anlamına gelir.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:

> [!div class="checklist"]
>
> * Apache Spark uygulaması için bir .NET oluşturma ve çalıştırma
> * Veri akışı oluşturmak için netcat'i kullanma
> * Akış verilerini analiz etmek için kullanıcı tanımlı işlevleri ve SparkSQL'i kullanma

## <a name="prerequisites"></a>Önkoşullar

Apache Spark uygulaması için ilk .NET uygulamanızsa, temel bilgileri tanımak için [Başlangıç eğitimiyle](get-started.md) başlayın.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Komut isteminizde, yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   Komut `dotnet` sizin için `new` bir `console` tür uygulaması oluşturur. Parametre, `-o` uygulamanızın depolandığı *mySparkStreamingApp* adında bir dizin oluşturur ve gerekli dosyalarla doldurulur. Komut, `cd mySparkStreamingApp` dizini yeni oluşturduğunuz uygulama dizinine değiştirir.

1. Bir uygulamada Apache Spark için .NET'i kullanmak için Microsoft.Spark paketini yükleyin. Konsolunuzda aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Veri akışı oluşturma ve bağlanma

Akış işlemetest etmek için bir popüler yolu **netcat**geçer. netcat *(nc*olarak da bilinir) ağ bağlantılarından okumanızı ve yazmanızı sağlar. Terminal penceresinden netcat ile ağ bağlantısı kurarsınız.

### <a name="create-a-data-stream-with-netcat"></a>netcat ile veri akışı oluşturma

1. [Netcat'i indirin.](https://sourceforge.net/projects/nc110/files/) Ardından, dosyayı zip indirmeden ayıklayın ve çıkardığınız dizin "PATH" ortam değişkenine ekleyip.

2. Yeni bir bağlantı başlatmak için yeni bir konsol açın ve 9999 portundaki localhost'a bağlanan aşağıdaki komutu çalıştırın.

   Windows'da:

   ```console
   nc -vvv -l -p 9999
   ```

   Linux üzerinde:

   ```console
   nc -lk 9999
   ```

   Spark programınız bu komut istemine yazdığınız girişi dinler.

### <a name="create-a-sparksession"></a>Bir SparkSession oluşturma

1. `using` *mySparkStreamingApp'taki* *Program.cs* dosyasının üst bölümüne aşağıdaki ek ifadeleri ekleyin:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. `Main` Yeni `SparkSession`bir . Kıvılcım Oturumu, Dataset ve DataFrame API ile Spark programlamanın giriş noktasıdır.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Yukarıda oluşturulan *kıvılcım* nesnesini aramak, programınız boyunca Spark ve DataFrame işlevlerine erişmenizi sağlar.

### <a name="connect-to-a-stream-with-readstream"></a>ReadStream ile bir akışa bağlanın()

Yöntem, `ReadStream()` akış `DataStreamReader` verilerini bir ' de okumak `DataFrame`için kullanılabilecek bir yöntem döndürür. Spark uygulamanıza akış verilerini nerede beklediğini söylemek için ana bilgisayar ve bağlantı noktası bilgilerini ekleyin.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Kullanıcı tanımlı bir işlev kaydetme

Verilerinizde hesaplamalar ve analizler gerçekleştirmek için Spark uygulamalarında *kullanıcı tanımlı işlevler*olan UDF'leri kullanabilirsiniz.

Bir UDF'yi `Main` `udfArray`kaydetmek için yönteminize aşağıdaki kodu ekleyin.

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Bu UDF, netcat terminalinden aldığı her dizeyi, özgün dizeyi *(str'de*bulunan) içeren bir dizi oluşturmak için işler ve ardından özgün dize uzunluğuyla birlikte eklenen özgün dizeyi işler.

Örneğin, netcat terminalinde *Hello dünyasına* girmek aşağıdakileri yaptığı bir dizi üretir:

* dizi\[0] = Merhaba dünya
* dizi\[1] = Merhaba dünya 11

## <a name="use-sparksql"></a>SparkSQL kullanın

DataFrame'inizde depolanan verilerüzerinde çeşitli işlevleri gerçekleştirmek için SparkSQL'i kullanın. Bir DataFrame'in her satırına UDF uygulamak için UDF'leri ve SparkSQL'i birleştirmek yaygındır.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Bu kod snippet, netcat terminalinizden okunan her dizeyi temsil eden DataFrame'inizdeki her değere *udfArray* uygular. Dizinizin her <xref:Microsoft.Spark.Sql.Functions.Explode%2A> girişini kendi satırına koymak için SparkSQL yöntemini uygulayın. Son olarak, yeni DataFrame <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> *arrayDF'de* ürettiğiniz sütunları yerleştirmek için kullanın.

## <a name="display-your-stream"></a>Akışınızı görüntüleme

Sonuçları <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> konsola yazdırmak ve yalnızca en son çıktıyı görüntülemek gibi çıktınızın özelliklerini oluşturmak için kullanın.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Kodunuzu çalıştırın

Spark'taki yapılandırılmış akış, verileri bir dizi küçük **toplu işlem**le işler.  Programınızı çalıştırdığınızda, netcat bağlantısını kurduğunuz komut istemi yazmaya başlamanızı sağlar. Bu komut istemine veri yazdıktan sonra Enter tuşuna her bastığınızda, Spark girişinizi bir toplu iş olarak kabul eder ve UDF'yi çalıştırır.

### <a name="use-spark-submit-to-run-your-app"></a>Uygulamanızı çalıştırmak için kıvılcım gönder'i kullanma

Yeni bir netcat oturumuna başladıktan sonra, `spark-submit` yeni bir terminal açın ve aşağıdaki komuta benzer şekilde komutunuzu çalıştırın:

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Yukarıdaki komutu Microsoft Spark jar dosyanıza giden gerçek yol ile güncelleştirdiğinden emin olun. Yukarıdaki komut, netcat sunucunuzun localhost port 9999'da çalıştığını da varsayar.

## <a name="get-the-code"></a>Kodu alma

Bu öğretici [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) örneğini kullanır, ancak GitHub'da üç tam akış işleme örneği daha vardır:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): herhangi bir kaynaktan aktarılan verilere ilişkin sözcük sayısı
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): pencereleme mantığı ile verilere kelime sayısı
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): Kafka'dan aktarılan verilere ilişkin kelime sayısı

## <a name="next-steps"></a>Sonraki adımlar

Apache Spark uygulamanızı Databricks'e nasıl dağıtacağınız hakkında bilgi edinmek için bir sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici: Databricks'e Apache Spark uygulaması için bir .NET dağıtma](databricks-deployment.md)
