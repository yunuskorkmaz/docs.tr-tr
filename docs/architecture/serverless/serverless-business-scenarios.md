---
title: Sunucusuz uygulamalar için örnek iş senaryoları ve kullanım örnekleri
description: Görüntü işlemeden mobil desteğe ve ETL işlem hattına kadar olan örneklere erişerek, uygulamalı bir yaklaşım ile sunucusuz öğrenin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 5c2ee70b86fbc9a54d2a532eaa3d7509f23825df
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135665"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="b744a-103">Sunucusuz iş senaryoları ve kullanım örnekleri</span><span class="sxs-lookup"><span data-stu-id="b744a-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="b744a-104">Sunucusuz uygulamalar için birçok kullanım durumu ve senaryosu vardır.</span><span class="sxs-lookup"><span data-stu-id="b744a-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="b744a-105">Bu bölümde, farklı senaryoları gösteren örnekler yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="b744a-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="b744a-106">Senaryolar ilgili belgelerin ve genel kaynak kodu depolarının bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b744a-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="b744a-107">Bu bölümdeki örnekler, kendi oluşturma ve sunucusuz çözümler uygulamanıza başlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b744a-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="b744a-108">Büyük veri işleme</span><span class="sxs-lookup"><span data-stu-id="b744a-108">Big data processing</span></span>

![Şemayı eşleme/azaltma](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="b744a-110">Bu örnek, büyük bir veri kümesinde bir eşleme/azaltma işlemi yapmak için sunucusuz kullanır.</span><span class="sxs-lookup"><span data-stu-id="b744a-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="b744a-111">2017 ' de günde yeni York sarı vergilenme dönüşlerin ortalama hızını belirler.</span><span class="sxs-lookup"><span data-stu-id="b744a-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="b744a-112">Büyük veri Işleme: Azure 'da sunucusuz MapReduce</span><span class="sxs-lookup"><span data-stu-id="b744a-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="b744a-113">Sunucusuz uygulamalar oluşturma: Uygulamalı laboratuvar</span><span class="sxs-lookup"><span data-stu-id="b744a-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="b744a-114">Sunucu tarafı mantığı çalıştırmak ve sunucusuz mimariler oluşturmak için işlevleri kullanmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="b744a-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="b744a-115">İşletmeniz için en iyi Azure hizmetini seçme</span><span class="sxs-lookup"><span data-stu-id="b744a-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="b744a-116">Azure Işlevleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="b744a-116">Creating Azure Functions</span></span>
- <span data-ttu-id="b744a-117">Tetikleyicileri kullanma</span><span class="sxs-lookup"><span data-stu-id="b744a-117">Using triggers</span></span>
- <span data-ttu-id="b744a-118">Zincirleme işlevleri</span><span class="sxs-lookup"><span data-stu-id="b744a-118">Chaining functions</span></span>
- <span data-ttu-id="b744a-119">Uzun süre çalışan iş akışları</span><span class="sxs-lookup"><span data-stu-id="b744a-119">Long-running workflows</span></span>
- <span data-ttu-id="b744a-120">İzleme</span><span class="sxs-lookup"><span data-stu-id="b744a-120">Monitoring</span></span>
- <span data-ttu-id="b744a-121">Geliştirme, test ve dağıtım</span><span class="sxs-lookup"><span data-stu-id="b744a-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="b744a-122">Sunucusuz uygulamalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="b744a-122">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="b744a-123">Müşteri İncelemeleri</span><span class="sxs-lookup"><span data-stu-id="b744a-123">Customer reviews</span></span>

<span data-ttu-id="b744a-124">Bu örnek, Visual Studio 'da C# sınıf kitaplıkları için yeni Azure Işlevleri araçları 'nı örnekler.</span><span class="sxs-lookup"><span data-stu-id="b744a-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="b744a-125">Müşterilerin Azure depolama Blobları ve CosmosDB 'de depolanan ürün incelemelerini göndermesi için bir Web sitesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b744a-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="b744a-126">Azure bilişsel hizmetler 'i kullanarak müşteri incelemelerinin otomatik olarak yönetimini gerçekleştirmek için bir Azure Işlevi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b744a-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="b744a-127">Web sitesini işlevden ayırmak için bir Azure depolama kuyruğu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b744a-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="b744a-128">Bilişsel hizmetler ile müşteri Incelemeleri uygulaması</span><span class="sxs-lookup"><span data-stu-id="b744a-128">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="b744a-129">Docker Linux görüntü desteği</span><span class="sxs-lookup"><span data-stu-id="b744a-129">Docker Linux image support</span></span>

<span data-ttu-id="b744a-130">Bu örnek, bir Linux Docker `Dockerfile` kapsayıcısında Azure işlevleri oluşturmak ve çalıştırmak için nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b744a-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="b744a-131">Linux 'ta Azure Işlevleri</span><span class="sxs-lookup"><span data-stu-id="b744a-131">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="b744a-132">Dosya işleme ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="b744a-132">File processing and validation</span></span>

<span data-ttu-id="b744a-133">Bu örnek, kuramsal müşterilerden bir CSV dosyası kümesini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="b744a-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="b744a-134">"Batch" müşterisi için gereken tüm dosyaların kullanılabilir olmasını sağlar ve sonra her bir dosyanın yapısını doğrular.</span><span class="sxs-lookup"><span data-stu-id="b744a-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="b744a-135">Azure Işlevleri, Logic Apps ve Dayanıklı İşlevler kullanılarak farklı çözümler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b744a-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="b744a-136">Azure Işlevleri, Logic Apps ve Dayanıklı İşlevler kullanarak dosya işleme ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="b744a-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="b744a-137">Oyun verileri görselleştirme</span><span class="sxs-lookup"><span data-stu-id="b744a-137">Game data visualization</span></span>

![Oyun telemetrisi](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="b744a-139">Bir geliştiricinin oyunları için bir düzenleyici veri görselleştirme çözümünü nasıl uygulayamayacağı hakkında bir örnek.</span><span class="sxs-lookup"><span data-stu-id="b744a-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="b744a-140">Aslında, bir Unreal Engine 4 eklentisi ve Unity eklentisi arka ucu olarak bu örnek kullanılarak geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b744a-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="b744a-141">Hizmet bileşeni, oyun altyapısı belirsiz.</span><span class="sxs-lookup"><span data-stu-id="b744a-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="b744a-142">Düzenleyici içi oyun telemetri görselleştirmesi</span><span class="sxs-lookup"><span data-stu-id="b744a-142">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="b744a-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="b744a-143">GraphQL</span></span>

<span data-ttu-id="b744a-144">GraphQL API 'sini kullanıma sunan sunucusuz bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b744a-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="b744a-145">GraphQL için sunucusuz işlevler</span><span class="sxs-lookup"><span data-stu-id="b744a-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="b744a-146">Nesnelerin İnterneti (IoT) güvenilir Edge geçişi</span><span class="sxs-lookup"><span data-stu-id="b744a-146">Internet of Things (IoT) reliable edge relay</span></span>

![IoT mimarisi](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="b744a-148">Bu örnek, IoT cihazlarından güvenilir yukarı akış iletişimini etkinleştirmek için yeni bir iletişim protokolü uygular.</span><span class="sxs-lookup"><span data-stu-id="b744a-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="b744a-149">Veri boşluğu algılamayı ve geri dolguyu otomatikleştirir.</span><span class="sxs-lookup"><span data-stu-id="b744a-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="b744a-150">IoT güvenilir Edge geçişi</span><span class="sxs-lookup"><span data-stu-id="b744a-150">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="b744a-151">Mikro hizmetler başvuru mimarisi</span><span class="sxs-lookup"><span data-stu-id="b744a-151">Microservices reference architecture</span></span>

![Başvuru mimarisi](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="b744a-153">Reuna bulut uygulamasına (kurgusal bir şirket) göre grup tasarlama, geliştirme ve sunma konusunda karar veren işlem sürecinde size kılavuzluk eden bir başvuru mimarisi.</span><span class="sxs-lookup"><span data-stu-id="b744a-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="b744a-154">Mimarinin tüm bileşenlerini yapılandırmaya ve dağıtmaya yönelik uygulamalı yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="b744a-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="b744a-155">Sunucusuz mikro hizmetler başvuru mimarisi</span><span class="sxs-lookup"><span data-stu-id="b744a-155">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="b744a-156">Konsol uygulamalarını sunucusuz 'e geçirme</span><span class="sxs-lookup"><span data-stu-id="b744a-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="b744a-157">Bu örnek, herhangi bir konsol uygulamasını`.csx` Azure IŞLEVLERINDE bir http Web hizmetine dönüştürmek için kullanılabilen genel bir işlevdir (dosya).</span><span class="sxs-lookup"><span data-stu-id="b744a-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="b744a-158">Tek yapmanız gereken, `.exe`bir yapılandırma dosyasını düzenleyeceğiniz ve öğesine bağımsız değişken olarak geçirilecek giriş parametrelerini belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="b744a-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="b744a-159">Konsol uygulamalarını Azure Işlevleri üzerinde çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b744a-159">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="b744a-160">Mobil için sunucusuz</span><span class="sxs-lookup"><span data-stu-id="b744a-160">Serverless for mobile</span></span>

<span data-ttu-id="b744a-161">Azure Işlevlerinin kolayca uygulanması ve bakımını yapmak ve HTTP üzerinden erişilebilir olması kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="b744a-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="b744a-162">Bir mobil uygulama için API uygulamanın harika bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="b744a-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="b744a-163">Microsoft, Xamarin ile iOS, Android ve Windows için harika platformlar arası araçlar sunar.</span><span class="sxs-lookup"><span data-stu-id="b744a-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="b744a-164">Bu nedenle, Xamarin ve Azure Işlevleri birlikte harika çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b744a-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="b744a-165">Bu makalede, Azure Web portalında veya Visual Studio 'da ilk olarak Azure Işlevinin nasıl uygulanacağı ve Android, iOS ve Windows üzerinde çalışan Xamarin. Forms ile platformlar arası istemci oluşturma işlemlerinin nasıl yapılacağı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b744a-165">This article shows how to implement an Azure Function in the Azure Web Portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms, running on Android, iOS, and Windows.</span></span>

[<span data-ttu-id="b744a-166">Xamarin. Forms istemcisiyle basit bir Azure Işlevi uygulama</span><span class="sxs-lookup"><span data-stu-id="b744a-166">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a><span data-ttu-id="b744a-167">Sunucusuz mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="b744a-167">Serverless messaging</span></span>

<span data-ttu-id="b744a-168">Bu örnek, her sayıdaki oturum/bölüm arasında rastgele sayıda ileti yüklemek için Dayanıklı İşlevler ' fan çıkış deseninin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b744a-168">This sample shows how to utilize Durable Functions' fan out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="b744a-169">Service Bus, Event Hubs veya depolama kuyruklarını hedefler.</span><span class="sxs-lookup"><span data-stu-id="b744a-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="b744a-170">Örnek ayrıca, başka bir Azure Işleviyle bu iletileri kullanma ve sonuç zamanlama verilerini başka bir olay hub 'ına yükleme özelliğini de ekler.</span><span class="sxs-lookup"><span data-stu-id="b744a-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="b744a-171">Veriler daha sonra Azure Veri Gezgini gibi analiz hizmetlerine alınır.</span><span class="sxs-lookup"><span data-stu-id="b744a-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="b744a-172">Azure Işlevleri ile Service Bus, Event Hubs ve depolama kuyrukları aracılığıyla ileti oluşturun ve kullanın</span><span class="sxs-lookup"><span data-stu-id="b744a-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="b744a-173">Önerilen Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b744a-173">Recommended resources</span></span>

- [<span data-ttu-id="b744a-174">Linux 'ta Azure Işlevleri</span><span class="sxs-lookup"><span data-stu-id="b744a-174">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="b744a-175">Büyük veri Işleme: Azure 'da sunucusuz MapReduce</span><span class="sxs-lookup"><span data-stu-id="b744a-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="b744a-176">Sunucusuz uygulamalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="b744a-176">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="b744a-177">Bilişsel hizmetler ile müşteri Incelemeleri uygulaması</span><span class="sxs-lookup"><span data-stu-id="b744a-177">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="b744a-178">Azure Işlevleri, Logic Apps ve Dayanıklı İşlevler kullanarak dosya işleme ve doğrulama</span><span class="sxs-lookup"><span data-stu-id="b744a-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [<span data-ttu-id="b744a-179">Xamarin. Forms istemcisiyle basit bir Azure Işlevi uygulama</span><span class="sxs-lookup"><span data-stu-id="b744a-179">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="b744a-180">Düzenleyici içi oyun telemetri görselleştirmesi</span><span class="sxs-lookup"><span data-stu-id="b744a-180">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="b744a-181">IoT güvenilir Edge geçişi</span><span class="sxs-lookup"><span data-stu-id="b744a-181">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="b744a-182">Azure Işlevleri ile Service Bus, Event Hubs ve depolama kuyrukları aracılığıyla ileti oluşturun ve kullanın</span><span class="sxs-lookup"><span data-stu-id="b744a-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="b744a-183">Konsol uygulamalarını Azure Işlevleri üzerinde çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b744a-183">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="b744a-184">GraphQL için sunucusuz işlevler</span><span class="sxs-lookup"><span data-stu-id="b744a-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="b744a-185">Sunucusuz mikro hizmetler başvuru mimarisi</span><span class="sxs-lookup"><span data-stu-id="b744a-185">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="b744a-186">[Önceki](orchestration-patterns.md)
>[İleri](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="b744a-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
