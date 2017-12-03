---
title: "WCF Hizmetleri için Basitleştirilmiş Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6f0d73ba01ec51fe2fcd00f33bbd3183e382c74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="b193a-102">WCF Hizmetleri için Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b193a-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="b193a-103">Bu örnek, uygulama ve tipik hizmeti ve kullanarak istemci yapılandırma gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b193a-103">This sample demonstrates how to implement and configure a typical service and client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="b193a-104">Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b193a-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="b193a-105">Basitleştirilmiş yapılandırmada hizmet ile iletişim için bir uç noktasını kullanıma sunar, bu hizmeti kullanan [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b193a-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="b193a-106">Öncesinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], uç nokta yapılandırma dosyasında (Web.config) aşağıdaki örnek yapılandırma kodda gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b193a-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b193a-107">İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` öğesidir isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b193a-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="b193a-108">Ne zaman bir hizmet tanımlamıyor uç nokta, her bir temel adres ve uygulanan sözleşme için bir uç nokta eklenir hizmete.</span><span class="sxs-lookup"><span data-stu-id="b193a-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="b193a-109">Temel adres uç nokta belirlemek için sözleşme ada eklenir ve bağlama adres düzeni tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b193a-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="b193a-110">Aşağıdaki kod örneğinde bir Basitleştirilmiş yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="b193a-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="b193a-111">Yapılandırıldığı şekilde hizmet http://localhost/servicemodelsamples/service.svc aynı bilgisayara bir istemci tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b193a-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="b193a-112">Hizmete erişmek istemciler için uzak bilgisayarlarda, localhost yerine bir tam etki alanı adı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b193a-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="b193a-113">Hizmet meta verileri varsayılan olarak kullanıma sunmuyor.</span><span class="sxs-lookup"><span data-stu-id="b193a-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="b193a-114">Bu nedenle, hizmetin açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı.</span><span class="sxs-lookup"><span data-stu-id="b193a-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="b193a-115">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b193a-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="b193a-116">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b193a-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b193a-117">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b193a-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b193a-118">Örnek, aşağıdaki adımları izleyerek çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="b193a-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="b193a-119">Sağ tıklayın **hizmet** proje ve seçin **başlangıç projesi olarak ayarla**, tuşuna basarak **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b193a-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="b193a-120">Hizmetin çalışır durumda olduğunu onaylamak ve çalışan konsol çıktısı için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="b193a-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="b193a-121">Sağ tıklayın **istemci** proje ve seçin **başlangıç projesi olarak ayarla**, tuşuna basarak **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b193a-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b193a-122">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="b193a-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b193a-123">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b193a-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b193a-124">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b193a-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b193a-125">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b193a-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="b193a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b193a-126">See Also</span></span>  
 [<span data-ttu-id="b193a-127">AppFabric Yönetimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="b193a-127">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [<span data-ttu-id="b193a-128">Basitleştirilmiş yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b193a-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
