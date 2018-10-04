---
title: Intranet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
author: BrucePerlerMS
ms.openlocfilehash: e09f7c8483e1a3ca330bbee995c2d59f9005f207
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48265627"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="24f02-102">Intranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="24f02-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="24f02-103">WCF uygulaması için özel bir güvenli ağ üzerinden bilgi sağlamak için geliştirilmiş basit bir Windows Communication Foundation (WCF) hizmeti aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="24f02-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="24f02-104">Güvenlik, verileri düşük önem derecesi olduğundan, ağ doğası gereği güvenli olması beklenir veya WCF altyapısı aşağıdaki katman tarafından sağlanan güvenlik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="24f02-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 <span data-ttu-id="24f02-105">![İntranet güvenli olmayan istemci ve hizmet senaryo](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="24f02-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="24f02-106">Özelliği</span><span class="sxs-lookup"><span data-stu-id="24f02-106">Characteristic</span></span>|<span data-ttu-id="24f02-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24f02-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="24f02-108">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="24f02-108">Security Mode</span></span>|<span data-ttu-id="24f02-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="24f02-109">None</span></span>|  
|<span data-ttu-id="24f02-110">Taşıma</span><span class="sxs-lookup"><span data-stu-id="24f02-110">Transport</span></span>|<span data-ttu-id="24f02-111">TCP</span><span class="sxs-lookup"><span data-stu-id="24f02-111">TCP</span></span>|  
|<span data-ttu-id="24f02-112">Bağlama</span><span class="sxs-lookup"><span data-stu-id="24f02-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="24f02-113">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="24f02-113">Interoperability</span></span>|<span data-ttu-id="24f02-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="24f02-114">WCF only</span></span>|  
|<span data-ttu-id="24f02-115">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="24f02-115">Authentication</span></span>|<span data-ttu-id="24f02-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="24f02-116">None</span></span>|  
|<span data-ttu-id="24f02-117">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="24f02-117">Integrity</span></span>|<span data-ttu-id="24f02-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="24f02-118">None</span></span>|  
|<span data-ttu-id="24f02-119">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="24f02-119">Confidentiality</span></span>|<span data-ttu-id="24f02-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="24f02-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="24f02-121">Hizmet</span><span class="sxs-lookup"><span data-stu-id="24f02-121">Service</span></span>  
 <span data-ttu-id="24f02-122">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="24f02-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="24f02-123">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="24f02-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="24f02-124">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24f02-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="24f02-125">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="24f02-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="24f02-126">Kod</span><span class="sxs-lookup"><span data-stu-id="24f02-126">Code</span></span>  
 <span data-ttu-id="24f02-127">Aşağıdaki kod, bir uç nokta ile herhangi bir güvenliğin oluşturma işlemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="24f02-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="24f02-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="24f02-128">Configuration</span></span>  
 <span data-ttu-id="24f02-129">Aşağıdaki kod, yapılandırma'yı kullanarak aynı uç noktasını ayarlar:</span><span class="sxs-lookup"><span data-stu-id="24f02-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""   
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"   
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="24f02-130">İstemci</span><span class="sxs-lookup"><span data-stu-id="24f02-130">Client</span></span>  
 <span data-ttu-id="24f02-131">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="24f02-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="24f02-132">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="24f02-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="24f02-133">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24f02-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="24f02-134">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24f02-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="24f02-135">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="24f02-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="24f02-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="24f02-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="24f02-137">Kod</span><span class="sxs-lookup"><span data-stu-id="24f02-137">Code</span></span>  
 <span data-ttu-id="24f02-138">Aşağıdaki kod TCP protokolünü kullanarak güvenli bir uç nokta erişen temel bir WCF istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="24f02-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="24f02-139">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="24f02-139">Configuration</span></span>  
 <span data-ttu-id="24f02-140">Aşağıdaki yapılandırma kodunu istemciye uygular:</span><span class="sxs-lookup"><span data-stu-id="24f02-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"   
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"   
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24f02-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24f02-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="24f02-142">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="24f02-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="24f02-143">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="24f02-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
