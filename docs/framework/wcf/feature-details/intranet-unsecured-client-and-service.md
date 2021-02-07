---
description: 'Daha fazla bilgi edinin: Intranet güvenli olmayan Istemci ve hizmet'
title: Intranet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: a03abc5b8eb0317c4d5d19347b3974d615570069
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704530"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="b26fc-103">Intranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="b26fc-103">Intranet Unsecured Client and Service</span></span>

<span data-ttu-id="b26fc-104">Aşağıdaki çizimde, bir WCF uygulamasına güvenli bir özel ağ hakkında bilgi sağlamak için geliştirilen basit bir Windows Communication Foundation (WCF) hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b26fc-104">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="b26fc-105">Veriler düşük öneme sahip olduğundan, ağın kendiliğinden güvenli olması beklendiğinden ve güvenlik, WCF altyapısının altındaki bir katman tarafından sağlandığı için güvenlik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b26fc-105">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Intranet güvenli olmayan istemci ve hizmet senaryosu.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="b26fc-107">Özellik</span><span class="sxs-lookup"><span data-stu-id="b26fc-107">Characteristic</span></span>|<span data-ttu-id="b26fc-108">Description</span><span class="sxs-lookup"><span data-stu-id="b26fc-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b26fc-109">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="b26fc-109">Security Mode</span></span>|<span data-ttu-id="b26fc-110">Yok</span><span class="sxs-lookup"><span data-stu-id="b26fc-110">None</span></span>|  
|<span data-ttu-id="b26fc-111">Aktarım</span><span class="sxs-lookup"><span data-stu-id="b26fc-111">Transport</span></span>|<span data-ttu-id="b26fc-112">TCP</span><span class="sxs-lookup"><span data-stu-id="b26fc-112">TCP</span></span>|  
|<span data-ttu-id="b26fc-113">Bağlama</span><span class="sxs-lookup"><span data-stu-id="b26fc-113">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="b26fc-114">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="b26fc-114">Interoperability</span></span>|<span data-ttu-id="b26fc-115">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="b26fc-115">WCF only</span></span>|  
|<span data-ttu-id="b26fc-116">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b26fc-116">Authentication</span></span>|<span data-ttu-id="b26fc-117">Yok</span><span class="sxs-lookup"><span data-stu-id="b26fc-117">None</span></span>|  
|<span data-ttu-id="b26fc-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="b26fc-118">Integrity</span></span>|<span data-ttu-id="b26fc-119">Yok</span><span class="sxs-lookup"><span data-stu-id="b26fc-119">None</span></span>|  
|<span data-ttu-id="b26fc-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="b26fc-120">Confidentiality</span></span>|<span data-ttu-id="b26fc-121">Yok</span><span class="sxs-lookup"><span data-stu-id="b26fc-121">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="b26fc-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="b26fc-122">Service</span></span>  

 <span data-ttu-id="b26fc-123">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b26fc-123">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b26fc-124">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="b26fc-124">Do one of the following:</span></span>  
  
- <span data-ttu-id="b26fc-125">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b26fc-125">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="b26fc-126">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b26fc-126">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b26fc-127">Kod</span><span class="sxs-lookup"><span data-stu-id="b26fc-127">Code</span></span>  

 <span data-ttu-id="b26fc-128">Aşağıdaki kod, güvenliği olmayan bir uç noktanın nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="b26fc-128">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="b26fc-129">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b26fc-129">Configuration</span></span>  

 <span data-ttu-id="b26fc-130">Aşağıdaki kod, yapılandırma kullanarak aynı uç noktayı ayarlar:</span><span class="sxs-lookup"><span data-stu-id="b26fc-130">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="b26fc-131">İstemci</span><span class="sxs-lookup"><span data-stu-id="b26fc-131">Client</span></span>  

 <span data-ttu-id="b26fc-132">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b26fc-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b26fc-133">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="b26fc-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="b26fc-134">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="b26fc-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="b26fc-135">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b26fc-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b26fc-136">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b26fc-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b26fc-137">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b26fc-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b26fc-138">Kod</span><span class="sxs-lookup"><span data-stu-id="b26fc-138">Code</span></span>  

 <span data-ttu-id="b26fc-139">Aşağıdaki kod, TCP protokolünü kullanarak güvenli olmayan bir uç noktaya erişen temel bir WCF istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b26fc-139">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="b26fc-140">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b26fc-140">Configuration</span></span>  

 <span data-ttu-id="b26fc-141">Aşağıdaki yapılandırma kodu istemci için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="b26fc-141">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b26fc-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b26fc-142">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="b26fc-143">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="b26fc-143">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b26fc-144">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b26fc-144">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
