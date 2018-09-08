---
title: Anonim İstemci ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d3e8269fc05caf70f4329ce8f13a3633a8982c0b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44173346"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="16318-102">Anonim İstemci ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="16318-102">Message Security with an Anonymous Client</span></span>
<span data-ttu-id="16318-103">Aşağıdaki senaryoda bir istemci ve Windows Communication Foundation (WCF) ileti güvenliği tarafından güvenliği sağlanan hizmet gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16318-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="16318-104">Gelecekte daha zengin bir beyana dayalı modeli destekleyebilir böylece tasarım hedefi aktarım güvenliği yerine ileti güvenliği kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="16318-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="16318-105">Yetkilendirme için zengin talep kullanma hakkında daha fazla bilgi için bkz. [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="16318-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="16318-106">Örnek bir uygulama için bkz: [ileti güvenliği anonim](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="16318-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>  
  
 <span data-ttu-id="16318-107">![Güvenlik anynymous istemci ile ileti](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="16318-107">![Message security with an anynymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>  
  
|<span data-ttu-id="16318-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="16318-108">Characteristic</span></span>|<span data-ttu-id="16318-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16318-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="16318-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="16318-110">Security Mode</span></span>|<span data-ttu-id="16318-111">İleti</span><span class="sxs-lookup"><span data-stu-id="16318-111">Message</span></span>|  
|<span data-ttu-id="16318-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="16318-112">Interoperability</span></span>|<span data-ttu-id="16318-113">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="16318-113">WCF only</span></span>|  
|<span data-ttu-id="16318-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="16318-114">Authentication (Server)</span></span>|<span data-ttu-id="16318-115">İlk anlaşma sunucu kimlik doğrulaması, ancak değil istemci kimlik doğrulaması gerektirir</span><span class="sxs-lookup"><span data-stu-id="16318-115">Initial negotiation requires server authentication, but not client authentication</span></span>|  
|<span data-ttu-id="16318-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="16318-116">Authentication (Client)</span></span>|<span data-ttu-id="16318-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="16318-117">None</span></span>|  
|<span data-ttu-id="16318-118">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="16318-118">Integrity</span></span>|<span data-ttu-id="16318-119">Evet, paylaşılan bir güvenlik bağlamı kullanma</span><span class="sxs-lookup"><span data-stu-id="16318-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="16318-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="16318-120">Confidentiality</span></span>|<span data-ttu-id="16318-121">Evet, paylaşılan bir güvenlik bağlamı kullanma</span><span class="sxs-lookup"><span data-stu-id="16318-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="16318-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="16318-122">Transport</span></span>|<span data-ttu-id="16318-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="16318-123">HTTP</span></span>|  
  
## <a name="service"></a><span data-ttu-id="16318-124">Hizmet</span><span class="sxs-lookup"><span data-stu-id="16318-124">Service</span></span>  
 <span data-ttu-id="16318-125">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="16318-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="16318-126">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="16318-126">Do one of the following:</span></span>  
  
-   <span data-ttu-id="16318-127">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16318-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="16318-128">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="16318-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="16318-129">Kod</span><span class="sxs-lookup"><span data-stu-id="16318-129">Code</span></span>  
 <span data-ttu-id="16318-130">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16318-130">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a><span data-ttu-id="16318-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="16318-131">Configuration</span></span>  
 <span data-ttu-id="16318-132">Aşağıdaki yapılandırmayı kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16318-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="16318-133">Hizmet davranışı öğesi hizmete istemcinin kimliğini doğrulamak için kullanılan bir sertifika belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16318-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="16318-134">Hizmet öğesi davranışını kullanarak belirtmelisiniz `behaviorConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="16318-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="16318-135">İstemci kimlik bilgisi türü olduğunu bağlama öğesi belirtir `None`, hizmeti kullanmak anonim istemcilere izin verme.</span><span class="sxs-lookup"><span data-stu-id="16318-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="16318-136">İstemci</span><span class="sxs-lookup"><span data-stu-id="16318-136">Client</span></span>  
 <span data-ttu-id="16318-137">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="16318-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="16318-138">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="16318-138">Do one of the following:</span></span>  
  
-   <span data-ttu-id="16318-139">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16318-139">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="16318-140">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16318-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="16318-141">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="16318-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="16318-142">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="16318-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="16318-143">Kod</span><span class="sxs-lookup"><span data-stu-id="16318-143">Code</span></span>  
 <span data-ttu-id="16318-144">Aşağıdaki kod, istemci bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="16318-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="16318-145">İleti modu güvenliği bağlama kullanır ve istemci kimlik bilgisi türü hiçbiri olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="16318-145">The binding uses message mode security, and the client credential type is set to none.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a><span data-ttu-id="16318-146">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="16318-146">Configuration</span></span>  
 <span data-ttu-id="16318-147">Aşağıdaki kod, istemciyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="16318-147">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16318-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16318-148">See Also</span></span>  
 [<span data-ttu-id="16318-149">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="16318-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="16318-150">Dağıtılan Uygulama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="16318-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="16318-151">İleti Güvenliği Anonim</span><span class="sxs-lookup"><span data-stu-id="16318-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [<span data-ttu-id="16318-152">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="16318-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="16318-153">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="16318-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
