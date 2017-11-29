---
title: "Anonim İstemci ile İleti Güvenliği"
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
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: edf1dd36fe8c0f3e6c1ae8087d1bacbc00cf307a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="746ce-102">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="746ce-102">Message Security with an Anonymous Client</span></span>
<span data-ttu-id="746ce-103">Aşağıdaki senaryoda bir istemci ve hizmet tarafından güvenli hale getirilmiş gösterir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti güvenlik.</span><span class="sxs-lookup"><span data-stu-id="746ce-103">The following scenario shows a client and service secured by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message security.</span></span> <span data-ttu-id="746ce-104">Böylece gelecekte daha zengin bir talep tabanlı modeli destekleyebilir tasarım hedefi taşıma güvenliği yerine ileti güvenliği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="746ce-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="746ce-105">yetkilendirme için zengin talep kullanarak bkz [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="746ce-105"> using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="746ce-106">Örnek bir uygulama için bkz: [ileti güvenliği anonim](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="746ce-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>  
  
 <span data-ttu-id="746ce-107">![İleti anynymous istemci ile güvenliği](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="746ce-107">![Message security with an anynymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>  
  
|<span data-ttu-id="746ce-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="746ce-108">Characteristic</span></span>|<span data-ttu-id="746ce-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="746ce-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="746ce-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="746ce-110">Security Mode</span></span>|<span data-ttu-id="746ce-111">İleti</span><span class="sxs-lookup"><span data-stu-id="746ce-111">Message</span></span>|  
|<span data-ttu-id="746ce-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="746ce-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="746ce-113">yalnızca</span><span class="sxs-lookup"><span data-stu-id="746ce-113"> only</span></span>|  
|<span data-ttu-id="746ce-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="746ce-114">Authentication (Server)</span></span>|<span data-ttu-id="746ce-115">İlk anlaşma sunucu kimlik doğrulaması, ancak değil istemci kimlik doğrulaması gerektirir</span><span class="sxs-lookup"><span data-stu-id="746ce-115">Initial negotiation requires server authentication, but not client authentication</span></span>|  
|<span data-ttu-id="746ce-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="746ce-116">Authentication (Client)</span></span>|<span data-ttu-id="746ce-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="746ce-117">None</span></span>|  
|<span data-ttu-id="746ce-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="746ce-118">Integrity</span></span>|<span data-ttu-id="746ce-119">Evet, paylaşılan güvenlik bağlamını kullanarak</span><span class="sxs-lookup"><span data-stu-id="746ce-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="746ce-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="746ce-120">Confidentiality</span></span>|<span data-ttu-id="746ce-121">Evet, paylaşılan güvenlik bağlamını kullanarak</span><span class="sxs-lookup"><span data-stu-id="746ce-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="746ce-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="746ce-122">Transport</span></span>|<span data-ttu-id="746ce-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="746ce-123">HTTP</span></span>|  
  
## <a name="service"></a><span data-ttu-id="746ce-124">Hizmet</span><span class="sxs-lookup"><span data-stu-id="746ce-124">Service</span></span>  
 <span data-ttu-id="746ce-125">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="746ce-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="746ce-126">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="746ce-126">Do one of the following:</span></span>  
  
-   <span data-ttu-id="746ce-127">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="746ce-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="746ce-128">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="746ce-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="746ce-129">Kod</span><span class="sxs-lookup"><span data-stu-id="746ce-129">Code</span></span>  
 <span data-ttu-id="746ce-130">Aşağıdaki kod ileti güvenliği kullanan hizmet uç noktası oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="746ce-130">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a><span data-ttu-id="746ce-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="746ce-131">Configuration</span></span>  
 <span data-ttu-id="746ce-132">Aşağıdaki yapılandırma kodu yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="746ce-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="746ce-133">Hizmet davranışı öğesi istemci hizmete kimliğini doğrulamak için kullanılan bir sertifika belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="746ce-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="746ce-134">Hizmet öğesinin davranışını kullanarak belirtmelisiniz `behaviorConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="746ce-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="746ce-135">İstemci kimlik bilgisi türü olduğunu bağlama öğesi belirtir `None`, hizmeti kullanmak anonim istemcilerinin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="746ce-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="746ce-136">İstemci</span><span class="sxs-lookup"><span data-stu-id="746ce-136">Client</span></span>  
 <span data-ttu-id="746ce-137">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="746ce-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="746ce-138">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="746ce-138">Do one of the following:</span></span>  
  
-   <span data-ttu-id="746ce-139">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="746ce-139">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="746ce-140">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="746ce-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="746ce-141">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="746ce-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="746ce-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="746ce-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="746ce-143">Kod</span><span class="sxs-lookup"><span data-stu-id="746ce-143">Code</span></span>  
 <span data-ttu-id="746ce-144">Aşağıdaki kod, istemci bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="746ce-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="746ce-145">İleti mod güvenliği bağlama kullanır ve istemci kimlik bilgisi türü hiçbiri olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="746ce-145">The binding uses message mode security, and the client credential type is set to none.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a><span data-ttu-id="746ce-146">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="746ce-146">Configuration</span></span>  
 <span data-ttu-id="746ce-147">Aşağıdaki kod istemci yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="746ce-147">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_ICalculator"   
        contract="ICalculator"  
        name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="746ce-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="746ce-148">See Also</span></span>  
 [<span data-ttu-id="746ce-149">Güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="746ce-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="746ce-150">Dağıtılan uygulama güvenliği</span><span class="sxs-lookup"><span data-stu-id="746ce-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="746ce-151">İleti güvenliği anonim</span><span class="sxs-lookup"><span data-stu-id="746ce-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [<span data-ttu-id="746ce-152">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="746ce-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="746ce-153">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="746ce-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
