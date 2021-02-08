---
description: 'Daha fazla bilgi edinin: Internet güvenli olmayan Istemci ve hizmet'
title: İnternet Güvenli Olmayan Hizmet ve İstemci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 8b402b276c80b2e1c148de0837d8644aad7a2d4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802781"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="982ba-103">İnternet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="982ba-103">Internet Unsecured Client and Service</span></span>

<span data-ttu-id="982ba-104">Aşağıdaki çizimde, genel, güvenli olmayan Windows Communication Foundation (WCF) istemci ve hizmeti örneği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="982ba-104">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Güvenli olmayan bir Internet senaryosunu gösteren ekran görüntüsü](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="982ba-106">Özellik</span><span class="sxs-lookup"><span data-stu-id="982ba-106">Characteristic</span></span>|<span data-ttu-id="982ba-107">Description</span><span class="sxs-lookup"><span data-stu-id="982ba-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="982ba-108">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="982ba-108">Security Mode</span></span>|<span data-ttu-id="982ba-109">Yok</span><span class="sxs-lookup"><span data-stu-id="982ba-109">None</span></span>|  
|<span data-ttu-id="982ba-110">Aktarım</span><span class="sxs-lookup"><span data-stu-id="982ba-110">Transport</span></span>|<span data-ttu-id="982ba-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="982ba-111">HTTP</span></span>|  
|<span data-ttu-id="982ba-112">Bağlama</span><span class="sxs-lookup"><span data-stu-id="982ba-112">Binding</span></span>|<span data-ttu-id="982ba-113"><xref:System.ServiceModel.BasicHttpBinding> kodda veya [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) yapılandırmadaki öğesi.</span><span class="sxs-lookup"><span data-stu-id="982ba-113"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="982ba-114">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="982ba-114">Interoperability</span></span>|<span data-ttu-id="982ba-115">Mevcut Web hizmeti istemcileri ve hizmetleriyle</span><span class="sxs-lookup"><span data-stu-id="982ba-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="982ba-116">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="982ba-116">Authentication</span></span>|<span data-ttu-id="982ba-117">Yok</span><span class="sxs-lookup"><span data-stu-id="982ba-117">None</span></span>|  
|<span data-ttu-id="982ba-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="982ba-118">Integrity</span></span>|<span data-ttu-id="982ba-119">Yok</span><span class="sxs-lookup"><span data-stu-id="982ba-119">None</span></span>|  
|<span data-ttu-id="982ba-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="982ba-120">Confidentiality</span></span>|<span data-ttu-id="982ba-121">Yok</span><span class="sxs-lookup"><span data-stu-id="982ba-121">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="982ba-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="982ba-122">Service</span></span>  

 <span data-ttu-id="982ba-123">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="982ba-123">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="982ba-124">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="982ba-124">Do one of the following:</span></span>  
  
- <span data-ttu-id="982ba-125">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="982ba-125">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="982ba-126">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="982ba-126">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="982ba-127">Kod</span><span class="sxs-lookup"><span data-stu-id="982ba-127">Code</span></span>  

 <span data-ttu-id="982ba-128">Aşağıdaki kod, güvenliği olmayan bir uç noktanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="982ba-128">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="982ba-129">Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> güvenlik modu olarak ayarlanır <xref:System.ServiceModel.BasicHttpSecurityMode.None> .</span><span class="sxs-lookup"><span data-stu-id="982ba-129">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="982ba-130">Hizmet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="982ba-130">Service Configuration</span></span>  

 <span data-ttu-id="982ba-131">Aşağıdaki kod, yapılandırma kullanarak aynı uç noktayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="982ba-131">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="982ba-132">İstemci</span><span class="sxs-lookup"><span data-stu-id="982ba-132">Client</span></span>  

 <span data-ttu-id="982ba-133">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="982ba-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="982ba-134">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="982ba-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="982ba-135">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="982ba-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="982ba-136">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="982ba-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="982ba-137">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="982ba-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="982ba-138">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="982ba-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="982ba-139">Kod</span><span class="sxs-lookup"><span data-stu-id="982ba-139">Code</span></span>  

 <span data-ttu-id="982ba-140">Aşağıdaki kod, güvenli olmayan bir uç noktaya erişen temel bir WCF istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="982ba-140">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="982ba-141">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="982ba-141">Client Configuration</span></span>  

 <span data-ttu-id="982ba-142">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="982ba-142">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="982ba-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="982ba-143">See also</span></span>

- [<span data-ttu-id="982ba-144">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="982ba-144">Common Security Scenarios</span></span>](common-security-scenarios.md)
- [<span data-ttu-id="982ba-145">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="982ba-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="982ba-146">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="982ba-146">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
