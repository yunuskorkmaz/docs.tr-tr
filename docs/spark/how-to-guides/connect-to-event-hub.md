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
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="b6dd2-103">Apache Spark için .NET Event Hubs Azure 'a bağlama</span><span class="sxs-lookup"><span data-stu-id="b6dd2-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="b6dd2-104">Bu makalede, Apache Kafka akışlarını okumak ve yazmak için .net Event Hubs [Apache Spark](https://github.com/dotnet/spark) uygulamanızı Azure 'a nasıl bağlayacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6dd2-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="b6dd2-105">Prerequisites</span></span>

<span data-ttu-id="b6dd2-106">Bir olay hub 'ı ile bir Event Hubs ad alanı hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-106">Have an Event Hubs Namespace ready with an event hub.</span></span> <span data-ttu-id="b6dd2-107">Adım adım kılavuz için [hızlı başlangıç: Azure Portal kullanarak bir olay hub 'ı oluşturma](/azure/event-hubs/event-hubs-create)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-107">For a step-by-step guide, refer to [Quickstart: Create an event hub using Azure portal](/azure/event-hubs/event-hubs-create).</span></span> <span data-ttu-id="b6dd2-108">Olay Hub 'ı ad alanını oluştururken standart fiyatlandırma katmanını seçtiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-108">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="b6dd2-109">Azure Event Hubs nedir?</span><span class="sxs-lookup"><span data-stu-id="b6dd2-109">What is Azure Event Hubs</span></span>

<span data-ttu-id="b6dd2-110">[Azure Event Hubs](/azure/event-hubs/event-hubs-about) , büyük veri akışı platformu ve olay alma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-110">[Azure Event Hubs](/azure/event-hubs/event-hubs-about) is a big-data streaming platform and event-ingestion service.</span></span> <span data-ttu-id="b6dd2-111">Kendi kümelerinizi yönetmek, yapılandırmak veya çalıştırmak zorunda kalmadan PaaS Kafka deneyimi sağlamak üzere [Apache Kafka](https://kafka.apache.org/) ile kolayca tümleştirilebilen, tam olarak yönetilen bir hizmet olarak platform (PaaS).</span><span class="sxs-lookup"><span data-stu-id="b6dd2-111">It is a fully managed Platform-as-a-Service (PaaS) that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure, or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="b6dd2-112">Uygulamanızı Azure 'a bağlama Event Hubs</span><span class="sxs-lookup"><span data-stu-id="b6dd2-112">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="b6dd2-113">Daha sonra kullanmak üzere Event Hubs bağlantı dizesini ve tam etki alanı adını (FQDN) alın.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-113">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="b6dd2-114">Yönergeler için bkz. [Event Hubs bağlantı dizesi alma](/azure/event-hubs/event-hubs-get-connection-string).</span><span class="sxs-lookup"><span data-stu-id="b6dd2-114">For instructions, see [Get an Event Hubs connection string](/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="b6dd2-115">Kafka için Event Hubs okumaya başlamak üzere kodunuzda ad uzayındaki ayrıntılarla aşağıdaki konfigürasyonları ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b6dd2-115">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="b6dd2-116">Uygulamanızda **BOOTSTRAP_SERVERS** ve **EH_SASL** güncelleştirin, örneğin:</span><span class="sxs-lookup"><span data-stu-id="b6dd2-116">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="b6dd2-117">Azure Olay Hub 'ı akışından okuma</span><span class="sxs-lookup"><span data-stu-id="b6dd2-117">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="b6dd2-118">Artık Kafka ile yaptığınız gibi Event Hubs ile akışı başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-118">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="b6dd2-119">Örnek kodu aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="b6dd2-119">Sample code as shown below:</span></span>

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

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="b6dd2-120">Azure Olay Hub 'ı akışına yaz</span><span class="sxs-lookup"><span data-stu-id="b6dd2-120">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="b6dd2-121">Event Hubs Ayrıca, aşağıda gösterildiği gibi aynı şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b6dd2-121">You can also write to Event Hubs in the same way, as shown below:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="b6dd2-122">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b6dd2-122">Run your application</span></span>

<span data-ttu-id="b6dd2-123">.NET Apache Spark uygulamanızı çalıştırmak için, ' `spark-sql-kafka-0-10` `libraryDependency` de `build.sbt` SBT projeleri için ' de kullanarak, derleme tanımının bir parçası olarak modülü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-123">In order to run your .NET for Apache Spark application, define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="b6dd2-124">`spark-submit`(Veya) gibi Spark ortamları için `spark-shell` , şöyle bir `--packages` komut satırı seçeneğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="b6dd2-124">For Spark environments such as `spark-submit` (or `spark-shell`), use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="b6dd2-125">Çalıştırılan Spark sürümüne uygun olarak paket sürümünü eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-125">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
