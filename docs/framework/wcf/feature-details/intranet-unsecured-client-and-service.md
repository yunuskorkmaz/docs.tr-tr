---
title: Intranet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 540c0fe5c4d06ea341b9cc8be9755cc67fe9bbc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039110"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="4e927-102">Intranet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="4e927-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="4e927-103">WCF uygulaması için özel bir güvenli ağ üzerinden bilgi sağlamak için geliştirilmiş basit bir Windows Communication Foundation (WCF) hizmeti aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4e927-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="4e927-104">Güvenlik, verileri düşük önem derecesi olduğundan, ağ doğası gereği güvenli olması beklenir veya WCF altyapısı aşağıdaki katman tarafından sağlanan güvenlik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4e927-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![İntranet güvenli olmayan istemci ve hizmet senaryo.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="4e927-106">Özelliği</span><span class="sxs-lookup"><span data-stu-id="4e927-106">Characteristic</span></span>|<span data-ttu-id="4e927-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e927-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4e927-108">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="4e927-108">Security Mode</span></span>|<span data-ttu-id="4e927-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e927-109">None</span></span>|  
|<span data-ttu-id="4e927-110">Taşıma</span><span class="sxs-lookup"><span data-stu-id="4e927-110">Transport</span></span>|<span data-ttu-id="4e927-111">TCP</span><span class="sxs-lookup"><span data-stu-id="4e927-111">TCP</span></span>|  
|<span data-ttu-id="4e927-112">Bağlama</span><span class="sxs-lookup"><span data-stu-id="4e927-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="4e927-113">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="4e927-113">Interoperability</span></span>|<span data-ttu-id="4e927-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="4e927-114">WCF only</span></span>|  
|<span data-ttu-id="4e927-115">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4e927-115">Authentication</span></span>|<span data-ttu-id="4e927-116">None</span><span class="sxs-lookup"><span data-stu-id="4e927-116">None</span></span>|  
|<span data-ttu-id="4e927-117">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="4e927-117">Integrity</span></span>|<span data-ttu-id="4e927-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e927-118">None</span></span>|  
|<span data-ttu-id="4e927-119">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="4e927-119">Confidentiality</span></span>|<span data-ttu-id="4e927-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="4e927-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="4e927-121">Hizmet</span><span class="sxs-lookup"><span data-stu-id="4e927-121">Service</span></span>  
 <span data-ttu-id="4e927-122">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="4e927-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4e927-123">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="4e927-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="4e927-124">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e927-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="4e927-125">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4e927-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4e927-126">Kod</span><span class="sxs-lookup"><span data-stu-id="4e927-126">Code</span></span>  
 <span data-ttu-id="4e927-127">Aşağıdaki kod, bir uç nokta ile herhangi bir güvenliğin oluşturma işlemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4e927-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="4e927-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4e927-128">Configuration</span></span>  
 <span data-ttu-id="4e927-129">Aşağıdaki kod, yapılandırma'yı kullanarak aynı uç noktasını ayarlar:</span><span class="sxs-lookup"><span data-stu-id="4e927-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="4e927-130">İstemci</span><span class="sxs-lookup"><span data-stu-id="4e927-130">Client</span></span>  
 <span data-ttu-id="4e927-131">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="4e927-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="4e927-132">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="4e927-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="4e927-133">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e927-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="4e927-134">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e927-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="4e927-135">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e927-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="4e927-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4e927-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="4e927-137">Kod</span><span class="sxs-lookup"><span data-stu-id="4e927-137">Code</span></span>  
 <span data-ttu-id="4e927-138">Aşağıdaki kod TCP protokolünü kullanarak güvenli bir uç nokta erişen temel bir WCF istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e927-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="4e927-139">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4e927-139">Configuration</span></span>  
 <span data-ttu-id="4e927-140">Aşağıdaki yapılandırma kodunu istemciye uygular:</span><span class="sxs-lookup"><span data-stu-id="4e927-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e927-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e927-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="4e927-142">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e927-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="4e927-143">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="4e927-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
