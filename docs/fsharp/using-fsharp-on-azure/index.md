---
title: "F # Azure üzerinde kullanma"
description: "F # ile Azure hizmetlerini kullanmaya Kılavuzu"
keywords: "Azure, bulut, visual f #, f #'ta, .NET, .NET Core işlevsel programlama"
author: sylvanc
ms.author: phcart
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: FAD4D11E-703A-42D4-9F72-893D9E0F569B
ms.openlocfilehash: 636604b1a0b645f13ac20d7ed85bde9abae3f9f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-f-on-azure"></a><span data-ttu-id="e4bcc-104">F # Azure üzerinde kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-104">Using F# on Azure</span></span>

<span data-ttu-id="e4bcc-105">F # bulut programlama için mükemmel bir dildir ve web uygulamaları, bulut Hizmetleri, bulutta barındırılan mikro yazmak için sık kullanılan ve ölçeklenebilir veri işleme için.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-105">F# is a superb language for cloud programming and is frequently used to write web applications, cloud services, cloud-hosted microservices, and for scalable data processing.</span></span>

<span data-ttu-id="e4bcc-106">Aşağıdaki bölümlerde, aralığı, Azure Hizmetleri F # ile kullanma hakkında kaynaklar bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-106">In the following sections, you will find resources on how to use a range of Azure services with F#.</span></span>

> [!NOTE]
> <span data-ttu-id="e4bcc-107">Lütfen belirli bir Azure hizmet bu belgelerde değilse, bu hizmet için Azure işlevleri veya .NET belgelerine başvurun.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-107">If a particular Azure service isn't in this documentation set, please consult either the Azure Functions or .NET documentation for that service.</span></span> <span data-ttu-id="e4bcc-108">Bazı Azure Hizmetleri dilden bağımsız ve hiçbir dile özgü belge gerektirir ve burada listelenmeyen.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-108">Some Azure services are language-independent and require no language-specific documentation and are not listed here.</span></span>

## <a name="using-azure-virtual-machines-with-f"></a><span data-ttu-id="e4bcc-109">Azure sanal makineleri F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-109">Using Azure Virtual Machines with F#</span></span> #

<span data-ttu-id="e4bcc-110">Azure sanal makine (VM) yapılandırmaları çeşitli destekler, bkz: [Linux ve Azure sanal makineleri](https://azure.microsoft.com/services/virtual-machines/).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-110">Azure supports a wide range of virtual machine (VM) configurations, see [Linux and Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).</span></span>

<span data-ttu-id="e4bcc-111">F # yürütme, derleme ve/veya bkz için bir sanal makinede yüklemek için [kullanarak F # Linux'ta](http://fsharp.org/use/linux) ve [kullanarak F # Windows](http://fsharp.org/use/windows).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-111">To install F# on a virtual machine for execution, compilation and/or scripting see [Using F# on Linux](http://fsharp.org/use/linux) and [Using F# on Windows](http://fsharp.org/use/windows).</span></span>


## <a name="using-azure-functions-with-f"></a><span data-ttu-id="e4bcc-112">Azure işlevleri F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-112">Using Azure Functions with F#</span></span> #

<span data-ttu-id="e4bcc-113">[Azure işlevleri](https://azure.microsoft.com/services/functions/) kolayca kodu veya "işlevleri" küçük parçalarını çalıştırmak için bir bulutta çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-113">[Azure Functions](https://azure.microsoft.com/services/functions/) is a solution for easily running small pieces of code, or "functions," in the cloud.</span></span> <span data-ttu-id="e4bcc-114">Tüm uygulama veya çalıştırmak için altyapı hakkında endişelenmeden elinizdeki sorun için ihtiyacınız olan kodu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-114">You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it.</span></span> <span data-ttu-id="e4bcc-115">İşlevlerinizi Azure depolama ve diğer bulutta barındırılan kaynakları olayları bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-115">Your functions are connected to events in Azure storage and other cloud-hosted resources.</span></span> <span data-ttu-id="e4bcc-116">Veri, F # işlevleri işlev bağımsız değişkenleri aracılığıyla akar.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-116">Data flows into your F# functions via function arguments.</span></span> <span data-ttu-id="e4bcc-117">İhtiyaca göre ölçekleme için güvenen Azure tercih ettiğiniz geliştirme dilini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-117">You can use your development language of choice, trusting Azure to scale as needed.</span></span>

<span data-ttu-id="e4bcc-118">Azure işlevleri F # olarak F # kodu verimli, geriye dönük, ölçeklenebilir yürütülmesi ile birinci sınıf bir dil için destek.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-118">Azure Functions support F# as a first-class language with efficient, reactive, scalable execution of F# code.</span></span> <span data-ttu-id="e4bcc-119">Bkz: [Azure işlevleri F # Geliştirici Başvurusu](/azure/azure-functions/functions-reference-fsharp) F # ile Azure işlevlerinin nasıl kullanılacağı hakkında başvuru belgeleri için.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-119">See the [Azure Functions F# Developer Reference](/azure/azure-functions/functions-reference-fsharp) for reference documentation on how to use F# with Azure Functions.</span></span>

<span data-ttu-id="e4bcc-120">Azure işlevleri ve F # kullanma için diğer kaynaklar:</span><span class="sxs-lookup"><span data-stu-id="e4bcc-120">Other resources for using Azure Functions and F#:</span></span>

* [<span data-ttu-id="e4bcc-121">F # Suave kullanarak Azure işlevleri ölçeklendirin</span><span class="sxs-lookup"><span data-stu-id="e4bcc-121">Scale Up Azure Functions in F# Using Suave</span></span>](http://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [<span data-ttu-id="e4bcc-122">F #'de Azure işlevi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-122">How to create Azure function in F#</span></span>](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [<span data-ttu-id="e4bcc-123">Azure türü sağlayıcısı ile Azure işlevlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-123">Using the Azure Type Provider with Azure Functions</span></span>](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a><span data-ttu-id="e4bcc-124">Azure Storage F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-124">Using Azure Storage with F#</span></span> #

<span data-ttu-id="e4bcc-125">Azure depolama, depolama hizmetleri dayanıklılık, kullanılabilirlik ve ölçeklenebilirlik müşterilerin ihtiyaçlarını karşılamak üzere kullanan modern uygulamalar için temel bir katmanıdır.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-125">Azure Storage is a base layer of storage services for modern applications that rely on durability, availability, and scalability to meet the needs of customers.</span></span> <span data-ttu-id="e4bcc-126">F # programları, doğrudan aşağıdaki makalelerde açıklanan techinques kullanarak Azure storage Hizmetleri ile etkileşim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-126">F# programs can interact directly with Azure storage services, using the techinques described in the following articles.</span></span>

* [<span data-ttu-id="e4bcc-127">F # kullanarak Azure Blob storage'ı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e4bcc-127">Get started with Azure Blob storage using F#</span></span>](blob-storage.md)
* [<span data-ttu-id="e4bcc-128">F # kullanarak Azure File storage'ı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e4bcc-128">Get started with Azure File storage using F#</span></span>](file-storage.md)
* [<span data-ttu-id="e4bcc-129">F # kullanarak Azure kuyruk depolamaya başlayın</span><span class="sxs-lookup"><span data-stu-id="e4bcc-129">Get started with Azure Queue storage using F#</span></span>](queue-storage.md)
* [<span data-ttu-id="e4bcc-130">F # kullanarak Azure Table storage'ı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e4bcc-130">Get started with Azure Table storage using F#</span></span>](table-storage.md)

<span data-ttu-id="e4bcc-131">Azure depolama, Azure işlevleri ile birlikte açık API çağrıları yerine bildirim temelli yapılandırma aracılığıyla da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-131">Azure Storage can also be used in conjunction with Azure Functions through declarative configuration rather than explicit API calls.</span></span> <span data-ttu-id="e4bcc-132">Bkz: [Azure işlevleri Tetikleyicileri ve bağlamaları için Azure Storage](/azure/azure-functions/functions-bindings-storage) F # örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-132">See [Azure Functions triggers and bindings for Azure Storage](/azure/azure-functions/functions-bindings-storage) which includes F# examples.</span></span>

## <a name="using-azure-app-service-with-f"></a><span data-ttu-id="e4bcc-133">Azure uygulama hizmeti F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-133">Using Azure App Service with F#</span></span> #

<span data-ttu-id="e4bcc-134">[Azure uygulama hizmeti](https://azure.microsoft.com/services/app-service/) güçlü web ve Bulut veya şirket içi herhangi bir yerden, veri bağlanmak mobil uygulamaları oluşturmak için bir bulut Platform.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-134">[Azure App Service](https://azure.microsoft.com/services/app-service/) is a cloud platform to build powerful web and mobile apps that connect to data anywhere, in the cloud or on-premises.</span></span>

* [<span data-ttu-id="e4bcc-135">F # Azure Web API örneği</span><span class="sxs-lookup"><span data-stu-id="e4bcc-135">F# Azure Web API example</span></span>](https://github.com/fsprojects/azure-webapi-example)
* [<span data-ttu-id="e4bcc-136">F # Azure üzerinde bir web uygulamasında barındırma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-136">Hosting F# in a web application on Azure</span></span>](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a><span data-ttu-id="e4bcc-137">Apache Spark F # Azure Hdınsight ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-137">Using Apache Spark with F# with Azure HDInsight</span></span>

<span data-ttu-id="e4bcc-138">[Azure Hdınsight'ta Apache Spark](https://azure.microsoft.com/services/hdinsight/apache-spark/) büyük ölçekli veri analizi uygulamaları çalıştıran bir açık kaynak işleme altyapısıdır.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-138">[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) is an open source processing framework that runs large-scale data analytics applications.</span></span> <span data-ttu-id="e4bcc-139">Azure Apache Spark, kolay ve dağıtmak için uygun maliyetli hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-139">Azure makes Apache Spark easy and cost effective to deploy.</span></span> <span data-ttu-id="e4bcc-140">F # kullanarak Spark uygulamanızı geliştirin [Mobius](https://github.com/Microsoft/Mobius), Spark için bir .NET API.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-140">Develop your Spark application in F# using [Mobius](https://github.com/Microsoft/Mobius), a .NET API for Spark.</span></span>

* [<span data-ttu-id="e4bcc-141">F # Mobius kullanarak uygulama Spark uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e4bcc-141">Implementing Spark Apps in F# using Mobius</span></span>](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [<span data-ttu-id="e4bcc-142">Örnek F # Spark Mobius kullanan uygulamalar</span><span class="sxs-lookup"><span data-stu-id="e4bcc-142">Example F# Spark Apps using Mobius</span></span>](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-documentdb-with-f"></a><span data-ttu-id="e4bcc-143">Azure DocumentDB F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-143">Using Azure DocumentDB with F#</span></span> #

<span data-ttu-id="e4bcc-144">[Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) yüksek oranda kullanılabilir, genel olarak dağıtılmış uygulamalar için bir NoSQL hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-144">[Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) is a NoSQL service for highly available, globally distributed apps.</span></span>

<span data-ttu-id="e4bcc-145">Azure DocumentDB F # ile iki şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e4bcc-145">Azure DocumentDB can be used with F# in two ways:</span></span>

1. <span data-ttu-id="e4bcc-146">F # Azure işlevleri oluşturulmasını aracılığıyla hangi tepki veya DocumentDB koleksiyonlarda yapılan değişiklikler neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-146">Through the creation of F# Azure Functions which react to or cause changes to DocumentDB collections.</span></span> <span data-ttu-id="e4bcc-147">Bkz: [Azure DocumentDB için Tetikleyiciler](/azure/azure-functions/functions-bindings-documentdb), veya</span><span class="sxs-lookup"><span data-stu-id="e4bcc-147">See [Azure Function triggers for DocumentDB](/azure/azure-functions/functions-bindings-documentdb), or</span></span>
2. <span data-ttu-id="e4bcc-148">Kullanarak [için Azure .NET SDK'sı](/azure/documentdb/documentdb-get-started-quickstart).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-148">By using the [.NET SDK for Azure](/azure/documentdb/documentdb-get-started-quickstart).</span></span> <span data-ttu-id="e4bcc-149">Bu örnekler C# dilinde olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-149">Note these examples are in C#.</span></span>

## <a name="using-azure-event-hubs-with-f"></a><span data-ttu-id="e4bcc-150">Azure Event Hubs'a F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-150">Using Azure Event Hubs with F#</span></span> #

<span data-ttu-id="e4bcc-151">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) bulut ölçekli telemetri alım Web siteleri, uygulamaları ve cihazları sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-151">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) provide cloud-scale telemetry ingestion from websites, apps, and devices.</span></span>

<span data-ttu-id="e4bcc-152">Azure Event Hubs F # ile iki şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e4bcc-152">Azure Event Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="e4bcc-153">F # Azure işlevleri oluşturulmasını, olaylar tarafından tetiklenen.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-153">Through the creation of F# Azure Functions which are triggered by events.</span></span> <span data-ttu-id="e4bcc-154">Bkz: [Azure Event Hubs için Tetikleyiciler](/azure/azure-functions/functions-bindings-event-hubs), veya</span><span class="sxs-lookup"><span data-stu-id="e4bcc-154">See [Azure Function triggers for Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), or</span></span>
2. <span data-ttu-id="e4bcc-155">Kullanarak [için Azure .NET SDK'sı](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-155">By using the [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted).</span></span> <span data-ttu-id="e4bcc-156">Bu örnekler C# dilinde olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-156">Note these examples are in C#.</span></span>

## <a name="using-azure-notification-hubs-with-f"></a><span data-ttu-id="e4bcc-157">Azure bildirim hub'ları F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-157">Using Azure Notification Hubs with F#</span></span> #

<span data-ttu-id="e4bcc-158">[Azure bildirim hub'ları](/azure/notification-hubs/) herhangi bir arka uçtan (içinde bulutta veya şirket içi) herhangi bir mobil platforma mobil anında iletme bildirimleri göndermek etkinleştirmeniz çok platformlu, ölçeği gönderim altyapısı şunlardır.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-158">[Azure Notification Hubs](/azure/notification-hubs/) are multiplatform, scaled-out push infrastructure that enable you to send mobile push notifications from any backend (in the cloud or on-premises) to any mobile platform.</span></span>

<span data-ttu-id="e4bcc-159">Azure bildirim hub'ları F # ile iki şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e4bcc-159">Azure Notification Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="e4bcc-160">F # Azure işlevleri oluşturulmasını, bir bildirim hub'ına sonuçları gönderir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-160">Through the creation of F# Azure Functions which send results to a notification hub.</span></span> <span data-ttu-id="e4bcc-161">Bkz: [Azure işlevi bildirim hub'ları için Tetikleyiciler çıkış](/azure/azure-functions/functions-bindings-notification-hubs), veya</span><span class="sxs-lookup"><span data-stu-id="e4bcc-161">See [Azure Function output triggers for Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), or</span></span>
2. <span data-ttu-id="e4bcc-162">Kullanarak [için Azure .NET SDK'sı](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-162">By using the [.NET SDK for Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/).</span></span> <span data-ttu-id="e4bcc-163">Bu örnekler C# dilinde olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-163">Note these examples are in C#.</span></span>


## <a name="implementing-webhooks-on-azure-with-f"></a><span data-ttu-id="e4bcc-164">F # ile Azure üzerinde Web Kancalarını uygulama</span><span class="sxs-lookup"><span data-stu-id="e4bcc-164">Implementing WebHooks on Azure with F#</span></span> #

<span data-ttu-id="e4bcc-165">A [Web kancası](https://en.wikipedia.org/wiki/Webhook) olan bir web isteği tetiklenen geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-165">A [Webhook](https://en.wikipedia.org/wiki/Webhook) is a callback triggered via a web request.</span></span> <span data-ttu-id="e4bcc-166">Web kancası sinyal olayları GitHub gibi siteleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-166">Webhooks are used by sites such as GitHub to signal events.</span></span> 

<span data-ttu-id="e4bcc-167">Web kancası F # içinde uygulanan ve Azure üzerinde barındırılan bir [Azure işlevi F # Web kancası bağlama ile](/azure/azure-functions/functions-bindings-http-webhook).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-167">Webhooks can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Webhook Binding](/azure/azure-functions/functions-bindings-http-webhook).</span></span>

## <a name="using-webjobs-with-f"></a><span data-ttu-id="e4bcc-168">Webjobs F # ile kullanma</span><span class="sxs-lookup"><span data-stu-id="e4bcc-168">Using Webjobs with F#</span></span> #

<span data-ttu-id="e4bcc-169">[Web işleri](/azure/app-service-web/web-sites-create-web-jobs) programları App Service web uygulamanızda üç yolla çalıştırabilirsiniz: isteğe bağlı olarak, sürekli olarak veya bir zamanlamaya göre.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-169">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) are programs you can run in your App Service web app in three ways: on demand, continuously, or on a schedule.</span></span>

[<span data-ttu-id="e4bcc-170">Örnek F # Webjob</span><span class="sxs-lookup"><span data-stu-id="e4bcc-170">Example F# Webjob</span></span>](https://github.com/andredublin/fsharp-azure-webjob)

## <a name="implementing-timers-on-azure-with-f"></a><span data-ttu-id="e4bcc-171">F # ile Azure üzerinde zamanlayıcılar uygulama</span><span class="sxs-lookup"><span data-stu-id="e4bcc-171">Implementing Timers on Azure with F#</span></span> #

<span data-ttu-id="e4bcc-172">Zamanlayıcı bir zamanlama, bir kez veya yinelenen göre işlevlerine çağrı tetikler.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-172">Timer triggers call functions based on a schedule, one time or recurring.</span></span>

<span data-ttu-id="e4bcc-173">Zamanlayıcılar F # içinde uygulanan ve Azure üzerinde barındırılan bir [Azure işlevi F # Zamanlayıcı tetikleyicisi ile](/azure/azure-functions/functions-bindings-timer).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-173">Timers can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Timer Trigger](/azure/azure-functions/functions-bindings-timer).</span></span>

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a><span data-ttu-id="e4bcc-174">Dağıtma ve F # kodlarıyla Azure kaynaklarını yönetme</span><span class="sxs-lookup"><span data-stu-id="e4bcc-174">Deploying and Managing Azure Resources with F# Scripts</span></span> #

<span data-ttu-id="e4bcc-175">Azure VM'ler programlı olarak dağıtılan ve F # komut dosyalarından Microsoft.Azure.Management paketleri ve API'leri kullanılarak yönetilen.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-175">Azure VMs may be programmatically deployed and managed from F# scripts by using the Microsoft.Azure.Management packages and APIs.</span></span> <span data-ttu-id="e4bcc-176">Örneğin, [.NET için yönetim kitaplıkları ile çalışmaya başlama](https://msdn.microsoft.com/library/dn722415.aspx) ve [kullanarak Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-176">For example, see [Get Started with the Management Libraries for .NET](https://msdn.microsoft.com/library/dn722415.aspx) and [Using Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).</span></span>

<span data-ttu-id="e4bcc-177">Benzer şekilde, diğer Azure kaynaklarına de dağıtılan ve aynı Bileşenleri'ni kullanarak F # betiklerinden yönetilen.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-177">Likewise, other Azure resources may also be deployed and managed from F# scripts using the same components.</span></span> <span data-ttu-id="e4bcc-178">Örneğin, depolama hesabı oluşturma, Azure bulut Hizmetleri dağıtma, Azure DocumentDB örneği oluşturabilir ve Azure gönderemedi hub F # komut dosyalarından programlı olarak yönetmek.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-178">For example, you can create storage accounts, deploy Azure Cloud Services, create Azure DocumentDB instances and manage Azure Notifcation Hubs programmatically from F# scripts.</span></span>

<span data-ttu-id="e4bcc-179">Dağıtmak ve kaynakları yönetmek için F # komut dosyalarını kullanarak normal şekilde gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-179">Using F# scripts to deploy and manage resources is not normally necessary.</span></span> <span data-ttu-id="e4bcc-180">Örneğin, Azure kaynaklarını parametreli olabilir JSON şablonu açıklamaları gelen dağıtılan directy olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4bcc-180">For example, Azure resources may also be deployed directy from JSON template descriptions, which can be parameterized.</span></span> <span data-ttu-id="e4bcc-181">Bkz: [Azure Resource Manager şablonları](/azure/azure-resource-manager/resource-manager-template-best-practices) örnekler gibi dahil [Azure hızlı başlangıç şablonlarını](https://azure.microsoft.com/documentation/templates/).</span><span class="sxs-lookup"><span data-stu-id="e4bcc-181">See [Azure Resource Manager Templates](/azure/azure-resource-manager/resource-manager-template-best-practices) including examples such as the [Azure Quickstart Templates](https://azure.microsoft.com/documentation/templates/).</span></span>

## <a name="other-resources"></a><span data-ttu-id="e4bcc-182">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e4bcc-182">Other resources</span></span>

* [<span data-ttu-id="e4bcc-183">Tüm Azure hizmetleri hakkında tüm belgeleri</span><span class="sxs-lookup"><span data-stu-id="e4bcc-183">Full documentation on all Azure services</span></span>](/azure/)
