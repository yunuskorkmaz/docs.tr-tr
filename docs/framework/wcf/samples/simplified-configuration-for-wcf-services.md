---
title: WCF Hizmetleri için Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: ebdf7ab62676bb0c8ac99a5335a3047fcdd5a9b3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482897"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="dedea-102">WCF Hizmetleri için Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dedea-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="dedea-103">Bu örnek nasıl uygulanacağını ve tipik hizmeti ve Windows Communication Foundation (WCF) kullanarak istemci yapılandırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="dedea-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="dedea-104">Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dedea-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="dedea-105">Basitleştirilmiş Yapılandırma hizmeti ile iletişim için bir uç noktasını kullanıma sunar, bu hizmeti kullanır [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dedea-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="dedea-106">Öncesinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], aşağıdaki örnek yapılandırma kodda gösterildiği gibi uç noktası genellikle bir yapılandırma dosyasında (Web.config) tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="dedea-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="dedea-107">İçinde [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` öğesi, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dedea-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="dedea-108">Ne zaman bir hizmet tanımlamıyor tüm uç noktalar, her bir temel adres ve uygulanan sözleşme için bir uç nokta eklenir hizmete.</span><span class="sxs-lookup"><span data-stu-id="dedea-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="dedea-109">Temel adres uç nokta belirlemek için sözleşme adına eklenir ve bağlama adres düzeni tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="dedea-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="dedea-110">Aşağıdaki kod örneği bir Basitleştirilmiş yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="dedea-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="dedea-111">Adresinden yapılandırıldığı gibi hizmet erişilebilen http://localhost/servicemodelsamples/service.svc aynı bilgisayarda bir istemci tarafından.</span><span class="sxs-lookup"><span data-stu-id="dedea-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="dedea-112">Hizmete erişmek istemciler için uzak bilgisayarlarda, localhost yerine bir tam etki alanı adı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="dedea-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="dedea-113">Hizmet meta verileri varsayılan olarak kullanıma sunmuyor.</span><span class="sxs-lookup"><span data-stu-id="dedea-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="dedea-114">Bu nedenle, hizmet açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı.</span><span class="sxs-lookup"><span data-stu-id="dedea-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="dedea-115">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dedea-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="dedea-116">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dedea-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="dedea-117">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dedea-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="dedea-118">Aşağıdaki adımları izleyerek örneği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dedea-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="dedea-119">Sağ tıklayın **hizmet** seçin ve proje **başlangıç projesi olarak ayarla**, tuşuna **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="dedea-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="dedea-120">Yedekleme hizmetinin olduğunu onaylamak ve çalışan konsol çıktısı için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="dedea-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="dedea-121">Sağ tıklayın **istemci** seçin ve proje **başlangıç projesi olarak ayarla**, tuşuna **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="dedea-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dedea-122">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="dedea-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dedea-123">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dedea-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dedea-124">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="dedea-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dedea-125">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dedea-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="dedea-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dedea-126">See Also</span></span>  
 [<span data-ttu-id="dedea-127">AppFabric Yönetimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="dedea-127">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)  
 [<span data-ttu-id="dedea-128">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dedea-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
