---
title: Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: e6129594df6170f94a06caa08a9f16e4770bbfd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501461"
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="84fd5-102">Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği</span><span class="sxs-lookup"><span data-stu-id="84fd5-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="84fd5-103">Bu örnek, bir hizmet bulmak gösterilmiştir <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliğini <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span><span class="sxs-lookup"><span data-stu-id="84fd5-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="84fd5-104">Zaman <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.Description.ListenUriMode.Unique>, ListenUri güvence altına benzersiz olması için bağlantı noktası ayarlayarak veya yolun bir GUID ekleyerek benzersiz olması için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84fd5-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="84fd5-105">Hizmet Özellikleri</span><span class="sxs-lookup"><span data-stu-id="84fd5-105">Features on the Service</span></span>  
 <span data-ttu-id="84fd5-106"><xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Özelliği ayarlanmış <xref:System.ServiceModel.Description.ListenUriMode.Unique> TCP uç noktası için.</span><span class="sxs-lookup"><span data-stu-id="84fd5-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="84fd5-107">Hizmet ardından bulunabilirlik üzerinden yapılan bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası.</span><span class="sxs-lookup"><span data-stu-id="84fd5-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="84fd5-108">İstemci özellikleri</span><span class="sxs-lookup"><span data-stu-id="84fd5-108">Features on the Client</span></span>  
 <span data-ttu-id="84fd5-109">Bu istemci doğru kullanarak hizmete bağlanıyor `Via.Uri` kullanarak <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84fd5-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="84fd5-110"><xref:System.ServiceModel.Discovery.FindResponse> Sağlayıcıdan döndürülen yöntemi, sonra da geçerli bir içerip içermediğini için sorgulanır <xref:System.ServiceModel.Endpoint.ListenUri%2A> ve farklı olup `Address.Uri`.</span><span class="sxs-lookup"><span data-stu-id="84fd5-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="84fd5-111">Uygun bilgileri sonra geçirilir `InvokeCalculatorService` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84fd5-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="84fd5-112">İçinde `InvokeCalculatorService` yöntemi, <xref:System.ServiceModel.Endpoint.ListenUri%2A> çağıran tarafından geçirilen sonra bir `ClientViaBehavior` doğru ile `Via.Uri` istemcinin uç noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="84fd5-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="84fd5-113">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="84fd5-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="84fd5-114">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], UniqueListenUriMode.sln açın.</span><span class="sxs-lookup"><span data-stu-id="84fd5-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="84fd5-115">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="84fd5-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="84fd5-116">[Çözüm temel dizin] \service\bin\debug klasöründe oluşturulan hizmet uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="84fd5-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="84fd5-117">[Çözüm temel dizin] \Client\bin\debug klasöründe oluşturulan istemci uygulaması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="84fd5-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="84fd5-118">İstemci çalışan hizmetin bulur ve hizmetin uç noktası tarafından yayımlanan meta verileri konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="84fd5-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84fd5-119">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="84fd5-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="84fd5-120">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="84fd5-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="84fd5-121">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="84fd5-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84fd5-122">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="84fd5-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="84fd5-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84fd5-123">See Also</span></span>
