---
title: "Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 82f47fb0b789e41c332ebae2cfeaeb350ff0fddd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="2dd82-102">Benzersiz Dinleme Uri Modu ile Hizmet Keşfetme Örneği</span><span class="sxs-lookup"><span data-stu-id="2dd82-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="2dd82-103">Bu örnek, bir hizmet bulmak gösterilmiştir <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliğini <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span><span class="sxs-lookup"><span data-stu-id="2dd82-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="2dd82-104">Zaman <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.Description.ListenUriMode.Unique>, ListenUri güvence altına benzersiz olması için bağlantı noktası ayarlayarak veya yolun bir GUID ekleyerek benzersiz olması için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dd82-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="2dd82-105">Hizmet Özellikleri</span><span class="sxs-lookup"><span data-stu-id="2dd82-105">Features on the Service</span></span>  
 <span data-ttu-id="2dd82-106"><xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> Özelliği ayarlanmış <xref:System.ServiceModel.Description.ListenUriMode.Unique> TCP uç noktası için.</span><span class="sxs-lookup"><span data-stu-id="2dd82-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="2dd82-107">Hizmet ardından bulunabilirlik üzerinden yapılan bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası.</span><span class="sxs-lookup"><span data-stu-id="2dd82-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="2dd82-108">İstemci özellikleri</span><span class="sxs-lookup"><span data-stu-id="2dd82-108">Features on the Client</span></span>  
 <span data-ttu-id="2dd82-109">Bu istemci doğru kullanarak hizmete bağlanıyor `Via.Uri` kullanarak <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2dd82-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="2dd82-110"><xref:System.ServiceModel.Discovery.FindResponse> Sağlayıcıdan döndürülen yöntemi, sonra da geçerli bir içerip içermediğini için sorgulanır <xref:System.ServiceModel.Endpoint.ListenUri%2A> ve farklı olup `Address.Uri`.</span><span class="sxs-lookup"><span data-stu-id="2dd82-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="2dd82-111">Uygun bilgileri sonra geçirilir `InvokeCalculatorService` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2dd82-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="2dd82-112">İçinde `InvokeCalculatorService` yöntemi, <xref:System.ServiceModel.Endpoint.ListenUri%2A> çağıran tarafından geçirilen sonra bir `ClientViaBehavior` doğru ile `Via.Uri` istemcinin uç noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2dd82-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="2dd82-113">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="2dd82-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="2dd82-114">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], UniqueListenUriMode.sln açın.</span><span class="sxs-lookup"><span data-stu-id="2dd82-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="2dd82-115">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2dd82-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2dd82-116">[Çözüm temel dizin] \service\bin\debug klasöründe oluşturulan hizmet uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2dd82-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="2dd82-117">[Çözüm temel dizin] \Client\bin\debug klasöründe oluşturulan istemci uygulaması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2dd82-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="2dd82-118">İstemci çalışan hizmetin bulur ve hizmetin uç noktası tarafından yayımlanan meta verileri konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="2dd82-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2dd82-119">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2dd82-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2dd82-120">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2dd82-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2dd82-121">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2dd82-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2dd82-122">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2dd82-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="2dd82-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dd82-123">See Also</span></span>
