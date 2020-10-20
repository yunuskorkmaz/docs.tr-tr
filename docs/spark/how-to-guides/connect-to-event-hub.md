---
title: Apache Spark için .NET Event Hubs Azure 'a bağlama
description: Apache Spark örneği için yerel .NET 'ten Azure Event hub 'a nasıl bağlanacağınızı öğrenin.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c8fd10992e63674032af4148e0673a5330d9086c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223965"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a>Apache Spark için .NET Event Hubs Azure 'a bağlama

Bu makalede, Apache Kafka akışlarını okumak ve yazmak için .net Event Hubs [Apache Spark](https://github.com/dotnet/spark) uygulamanızı Azure 'a nasıl bağlayacağınızı öğreneceksiniz.

## <a name="prerequisites"></a>Ön koşullar

Bir olay hub 'ı ile bir Event Hubs ad alanı hazırlayın. Adım adım kılavuz için [hızlı başlangıç: Azure Portal kullanarak bir olay hub 'ı oluşturma](/azure/event-hubs/event-hubs-create)bölümüne bakın. Olay Hub 'ı ad alanını oluştururken standart fiyatlandırma katmanını seçtiğinizden emin olun.

## <a name="what-is-azure-event-hubs"></a>Azure Event Hubs nedir?

[Azure Event Hubs](/azure/event-hubs/event-hubs-about) , büyük veri akışı platformu ve olay alma hizmetidir. Kendi kümelerinizi yönetmek, yapılandırmak veya çalıştırmak zorunda kalmadan PaaS Kafka deneyimi sağlamak üzere [Apache Kafka](https://kafka.apache.org/) ile kolayca tümleştirilebilen, tam olarak yönetilen bir hizmet olarak platform (PaaS).

## <a name="connect-your-application-to-azure-event-hubs"></a>Uygulamanızı Azure 'a bağlama Event Hubs

1. Daha sonra kullanmak üzere Event Hubs bağlantı dizesini ve tam etki alanı adını (FQDN) alın. Yönergeler için bkz. [Event Hubs bağlantı dizesi alma](/azure/event-hubs/event-hubs-get-connection-string).
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

.NET Apache Spark uygulamanızı çalıştırmak için, ' `spark-sql-kafka-0-10` `libraryDependency` de `build.sbt` SBT projeleri için ' de kullanarak, derleme tanımının bir parçası olarak modülü tanımlayın. `spark-submit`(Veya) gibi Spark ortamları için `spark-shell` , şöyle bir `--packages` komut satırı seçeneğini kullanın:

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> Çalıştırılan Spark sürümüne uygun olarak paket sürümünü eklediğinizden emin olun.
