---
title: Apache Spark için .NET Event Hubs Azure 'a bağlama
description: Apache Spark örneği için yerel .NET 'ten Azure Event hub 'a nasıl bağlanacağınızı öğrenin.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 3956a8152feb743f205f29334f0d42b3165cb27b
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877952"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a>Apache Spark için .NET Event Hubs Azure 'a bağlama

Bu makalede, Apache Kafka akışlarını okumak ve yazmak için .net Event Hubs [Apache Spark](https://github.com/dotnet/spark) uygulamanızı Azure 'a nasıl bağlayacağınızı öğreneceksiniz.

## <a name="prerequisites"></a>Ön koşullar

1. Bir olay hub 'ı ile bir Event Hubs ad alanı hazırlayın, bunun nasıl yapılacağını gösteren adım adım kılavuz için [Bu belgeye](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) bakın. Olay Hub 'ı ad alanını oluştururken standart fiyatlandırma katmanını seçtiğinizden emin olun.

## <a name="what-is-azure-event-hubs"></a>Azure Event Hubs nedir?

[Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) , büyük bir veri akışı platformu ve olay alma hizmetidir. Tam olarak yönetilen bir hizmet olarak platform (PaaS), kendi kümelerinizi yönetmek, yapılandırmak veya çalıştırmak zorunda kalmadan PaaS Kafka deneyimi sunmak üzere [Apache Kafka](https://kafka.apache.org/) ile kolayca tümleştirilebilir.

## <a name="connect-your-application-to-azure-event-hubs"></a>Uygulamanızı Azure 'a bağlama Event Hubs

1. Daha sonra kullanmak üzere Event Hubs bağlantı dizesini ve tam etki alanı adını (FQDN) alın. Yönergeler için bkz. [Event Hubs bağlantı dizesi alma](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string).
2. Kafka için Event Hubs okumaya başlamak üzere kodunuzda ad uzayındaki ayrıntılarla aşağıdaki konfigürasyonları ayarlayın:
    1. Uygulamanızda **BOOTSTRAP_SERVERS** ve **EH_SASL** güncelleştirin, örneğin:

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a>Azure Olay Hub 'ı akışından okuma

Artık Kafka ile yaptığınız gibi Event Hubs ile akışı başlatabilirsiniz. Örnek kodu aşağıda gösterildiği gibi:

```csharp
SparkSession spark = SparkSession
    .Builder()
    .AppName("Connect Event Hub")
    .GetOrCreate();

DataFrame df = spark
    .ReadStream()
    .Format("kafka")
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("subscribe", "spark-test")
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("kafka.request.timeout.ms", "60000")
    .Option("kafka.session.timeout.ms", "60000")
    .Option("failOnDataLoss", "false")
    .Load();

DataFrame dfWrite = df
    .WriteStream()
    .OutputMode("append")
    .Format("console")
    .Start();
```

## <a name="write-to-azure-event-hub-stream"></a>Azure Olay Hub 'ı akışına yaz

Event Hubs Ayrıca, aşağıda gösterildiği gibi aynı şekilde yazabilirsiniz:

```csharp
// df is the DataFrame to write

df.WriteStream()
    .Format("kafka")
    .Option("topic", topics)
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("checkpointLocation", "./checkpoint")
    .Start();
```

## <a name="run-your-application"></a>Uygulamanızı çalıştırma

.NET Apache Spark uygulamanızı çalıştırmak için, ' `spark-sql-kafka-0-10` `libraryDependency` ın SBT projelerinde ' de kullanarak, Spark projenizde derleme tanımının bir parçası olarak modülü tanımlamanız gerekir `build.sbt` . `spark-submit`(Veya) gibi Spark ortamları için `spark-shell` , şöyle bir `--packages` komut satırı seçeneğini kullanmanız gerekir:

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> Çalıştırılan Spark sürümüne uygun olarak paket sürümünü eklediğinizden emin olun.
