---
title: Duyuru Örnekleri
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: ee58a2fef970fa3e7936e2fc26a9e7fd31633347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500044"
---
# <a name="announcements-sample"></a><span data-ttu-id="845c9-102">Duyuru Örnekleri</span><span class="sxs-lookup"><span data-stu-id="845c9-102">Announcements Sample</span></span>
<span data-ttu-id="845c9-103">Bu örnek duyuru işlevselliğinin bulma özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="845c9-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="845c9-104">Duyurular, hizmet hakkındaki meta verileri içeren duyuru iletilerini göndermek hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="845c9-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="845c9-105">Varsayılan olarak, hizmet başlatıldığında ve hizmet kapatıldığında bye duyuru gönderilen hello duyuru gönderilir.</span><span class="sxs-lookup"><span data-stu-id="845c9-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="845c9-106">Noktadan noktaya gönderilen veya bu Duyurular çok noktaya yayın olabilir.</span><span class="sxs-lookup"><span data-stu-id="845c9-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="845c9-107">Bu örnek iki proje hizmet ve istemci oluşur.</span><span class="sxs-lookup"><span data-stu-id="845c9-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="845c9-108">Hizmet</span><span class="sxs-lookup"><span data-stu-id="845c9-108">Service</span></span>  
 <span data-ttu-id="845c9-109">Bu proje bir kendi kendini barındıran hesaplayıcı hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="845c9-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="845c9-110">İçinde `Main` yöntemi, bir hizmet ana bilgisayarı oluşturulur ve hizmet uç noktası için eklenir.</span><span class="sxs-lookup"><span data-stu-id="845c9-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="845c9-111">Ardından, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="845c9-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="845c9-112">Duyurular etkinleştirmek için bir duyuru uç noktası eklenmelidir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="845c9-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="845c9-113">Bu durumda çok noktaya yayın UDP kullanan standart bir uç nokta duyuru uç noktası olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="845c9-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="845c9-114">Bu, iyi bilinen bir UDP adresi duyuruları yayınlar.</span><span class="sxs-lookup"><span data-stu-id="845c9-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
```  
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
  
## <a name="client"></a><span data-ttu-id="845c9-115">İstemci</span><span class="sxs-lookup"><span data-stu-id="845c9-115">Client</span></span>  
 <span data-ttu-id="845c9-116">Bu projede unutmayın istemci konakları bir <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="845c9-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="845c9-117">Ayrıca, iki temsilciler olayı kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="845c9-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="845c9-118">Bu olaylar, çevrimiçi ve çevrimdışı duyuruları alındığında istemcinin ne yaptığını dikte.</span><span class="sxs-lookup"><span data-stu-id="845c9-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="845c9-119">`OnOnlineEvent` Ve `OnOfflineEvent` yöntemlerini işlemek hello ve bye duyuru iletileri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="845c9-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
```  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="845c9-120">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="845c9-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="845c9-121">Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="845c9-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="845c9-122">Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="845c9-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="845c9-123">Komut olduğu gibi çalışmazsa, etki alanı ve kullanıcı adı şu bağımsız değişkenleri yerine isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="845c9-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="845c9-124">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="845c9-124">Build the solution.</span></span>  
  
3.  <span data-ttu-id="845c9-125">Client.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="845c9-125">Run the client.exe application.</span></span>  
  
4.  <span data-ttu-id="845c9-126">Service.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="845c9-126">Run the service.exe application.</span></span> <span data-ttu-id="845c9-127">İstemci çevrimiçi duyuru alır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="845c9-127">Note the client receives an online announcement.</span></span>  
  
5.  <span data-ttu-id="845c9-128">Service.exe uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="845c9-128">Close the service.exe application.</span></span> <span data-ttu-id="845c9-129">Not istemci çevrimdışı duyuru alır.</span><span class="sxs-lookup"><span data-stu-id="845c9-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="845c9-130">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="845c9-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="845c9-131">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="845c9-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="845c9-132">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="845c9-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="845c9-133">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="845c9-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a><span data-ttu-id="845c9-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="845c9-134">See Also</span></span>
