---
title: Intranet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 2fa13a12a377cc16a95318367605d8b5d92769a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184694"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="624fd-102">Intranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="624fd-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="624fd-103">Aşağıdaki resimde, bir WCF uygulamasına güvenli bir özel ağ hakkında bilgi sağlamak için geliştirilen basit bir Windows Communication Foundation (WCF) hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="624fd-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="624fd-104">Veriler düşük öneme sahip olduğundan, ağın doğal olarak güvenli olması veya güvenliğin WCF altyapısının altındaki bir katman tarafından sağlandığı için güvenlik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="624fd-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Intranet güvenli olmayan istemci ve hizmet senaryosu.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="624fd-106">Özellik</span><span class="sxs-lookup"><span data-stu-id="624fd-106">Characteristic</span></span>|<span data-ttu-id="624fd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="624fd-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="624fd-108">Güvenlik Modu</span><span class="sxs-lookup"><span data-stu-id="624fd-108">Security Mode</span></span>|<span data-ttu-id="624fd-109">None</span><span class="sxs-lookup"><span data-stu-id="624fd-109">None</span></span>|  
|<span data-ttu-id="624fd-110">Aktarım</span><span class="sxs-lookup"><span data-stu-id="624fd-110">Transport</span></span>|<span data-ttu-id="624fd-111">TCP</span><span class="sxs-lookup"><span data-stu-id="624fd-111">TCP</span></span>|  
|<span data-ttu-id="624fd-112">Bağlama</span><span class="sxs-lookup"><span data-stu-id="624fd-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="624fd-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="624fd-113">Interoperability</span></span>|<span data-ttu-id="624fd-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="624fd-114">WCF only</span></span>|  
|<span data-ttu-id="624fd-115">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="624fd-115">Authentication</span></span>|<span data-ttu-id="624fd-116">None</span><span class="sxs-lookup"><span data-stu-id="624fd-116">None</span></span>|  
|<span data-ttu-id="624fd-117">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="624fd-117">Integrity</span></span>|<span data-ttu-id="624fd-118">None</span><span class="sxs-lookup"><span data-stu-id="624fd-118">None</span></span>|  
|<span data-ttu-id="624fd-119">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="624fd-119">Confidentiality</span></span>|<span data-ttu-id="624fd-120">None</span><span class="sxs-lookup"><span data-stu-id="624fd-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="624fd-121">Hizmet</span><span class="sxs-lookup"><span data-stu-id="624fd-121">Service</span></span>  
 <span data-ttu-id="624fd-122">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="624fd-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="624fd-123">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="624fd-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="624fd-124">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="624fd-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="624fd-125">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="624fd-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="624fd-126">Kod</span><span class="sxs-lookup"><span data-stu-id="624fd-126">Code</span></span>  
 <span data-ttu-id="624fd-127">Aşağıdaki kod, güvenlik olmadan bir bitiş noktasının nasıl oluşturulabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="624fd-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="624fd-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="624fd-128">Configuration</span></span>  
 <span data-ttu-id="624fd-129">Aşağıdaki kod yapılandırmayı kullanarak aynı bitiş noktasını ayarlar:</span><span class="sxs-lookup"><span data-stu-id="624fd-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="624fd-130">İstemci</span><span class="sxs-lookup"><span data-stu-id="624fd-130">Client</span></span>  
 <span data-ttu-id="624fd-131">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="624fd-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="624fd-132">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="624fd-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="624fd-133">Kodu (ve istemci kodunu) kullanarak tek başına bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="624fd-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="624fd-134">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="624fd-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="624fd-135">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="624fd-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="624fd-136">Örnek:</span><span class="sxs-lookup"><span data-stu-id="624fd-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="624fd-137">Kod</span><span class="sxs-lookup"><span data-stu-id="624fd-137">Code</span></span>  
 <span data-ttu-id="624fd-138">Aşağıdaki kod, TCP protokolünü kullanarak güvenli olmayan bir bitiş noktasına erişen temel bir WCF istemcisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="624fd-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="624fd-139">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="624fd-139">Configuration</span></span>  
 <span data-ttu-id="624fd-140">Aşağıdaki yapılandırma kodu istemci için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="624fd-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="624fd-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="624fd-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="624fd-142">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="624fd-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="624fd-143">[Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="624fd-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
