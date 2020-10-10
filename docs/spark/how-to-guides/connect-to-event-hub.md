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
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="37172-103">Apache Spark için .NET Event Hubs Azure 'a bağlama</span><span class="sxs-lookup"><span data-stu-id="37172-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="37172-104">Bu makalede, Apache Kafka akışlarını okumak ve yazmak için .net Event Hubs [Apache Spark](https://github.com/dotnet/spark) uygulamanızı Azure 'a nasıl bağlayacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="37172-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="37172-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="37172-105">Prerequisites</span></span>

1. <span data-ttu-id="37172-106">Bir olay hub 'ı ile bir Event Hubs ad alanı hazırlayın, bunun nasıl yapılacağını gösteren adım adım kılavuz için [Bu belgeye](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) bakın.</span><span class="sxs-lookup"><span data-stu-id="37172-106">Have an Event Hubs Namespace ready with an event hub, refer to [this document](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) for a step-by-step guide on how to do that.</span></span> <span data-ttu-id="37172-107">Olay Hub 'ı ad alanını oluştururken standart fiyatlandırma katmanını seçtiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="37172-107">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="37172-108">Azure Event Hubs nedir?</span><span class="sxs-lookup"><span data-stu-id="37172-108">What is Azure Event Hubs</span></span>

<span data-ttu-id="37172-109">[Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) , büyük bir veri akışı platformu ve olay alma hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="37172-109">[Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) is a big data streaming platform and event ingestion service.</span></span> <span data-ttu-id="37172-110">Tam olarak yönetilen bir hizmet olarak platform (PaaS), kendi kümelerinizi yönetmek, yapılandırmak veya çalıştırmak zorunda kalmadan PaaS Kafka deneyimi sunmak üzere [Apache Kafka](https://kafka.apache.org/) ile kolayca tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="37172-110">It is a fully managed Platform-as-a-Service (PaaS), that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="37172-111">Uygulamanızı Azure 'a bağlama Event Hubs</span><span class="sxs-lookup"><span data-stu-id="37172-111">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="37172-112">Daha sonra kullanmak üzere Event Hubs bağlantı dizesini ve tam etki alanı adını (FQDN) alın.</span><span class="sxs-lookup"><span data-stu-id="37172-112">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="37172-113">Yönergeler için bkz. [Event Hubs bağlantı dizesi alma](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string).</span><span class="sxs-lookup"><span data-stu-id="37172-113">For instructions, see [Get an Event Hubs connection string](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="37172-114">Kafka için Event Hubs okumaya başlamak üzere kodunuzda ad uzayındaki ayrıntılarla aşağıdaki konfigürasyonları ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="37172-114">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="37172-115">Uygulamanızda **BOOTSTRAP_SERVERS** ve **EH_SASL** güncelleştirin, örneğin:</span><span class="sxs-lookup"><span data-stu-id="37172-115">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="37172-116">Azure Olay Hub 'ı akışından okuma</span><span class="sxs-lookup"><span data-stu-id="37172-116">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="37172-117">Artık Kafka ile yaptığınız gibi Event Hubs ile akışı başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37172-117">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="37172-118">Örnek kodu aşağıda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="37172-118">Sample code as shown below:</span></span>

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

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="37172-119">Azure Olay Hub 'ı akışına yaz</span><span class="sxs-lookup"><span data-stu-id="37172-119">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="37172-120">Event Hubs Ayrıca, aşağıda gösterildiği gibi aynı şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="37172-120">You can also write to Event Hubs in the same way, as shown below:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="37172-121">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="37172-121">Run your application</span></span>

<span data-ttu-id="37172-122">.NET Apache Spark uygulamanızı çalıştırmak için, ' `spark-sql-kafka-0-10` `libraryDependency` ın SBT projelerinde ' de kullanarak, Spark projenizde derleme tanımının bir parçası olarak modülü tanımlamanız gerekir `build.sbt` .</span><span class="sxs-lookup"><span data-stu-id="37172-122">In order to run your .NET for Apache Spark application, you should define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="37172-123">`spark-submit`(Veya) gibi Spark ortamları için `spark-shell` , şöyle bir `--packages` komut satırı seçeneğini kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="37172-123">For Spark environments such as `spark-submit` (or `spark-shell`) you should use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="37172-124">Çalıştırılan Spark sürümüne uygun olarak paket sürümünü eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="37172-124">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
