---
title: Kullaıcı Adı İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 215d23be53fad330b6ab056af83ad907f207259e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386551"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="e05d5-102">Kullaıcı Adı İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e05d5-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="e05d5-103">Aşağıdaki çizimde, bir Windows Communication Foundation (WCF) hizmet ve istemci ileti düzeyi güvenliği kullanılarak güvenli gösterir.</span><span class="sxs-lookup"><span data-stu-id="e05d5-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="e05d5-104">Hizmet bir X.509 sertifikası ile doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="e05d5-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="e05d5-105">İstemci, bir kullanıcı adı ve parolasını kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="e05d5-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="e05d5-106">Örnek bir uygulama için bkz: [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="e05d5-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="e05d5-107">![İleti güvenliği kullanıcı adı kimlik doğrulaması kullanarak](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="e05d5-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="e05d5-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="e05d5-108">Characteristic</span></span>|<span data-ttu-id="e05d5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e05d5-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e05d5-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="e05d5-110">Security Mode</span></span>|<span data-ttu-id="e05d5-111">İleti</span><span class="sxs-lookup"><span data-stu-id="e05d5-111">Message</span></span>|  
|<span data-ttu-id="e05d5-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e05d5-112">Interoperability</span></span>|<span data-ttu-id="e05d5-113">Windows Communication Foundation (WCF) yalnızca</span><span class="sxs-lookup"><span data-stu-id="e05d5-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="e05d5-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="e05d5-114">Authentication (Server)</span></span>|<span data-ttu-id="e05d5-115">İlk anlaşma sunucu kimlik doğrulaması gerektirir</span><span class="sxs-lookup"><span data-stu-id="e05d5-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="e05d5-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="e05d5-116">Authentication (Client)</span></span>|<span data-ttu-id="e05d5-117">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="e05d5-117">User name/password</span></span>|  
|<span data-ttu-id="e05d5-118">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="e05d5-118">Integrity</span></span>|<span data-ttu-id="e05d5-119">Evet, paylaşılan bir güvenlik bağlamı kullanma</span><span class="sxs-lookup"><span data-stu-id="e05d5-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="e05d5-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="e05d5-120">Confidentiality</span></span>|<span data-ttu-id="e05d5-121">Evet, paylaşılan bir güvenlik bağlamı kullanma</span><span class="sxs-lookup"><span data-stu-id="e05d5-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="e05d5-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="e05d5-122">Transport</span></span>|<span data-ttu-id="e05d5-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="e05d5-123">HTTP</span></span>|  
|<span data-ttu-id="e05d5-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="e05d5-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="e05d5-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e05d5-125">Service</span></span>  
 <span data-ttu-id="e05d5-126">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="e05d5-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e05d5-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e05d5-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="e05d5-128">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e05d5-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="e05d5-129">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e05d5-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e05d5-130">Kod</span><span class="sxs-lookup"><span data-stu-id="e05d5-130">Code</span></span>  
 <span data-ttu-id="e05d5-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e05d5-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="e05d5-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e05d5-132">Configuration</span></span>  
 <span data-ttu-id="e05d5-133">Kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="e05d5-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"     
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">              
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="e05d5-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="e05d5-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="e05d5-135">Kod</span><span class="sxs-lookup"><span data-stu-id="e05d5-135">Code</span></span>  
 <span data-ttu-id="e05d5-136">Aşağıdaki kod, istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e05d5-136">The following code creates the client.</span></span> <span data-ttu-id="e05d5-137">İleti modu güvenlik bağlamadır ve istemci kimlik bilgisi türü `UserName`.</span><span class="sxs-lookup"><span data-stu-id="e05d5-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="e05d5-138">Kullanıcı adı ve parola yalnızca kod (yapılandırılabilir değildir) kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e05d5-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="e05d5-139">Kullanıcı adını ve parolasını döndürmek için kodu, uygulama düzeyinde yapılması gerekir çünkü burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="e05d5-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="e05d5-140">Örneğin, kullanıcıdan veri sorgulamak için bir Windows Forms iletişim kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e05d5-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="e05d5-141">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e05d5-141">Configuration</span></span>  
 <span data-ttu-id="e05d5-142">Aşağıdaki kod, istemciyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e05d5-142">The following code configures the client.</span></span> <span data-ttu-id="e05d5-143">İleti modu güvenlik bağlamadır ve istemci kimlik bilgisi türü `UserName`.</span><span class="sxs-lookup"><span data-stu-id="e05d5-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="e05d5-144">Kullanıcı adı ve parola yalnızca kod (yapılandırılabilir değildir) kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e05d5-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
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
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e05d5-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e05d5-145">See Also</span></span>  
 [<span data-ttu-id="e05d5-146">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e05d5-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e05d5-147">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="e05d5-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [<span data-ttu-id="e05d5-148">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="e05d5-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="e05d5-149">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="e05d5-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [<span data-ttu-id="e05d5-150">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="e05d5-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
