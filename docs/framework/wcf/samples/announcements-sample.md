---
description: Daha fazla bilgi için bkz. Duyurular örneği
title: Duyuru Örnekleri
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 076efed31f862f6de68e924446528d682a62824a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778951"
---
# <a name="announcements-sample"></a><span data-ttu-id="a1e24-103">Duyuru Örnekleri</span><span class="sxs-lookup"><span data-stu-id="a1e24-103">Announcements Sample</span></span>

<span data-ttu-id="a1e24-104">Bu örnek, bulma özelliğinin duyuru işlevselliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-104">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="a1e24-105">Duyurular, hizmetlerin hizmetle ilgili meta verileri içeren duyuru iletileri göndermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1e24-105">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="a1e24-106">Varsayılan olarak, hizmet başlatıldığında bir Hello duyurusu gönderilir ve hizmet kapandığında bir bye duyurusu gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-106">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="a1e24-107">Bu duyurular çok noktaya yayın yapabilir veya noktadan noktaya gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-107">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="a1e24-108">Bu örnek iki proje hizmetinden ve istemcisinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a1e24-108">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="a1e24-109">Hizmet</span><span class="sxs-lookup"><span data-stu-id="a1e24-109">Service</span></span>

<span data-ttu-id="a1e24-110">Bu proje, şirket içinde barındırılan bir Hesaplayıcı hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-110">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="a1e24-111">`Main`Yönteminde bir hizmet ana bilgisayarı oluşturulur ve buna bir hizmet uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-111">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="a1e24-112">Ardından, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a1e24-112">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="a1e24-113">Duyuruları etkinleştirmek için, ' a bir duyuru uç noktası eklenmelidir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .</span><span class="sxs-lookup"><span data-stu-id="a1e24-113">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="a1e24-114">Bu durumda, UDP çok noktaya yayın kullanan standart bir uç nokta, duyuru uç noktası olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-114">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="a1e24-115">Bu, duyuruları iyi bilinen bir UDP adresi üzerinden yayınlar.</span><span class="sxs-lookup"><span data-stu-id="a1e24-115">This broadcasts the announcements over a well-known UDP address.</span></span>

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

## <a name="client"></a><span data-ttu-id="a1e24-116">İstemci</span><span class="sxs-lookup"><span data-stu-id="a1e24-116">Client</span></span>

<span data-ttu-id="a1e24-117">Bu projede, istemcisinin bir barındırdığını unutmayın <xref:System.ServiceModel.Discovery.AnnouncementService> .</span><span class="sxs-lookup"><span data-stu-id="a1e24-117">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="a1e24-118">Ayrıca, iki temsilci olaylar ile kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-118">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="a1e24-119">Bu olaylar, çevrimiçi ve çevrimdışı Duyurular alındığında istemcinin ne yaptığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a1e24-119">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="a1e24-120">`OnOnlineEvent`Ve `OnOfflineEvent` yöntemleri sırasıyla Merhaba ve bye bildiri iletilerini işler.</span><span class="sxs-lookup"><span data-stu-id="a1e24-120">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="a1e24-121">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a1e24-121">To use this sample</span></span>

1. <span data-ttu-id="a1e24-122">Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-122">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="a1e24-123">Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="a1e24-123">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="a1e24-124">Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-124">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="a1e24-125">Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1e24-125">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="a1e24-126">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="a1e24-126">Build the solution.</span></span>

3. <span data-ttu-id="a1e24-127">client.exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1e24-127">Run the client.exe application.</span></span>

4. <span data-ttu-id="a1e24-128">service.exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1e24-128">Run the service.exe application.</span></span> <span data-ttu-id="a1e24-129">İstemcinin bir çevrimiçi duyuru aldığını aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="a1e24-129">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="a1e24-130">service.exe uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="a1e24-130">Close the service.exe application.</span></span> <span data-ttu-id="a1e24-131">İstemcinin çevrimdışı bir duyuru aldığını aklınızda bırakın.</span><span class="sxs-lookup"><span data-stu-id="a1e24-131">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1e24-132">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1e24-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1e24-133">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a1e24-133">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a1e24-134">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a1e24-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1e24-135">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a1e24-135">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
