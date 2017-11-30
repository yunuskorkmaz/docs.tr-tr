---
title: "İnternet Güvenli Olmayan Hizmet ve İstemci"
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
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: cd7cc9da457424dede6f62ecefca8cee0d94fb88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="e5ce5-102">İnternet Güvenli Olmayan Hizmet ve İstemci</span><span class="sxs-lookup"><span data-stu-id="e5ce5-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="e5ce5-103">Aşağıdaki çizimde bir ortak bir örneği gösterilir güvenli [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci ve hizmet.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-103">The following illustration shows an example of a public, unsecured [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span>  
  
 <span data-ttu-id="e5ce5-104">![Güvenli olmayan Internet cleint ve hizmet senaryo](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span><span class="sxs-lookup"><span data-stu-id="e5ce5-104">![Unsecured Internet cleint and service scenario](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span></span>  
  
|<span data-ttu-id="e5ce5-105">Özelliği</span><span class="sxs-lookup"><span data-stu-id="e5ce5-105">Characteristic</span></span>|<span data-ttu-id="e5ce5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5ce5-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e5ce5-107">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="e5ce5-107">Security Mode</span></span>|<span data-ttu-id="e5ce5-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-108">None</span></span>|  
|<span data-ttu-id="e5ce5-109">Taşıma</span><span class="sxs-lookup"><span data-stu-id="e5ce5-109">Transport</span></span>|<span data-ttu-id="e5ce5-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="e5ce5-110">HTTP</span></span>|  
|<span data-ttu-id="e5ce5-111">Bağlama</span><span class="sxs-lookup"><span data-stu-id="e5ce5-111">Binding</span></span>|<span data-ttu-id="e5ce5-112"><xref:System.ServiceModel.BasicHttpBinding>kodda, veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) yapılandırma öğesinde.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="e5ce5-113">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e5ce5-113">Interoperability</span></span>|<span data-ttu-id="e5ce5-114">Mevcut Web hizmeti istemcileri ve Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e5ce5-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="e5ce5-115">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e5ce5-115">Authentication</span></span>|<span data-ttu-id="e5ce5-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-116">None</span></span>|  
|<span data-ttu-id="e5ce5-117">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="e5ce5-117">Integrity</span></span>|<span data-ttu-id="e5ce5-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-118">None</span></span>|  
|<span data-ttu-id="e5ce5-119">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="e5ce5-119">Confidentiality</span></span>|<span data-ttu-id="e5ce5-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="e5ce5-121">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e5ce5-121">Service</span></span>  
 <span data-ttu-id="e5ce5-122">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e5ce5-123">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e5ce5-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="e5ce5-124">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="e5ce5-125">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e5ce5-126">Kod</span><span class="sxs-lookup"><span data-stu-id="e5ce5-126">Code</span></span>  
 <span data-ttu-id="e5ce5-127">Aşağıdaki kod ile herhangi bir güvenliğin bir uç nokta oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="e5ce5-128">Varsayılan olarak, <xref:System.ServiceModel.BasicHttpBinding> sahip ayarlamak kullanılan güvenlik modunu <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="e5ce5-129">Hizmet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e5ce5-129">Service Configuration</span></span>  
 <span data-ttu-id="e5ce5-130">Aşağıdaki kod Yapılandırması'nı kullanarak aynı uç nokta ayarlamayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-130">The following code sets up the same endpoint using configuration.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="e5ce5-131">İstemci</span><span class="sxs-lookup"><span data-stu-id="e5ce5-131">Client</span></span>  
 <span data-ttu-id="e5ce5-132">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e5ce5-133">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e5ce5-133">Do one of the following:</span></span>  
  
-   <span data-ttu-id="e5ce5-134">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-134">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="e5ce5-135">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e5ce5-136">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e5ce5-137">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e5ce5-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="e5ce5-138">Kod</span><span class="sxs-lookup"><span data-stu-id="e5ce5-138">Code</span></span>  
 <span data-ttu-id="e5ce5-139">Aşağıdaki kod temel gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenli olmayan bir uç nokta erişen istemci.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-139">The following code shows a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="e5ce5-140">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e5ce5-140">Client Configuration</span></span>  
 <span data-ttu-id="e5ce5-141">Aşağıdaki kod istemci yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-141">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5ce5-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-142">See Also</span></span>  
 [<span data-ttu-id="e5ce5-143">Ortak Güvenlik senaryoları</span><span class="sxs-lookup"><span data-stu-id="e5ce5-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [<span data-ttu-id="e5ce5-144">Güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="e5ce5-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e5ce5-145">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="e5ce5-145">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
