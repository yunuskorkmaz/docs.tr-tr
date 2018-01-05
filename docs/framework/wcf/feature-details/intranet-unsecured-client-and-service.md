---
title: "Intranet Güvenli Olmayan Hizmet ve İstemci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
caps.latest.revision: "20"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 0cfd98d401921c47bd85f8d4089e3efb437ca6b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="5f8fd-102">Intranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="5f8fd-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="5f8fd-103">Basit bir aşağıdaki çizimde gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet geliştirilen özel bir ağda güvenli için bilgi sağlamak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-103">The following illustration depicts a simple [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service developed to provide information on a secure private network to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="5f8fd-104">Güvenlik gerekli değildir veri düşük önem düzeyi olduğundan, ağ doğası gereği güvenli olması bekleniyor veya güvenlik bir katman tarafından sağlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure.</span></span>  
  
 <span data-ttu-id="5f8fd-105">![Intranet güvenli olmayan istemci ve hizmet senaryo](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="5f8fd-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="5f8fd-106">Özelliği</span><span class="sxs-lookup"><span data-stu-id="5f8fd-106">Characteristic</span></span>|<span data-ttu-id="5f8fd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f8fd-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5f8fd-108">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="5f8fd-108">Security Mode</span></span>|<span data-ttu-id="5f8fd-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-109">None</span></span>|  
|<span data-ttu-id="5f8fd-110">Taşıma</span><span class="sxs-lookup"><span data-stu-id="5f8fd-110">Transport</span></span>|<span data-ttu-id="5f8fd-111">TCP</span><span class="sxs-lookup"><span data-stu-id="5f8fd-111">TCP</span></span>|  
|<span data-ttu-id="5f8fd-112">Bağlama</span><span class="sxs-lookup"><span data-stu-id="5f8fd-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="5f8fd-113">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="5f8fd-113">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="5f8fd-114">yalnızca</span><span class="sxs-lookup"><span data-stu-id="5f8fd-114"> only</span></span>|  
|<span data-ttu-id="5f8fd-115">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="5f8fd-115">Authentication</span></span>|<span data-ttu-id="5f8fd-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-116">None</span></span>|  
|<span data-ttu-id="5f8fd-117">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="5f8fd-117">Integrity</span></span>|<span data-ttu-id="5f8fd-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-118">None</span></span>|  
|<span data-ttu-id="5f8fd-119">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="5f8fd-119">Confidentiality</span></span>|<span data-ttu-id="5f8fd-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="5f8fd-121">Hizmet</span><span class="sxs-lookup"><span data-stu-id="5f8fd-121">Service</span></span>  
 <span data-ttu-id="5f8fd-122">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5f8fd-123">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5f8fd-124">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5f8fd-125">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5f8fd-126">Kod</span><span class="sxs-lookup"><span data-stu-id="5f8fd-126">Code</span></span>  
 <span data-ttu-id="5f8fd-127">Aşağıdaki kod ile herhangi bir güvenliğin bir uç nokta oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="5f8fd-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5f8fd-128">Configuration</span></span>  
 <span data-ttu-id="5f8fd-129">Aşağıdaki kod Yapılandırması'nı kullanarak aynı uç nokta ayarlamayı ayarlar:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="5f8fd-130">İstemci</span><span class="sxs-lookup"><span data-stu-id="5f8fd-130">Client</span></span>  
 <span data-ttu-id="5f8fd-131">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5f8fd-132">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5f8fd-133">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="5f8fd-134">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5f8fd-135">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5f8fd-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5f8fd-137">Kod</span><span class="sxs-lookup"><span data-stu-id="5f8fd-137">Code</span></span>  
 <span data-ttu-id="5f8fd-138">Aşağıdaki kod temel gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] TCP protokolü kullanılarak güvenli olmayan bir uç nokta erişen istemci.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-138">The following code shows a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="5f8fd-139">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5f8fd-139">Configuration</span></span>  
 <span data-ttu-id="5f8fd-140">Aşağıdaki yapılandırma kodunu istemciye uygular:</span><span class="sxs-lookup"><span data-stu-id="5f8fd-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f8fd-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f8fd-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="5f8fd-142">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5f8fd-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="5f8fd-143">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="5f8fd-143">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
