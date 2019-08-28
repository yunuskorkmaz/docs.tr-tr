---
title: WCF Hizmetleri için Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 57aa92eb0a2978ab463c368ed70fb298cc5fb90d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038869"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="04c57-102">WCF Hizmetleri için Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04c57-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="04c57-103">Bu örnek, Windows Communication Foundation (WCF) kullanarak tipik bir hizmetin ve istemcinin nasıl uygulanacağını ve yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="04c57-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="04c57-104">Bu örnek, diğer tüm temel teknoloji örnekleri için temeldir.</span><span class="sxs-lookup"><span data-stu-id="04c57-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="04c57-105">Hizmet ile iletişim kurmak için bir uç nokta sunan bu hizmet, içindeki [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]Basitleştirilmiş yapılandırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="04c57-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="04c57-106">[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]Öncesinde, uç nokta genellikle aşağıdaki örnek yapılandırma kodunda gösterildiği gibi bir yapılandırma dosyasında (Web. config) tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="04c57-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="04c57-107">' De [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], öğesiisteğebağlıdır.`<service>`</span><span class="sxs-lookup"><span data-stu-id="04c57-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="04c57-108">Bir hizmet herhangi bir uç nokta tanımlamıyorsa, uygulanan her temel adres ve sözleşme için bir uç nokta hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="04c57-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="04c57-109">Bitiş noktasını ve bağlamanın adres düzeni tarafından belirlendiği temel adres, sözleşmenin adına eklenir.</span><span class="sxs-lookup"><span data-stu-id="04c57-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="04c57-110">Aşağıdaki kod örneği, Basitleştirilmiş bir yapılandırma dosyasını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="04c57-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="04c57-111">Yapılandırıldığı gibi, hizmete aynı bilgisayardaki bir istemci `http://localhost/servicemodelsamples/service.svc` tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="04c57-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="04c57-112">Uzak bilgisayarlardaki istemcilerin hizmete erişmesi için localhost yerine tam etki alanı adı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="04c57-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="04c57-113">Hizmet varsayılan olarak meta verileri kullanıma sunmaz.</span><span class="sxs-lookup"><span data-stu-id="04c57-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="04c57-114">Bu nedenle hizmet, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> davranışı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="04c57-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="04c57-115">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="04c57-115">To use this sample</span></span>  
  
1. <span data-ttu-id="04c57-116">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="04c57-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="04c57-117">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="04c57-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="04c57-118">Aşağıdaki adımları izleyerek örneği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="04c57-118">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="04c57-119">**Hizmet** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin ve ardından **CTRL + F5**tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="04c57-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="04c57-120">Hizmetin çalışır olduğunu onaylayan konsol çıkışının tamamlanmasını bekleyin.</span><span class="sxs-lookup"><span data-stu-id="04c57-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="04c57-121">**İstemci** projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin ve ardından **CTRL + F5**tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="04c57-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="04c57-122">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="04c57-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="04c57-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="04c57-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="04c57-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="04c57-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04c57-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="04c57-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="04c57-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04c57-126">See also</span></span>

- [<span data-ttu-id="04c57-127">AppFabric yönetim örnekleri</span><span class="sxs-lookup"><span data-stu-id="04c57-127">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
- [<span data-ttu-id="04c57-128">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04c57-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
