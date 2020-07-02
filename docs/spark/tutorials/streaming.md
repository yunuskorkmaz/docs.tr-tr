---
title: Apache Spark öğreticisi için .NET ile yapılandırılmış akış
description: Bu öğreticide, Spark yapılandırılmış akış için Apache Spark .NET kullanmayı öğreneceksiniz.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: 5420fe081db1704d7af647e8c88826c1bcf614d9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617849"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Öğretici: Apache Spark için .NET ile yapılandırılmış akış

Bu öğreticide, Apache Spark için .NET kullanarak Spark yapılandırılmış akış çağırma öğretilir. Spark yapısal akışı, gerçek zamanlı veri akışlarını işleme Apache Spark. Akış işleme, canlı verileri üretildiğinde analiz anlamına gelir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Apache Spark uygulaması için .NET oluşturma ve çalıştırma
> * Netcat kullanarak bir veri akışı oluşturun
> * Akış verilerini çözümlemek için Kullanıcı tanımlı işlevler ve parlak SQL kullanma

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Ön koşullar

Apache Spark uygulama için ilk .NET ise, temel bilgileri öğrenecek başlangıç [öğreticisiyle](get-started.md) başlayın.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. Komut istemindeki yeni bir konsol uygulaması oluşturmak için aşağıdaki komutları çalıştırın:

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   `dotnet`Komut `new` sizin için türünde bir uygulama oluşturur `console` . `-o`Parametresi, uygulamanızın depolandığı *Mymini Streamingapp* adlı bir dizin oluşturur ve gerekli dosyalarla doldurur. `cd mySparkStreamingApp`Komutu, dizini yeni oluşturduğunuz uygulama dizini olarak değiştirir.

1. .NET uygulamasını bir uygulamada Apache Spark için kullanmak üzere Microsoft. Spark paketini yüklemek için. Konsolunuza aşağıdaki komutu çalıştırın:

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Bir veri akışı oluşturun ve bu akışa bağlanın

Akış işlemeyi test etmenin popüler bir yolu **netcat**kullanmaktır. netcat ( *NC*olarak da bilinir) ağ bağlantılarından okuyup yazmanızı sağlar. Bir Terminal penceresi aracılığıyla netcat ile bir ağ bağlantısı kurarsınız.

### <a name="create-a-data-stream-with-netcat"></a>Netcat ile veri akışı oluşturma

1. [Netcat 'ı indirin](https://sourceforge.net/projects/nc110/files/). Sonra, dosyayı ZIP indirsitesinden ayıklayın ve "PATH" ortam değişkeninizden ayıkladığınız dizini ekleyin.

2. Yeni bir bağlantı başlatmak için yeni bir konsol açın ve 9999 numaralı bağlantı noktasında localhost 'a bağlanan aşağıdaki komutu çalıştırın.

   Windows'da:

   ```console
   nc -vvv -l -p 9999
   ```

   Linux 'ta:

   ```console
   nc -lk 9999
   ```

   Spark programınız, bu komut istemine yazdığınız girişi dinler.

### <a name="create-a-sparksession"></a>Mini oturum oluşturma

1. `using` *Mymini Streamingapp*içindeki *program.cs* dosyasının en üstüne aşağıdaki ek deyimlerini ekleyin:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. `Main`Yeni bir oluşturma yöntemine aşağıdaki kodu ekleyin `SparkSession` . Spark oturumu, veri kümesi ve DataFrame API 'SI ile Spark programlamanın giriş noktasıdır.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   Yukarıda oluşturulan *Spark* nesnesini çağırmak, programınızın tamamında Spark ve dataframe işlevlerine erişmenize olanak tanır.

### <a name="connect-to-a-stream-with-readstream"></a>ReadStream () ile bir akışa bağlanma

`ReadStream()`Yöntemi, `DataStreamReader` ' de akış verilerini okumak için kullanılabilecek bir döndürür `DataFrame` . Spark uygulamanıza akış verilerinin nerede beklendiğini bildirmek için konak ve bağlantı noktası bilgilerini ekleyin.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Kullanıcı tanımlı bir işlevi kaydetme

Verilerinizde hesaplamalar ve analiz yapmak için Spark uygulamalarında Kullanıcı tanımlı UDF 'ler, *Kullanıcı tanımlı işlevler*' i kullanabilirsiniz.

`Main`Adlı BIR UDF 'yi kaydetmek için aşağıdaki kodu yöntemine ekleyin `udfArray` .

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Bu UDF, özgün dizeyi ( *Str*içinde bulunur) içeren bir dizi oluşturmak için netcat terminalinden aldığı her dizeyi işler ve özgün dizenin uzunluğu ile birleştirilmiş özgün dizenin önüne gelir.

Örneğin, Netcat terminalinde *Hello World* girilmesi, şu durumlarda bir dizi üretir:

* dizi \[ 0] = Merhaba Dünya
* dizi \[ 1] = Merhaba Dünya 11

## <a name="use-sparksql"></a>Mini kullanılan SQL kullan

Veri Çerçeverinizdeki depolanan veriler üzerinde çeşitli işlevler gerçekleştirmek için, parlak SQL kullanın. Veri çerçevesinin her satırına bir UDF uygulamak için UDF 'Leri ve parlak SQL 'i birleştirmek yaygındır.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Bu kod parçacığı, Netcat terminalinizden okunan her dizeyi temsil eden veri Çerçevenizle her bir değere *Udfarray* uygular. <xref:Microsoft.Spark.Sql.Functions.Explode%2A>Dizinizin her girdisini kendi satırına yerleştirmek için, Mini SQL yöntemini uygulayın. Son olarak, <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> Yeni DataFrame *arraydf* 'da üretilebilen sütunları yerleştirmek için kullanın.

## <a name="display-your-stream"></a>Akışınızı görüntüleme

<xref:Microsoft.Spark.Sql.DataFrame.WriteStream>Sonuçları konsola yazdırma ve yalnızca en son çıktıyı görüntüleme gibi, çıktlarınızın özelliklerini oluşturmak için kullanın.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Kodunuzu çalıştırın

Spark 'ta yapılandırılmış akış, bir dizi küçük **toplu iş**aracılığıyla verileri işler.  Programınızı çalıştırdığınızda, Netcat bağlantısını oluşturduğunuz komut istemi yazmaya başlayabilmeniz için izin verir. Bu komut istemine veri yazdıktan sonra ENTER tuşuna her bastığınızda, Spark girişi bir toplu iş olarak değerlendirir ve UDF 'yi çalıştırır.

### <a name="use-spark-submit-to-run-your-app"></a>Uygulamanızı çalıştırmak için Spark-Gönder kullanın

Yeni bir netcat oturumu başlattıktan sonra, yeni bir Terminal açın ve `spark-submit` aşağıdaki komuta benzer şekilde komutunu çalıştırın:

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Yukarıdaki komutu, Microsoft Spark jar dosyanızın gerçek yoluyla güncelleştirdiğinizden emin olun. Yukarıdaki komut Ayrıca, Netcat sunucunuzun localhost bağlantı noktası 9999 üzerinde çalıştığını varsayar.

## <a name="get-the-code"></a>Kodu alma

Bu öğretici [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) örneğini kullanır, ancak GitHub 'da üç farklı tam akış işleme örneği vardır:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): herhangi bir kaynaktan akan verilerdeki sözcük sayısı
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): Pencereleme mantığı ile veri üzerinde sözcük sayısı
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): Kafka 'den akan verilerdeki sözcük sayısı

## <a name="next-steps"></a>Sonraki adımlar

.NET Apache Spark uygulamanızı Databricks 'e dağıtmayı öğrenmek için sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı](databricks-deployment.md)
