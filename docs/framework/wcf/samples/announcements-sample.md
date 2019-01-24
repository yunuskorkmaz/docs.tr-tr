---
title: Duyuru Örnekleri
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 775a56f322636664b5a0ced19df7bba347002e38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568575"
---
# <a name="announcements-sample"></a><span data-ttu-id="a72e7-102">Duyuru Örnekleri</span><span class="sxs-lookup"><span data-stu-id="a72e7-102">Announcements Sample</span></span>
<span data-ttu-id="a72e7-103">Bu örnek bulma özelliğinin duyuru işlevini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="a72e7-104">Duyurular hizmeti hakkında meta veriler içeren bir Duyurunun ileti göndermek için izin verin.</span><span class="sxs-lookup"><span data-stu-id="a72e7-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="a72e7-105">Varsayılan olarak, hizmet başlatıldığı ve hizmet kapatıldığında bye duyuru gönderilir hello duyuru gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="a72e7-106">Bu duyurular çok noktaya yayın veya noktadan noktaya gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="a72e7-107">Bu örnek, iki proje hizmeti ve istemci oluşur.</span><span class="sxs-lookup"><span data-stu-id="a72e7-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="a72e7-108">Hizmet</span><span class="sxs-lookup"><span data-stu-id="a72e7-108">Service</span></span>  
 <span data-ttu-id="a72e7-109">Bu proje, şirket içinde barındırılan hesaplayıcı hizmet içerir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="a72e7-110">İçinde `Main` yöntemi, bir hizmet konağı oluşturulur ve bir hizmet uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="a72e7-111">Ardından, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a72e7-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="a72e7-112">Duyurular etkinleştirmek için bir Duyurunun bitiş noktası eklenmelidir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a72e7-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="a72e7-113">Bu durumda UDP çok noktaya yayın kullanarak bir standart uç nokta duyuru uç noktası olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="a72e7-114">Bu, iyi bilinen bir UDP adresi duyurularını yayınlar.</span><span class="sxs-lookup"><span data-stu-id="a72e7-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="a72e7-115">İstemci</span><span class="sxs-lookup"><span data-stu-id="a72e7-115">Client</span></span>  
 <span data-ttu-id="a72e7-116">Bu projede unutmayın istemci konakları bir <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="a72e7-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="a72e7-117">Ayrıca, iki temsilci olduğunda olayları ile kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="a72e7-118">Bu olayları, istemcinin çevrimiçi ve çevrimdışı duyuruları alındığında ne yaptığını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```csharp
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="a72e7-119">`OnOnlineEvent` Ve `OnOfflineEvent` yöntemleri işleyen Merhaba ve bye duyuru iletileri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="a72e7-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a72e7-120">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a72e7-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="a72e7-121">Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="a72e7-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="a72e7-122">Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a72e7-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="a72e7-123">Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler yerine etki alanı ve kullanıcı adı isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a72e7-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="a72e7-124">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a72e7-124">Build the solution.</span></span>  
  
3.  <span data-ttu-id="a72e7-125">Client.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a72e7-125">Run the client.exe application.</span></span>  
  
4.  <span data-ttu-id="a72e7-126">Service.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a72e7-126">Run the service.exe application.</span></span> <span data-ttu-id="a72e7-127">İstemci çevrimiçi duyuruyu alır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a72e7-127">Note the client receives an online announcement.</span></span>  
  
5.  <span data-ttu-id="a72e7-128">Service.exe uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="a72e7-128">Close the service.exe application.</span></span> <span data-ttu-id="a72e7-129">Not istemci çevrimdışı duyuruyu alır.</span><span class="sxs-lookup"><span data-stu-id="a72e7-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a72e7-130">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="a72e7-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a72e7-131">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a72e7-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a72e7-132">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a72e7-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a72e7-133">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a72e7-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a><span data-ttu-id="a72e7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a72e7-134">See also</span></span>
