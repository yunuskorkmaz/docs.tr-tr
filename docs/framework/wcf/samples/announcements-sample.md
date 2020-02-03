---
title: Duyuru Örnekleri
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: c3824fb0dc7ab4169c309d1a5154127d6bc3b78f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747005"
---
# <a name="announcements-sample"></a><span data-ttu-id="c43d7-102">Duyuru Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c43d7-102">Announcements Sample</span></span>

<span data-ttu-id="c43d7-103">Bu örnek, bulma özelliğinin duyuru işlevselliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="c43d7-104">Duyurular, hizmetlerin hizmetle ilgili meta verileri içeren duyuru iletileri göndermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c43d7-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="c43d7-105">Varsayılan olarak, hizmet başlatıldığında bir Hello duyurusu gönderilir ve hizmet kapandığında bir bye duyurusu gönderilir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="c43d7-106">Bu duyurular çok noktaya yayın yapabilir veya noktadan noktaya gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="c43d7-107">Bu örnek iki proje hizmetinden ve istemcisinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c43d7-107">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="c43d7-108">Hizmet</span><span class="sxs-lookup"><span data-stu-id="c43d7-108">Service</span></span>

<span data-ttu-id="c43d7-109">Bu proje, şirket içinde barındırılan bir Hesaplayıcı hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="c43d7-110">`Main` yönteminde bir hizmet ana bilgisayarı oluşturulur ve buna bir hizmet uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="c43d7-111">Sonra bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c43d7-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="c43d7-112">Duyuruları etkinleştirmek için <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>bir duyuru uç noktası eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="c43d7-113">Bu durumda, UDP çok noktaya yayın kullanan standart bir uç nokta, duyuru uç noktası olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="c43d7-114">Bu, duyuruları iyi bilinen bir UDP adresi üzerinden yayınlar.</span><span class="sxs-lookup"><span data-stu-id="c43d7-114">This broadcasts the announcements over a well-known UDP address.</span></span>

```csharp
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);

     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();

     // Announce the availability of the service over UDP multicast
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());

    // Make the service discoverable over UDP multicast.
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());
    serviceHost.Open();
    // ...
}
```

## <a name="client"></a><span data-ttu-id="c43d7-115">İstemci</span><span class="sxs-lookup"><span data-stu-id="c43d7-115">Client</span></span>

<span data-ttu-id="c43d7-116">Bu projede, istemcinin bir <xref:System.ServiceModel.Discovery.AnnouncementService>barındırdığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c43d7-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="c43d7-117">Ayrıca, iki temsilci olaylar ile kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="c43d7-118">Bu olaylar, çevrimiçi ve çevrimdışı Duyurular alındığında istemcinin ne yaptığını belirler.</span><span class="sxs-lookup"><span data-stu-id="c43d7-118">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="c43d7-119">`OnOnlineEvent` ve `OnOfflineEvent` yöntemleri sırasıyla Merhaba ve bye bildiri iletilerini işler.</span><span class="sxs-lookup"><span data-stu-id="c43d7-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="c43d7-120">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c43d7-120">To use this sample</span></span>

1. <span data-ttu-id="c43d7-121">Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="c43d7-122">Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="c43d7-122">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="c43d7-123">Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-123">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="c43d7-124">Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c43d7-124">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="c43d7-125">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c43d7-125">Build the solution.</span></span>

3. <span data-ttu-id="c43d7-126">Client. exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c43d7-126">Run the client.exe application.</span></span>

4. <span data-ttu-id="c43d7-127">Service. exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c43d7-127">Run the service.exe application.</span></span> <span data-ttu-id="c43d7-128">İstemcinin bir çevrimiçi duyuru aldığını aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="c43d7-128">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="c43d7-129">Service. exe uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="c43d7-129">Close the service.exe application.</span></span> <span data-ttu-id="c43d7-130">İstemcinin çevrimdışı bir duyuru aldığını aklınızda bırakın.</span><span class="sxs-lookup"><span data-stu-id="c43d7-130">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c43d7-131">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c43d7-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c43d7-132">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c43d7-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c43d7-133">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="c43d7-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c43d7-134">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c43d7-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
