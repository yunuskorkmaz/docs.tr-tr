---
title: İnternet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 017744d692d6fd4183fde3c21e71fcee2f35844e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535364"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="e448c-102">İnternet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="e448c-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="e448c-103">Aşağıdaki çizimde, genel, güvenli olmayan Windows Communication Foundation (WCF) istemci ve hizmeti örneği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e448c-103">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Güvenli olmayan bir Internet senaryosunu gösteren ekran görüntüsü](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="e448c-105">Özellik</span><span class="sxs-lookup"><span data-stu-id="e448c-105">Characteristic</span></span>|<span data-ttu-id="e448c-106">Description</span><span class="sxs-lookup"><span data-stu-id="e448c-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e448c-107">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="e448c-107">Security Mode</span></span>|<span data-ttu-id="e448c-108">Yok</span><span class="sxs-lookup"><span data-stu-id="e448c-108">None</span></span>|  
|<span data-ttu-id="e448c-109">Aktarım</span><span class="sxs-lookup"><span data-stu-id="e448c-109">Transport</span></span>|<span data-ttu-id="e448c-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="e448c-110">HTTP</span></span>|  
|<span data-ttu-id="e448c-111">Bağlama</span><span class="sxs-lookup"><span data-stu-id="e448c-111">Binding</span></span>|<span data-ttu-id="e448c-112"><xref:System.ServiceModel.BasicHttpBinding> kodda veya [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) yapılandırmadaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="e448c-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="e448c-113">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e448c-113">Interoperability</span></span>|<span data-ttu-id="e448c-114">Mevcut Web hizmeti istemcileri ve hizmetleriyle</span><span class="sxs-lookup"><span data-stu-id="e448c-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="e448c-115">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e448c-115">Authentication</span></span>|<span data-ttu-id="e448c-116">Yok</span><span class="sxs-lookup"><span data-stu-id="e448c-116">None</span></span>|  
|<span data-ttu-id="e448c-117">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="e448c-117">Integrity</span></span>|<span data-ttu-id="e448c-118">Yok</span><span class="sxs-lookup"><span data-stu-id="e448c-118">None</span></span>|  
|<span data-ttu-id="e448c-119">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="e448c-119">Confidentiality</span></span>|<span data-ttu-id="e448c-120">Yok</span><span class="sxs-lookup"><span data-stu-id="e448c-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="e448c-121">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e448c-121">Service</span></span>  
 <span data-ttu-id="e448c-122">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e448c-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e448c-123">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e448c-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="e448c-124">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e448c-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="e448c-125">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e448c-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e448c-126">Kod</span><span class="sxs-lookup"><span data-stu-id="e448c-126">Code</span></span>  
 <span data-ttu-id="e448c-127">Aşağıdaki kod, güvenliği olmayan bir uç noktanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e448c-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="e448c-128">Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> güvenlik modu olarak ayarlanır <xref:System.ServiceModel.BasicHttpSecurityMode.None> .</span><span class="sxs-lookup"><span data-stu-id="e448c-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="e448c-129">Hizmet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e448c-129">Service Configuration</span></span>  
 <span data-ttu-id="e448c-130">Aşağıdaki kod, yapılandırma kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e448c-130">The following code sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="e448c-131">İstemci</span><span class="sxs-lookup"><span data-stu-id="e448c-131">Client</span></span>  
 <span data-ttu-id="e448c-132">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e448c-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e448c-133">Şunlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e448c-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="e448c-134">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="e448c-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="e448c-135">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e448c-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e448c-136">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e448c-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e448c-137">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e448c-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="e448c-138">Kod</span><span class="sxs-lookup"><span data-stu-id="e448c-138">Code</span></span>  
 <span data-ttu-id="e448c-139">Aşağıdaki kod, güvenli olmayan bir uç noktaya erişen temel bir WCF istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e448c-139">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="e448c-140">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e448c-140">Client Configuration</span></span>  
 <span data-ttu-id="e448c-141">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e448c-141">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e448c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e448c-142">See also</span></span>

- [<span data-ttu-id="e448c-143">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="e448c-143">Common Security Scenarios</span></span>](common-security-scenarios.md)
- [<span data-ttu-id="e448c-144">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="e448c-144">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="e448c-145">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e448c-145">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
