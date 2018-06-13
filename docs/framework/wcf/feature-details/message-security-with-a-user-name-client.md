---
title: Kullaıcı Adı İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7bda1bc18e2b5af1365c799c6f2be9d8d220e9ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495138"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="f5128-102">Kullaıcı Adı İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f5128-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="f5128-103">Aşağıdaki çizimde, bir Windows Communication Foundation (WCF) hizmetini ve ileti düzeyi güvenlik kullanılarak güvenli istemci gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5128-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="f5128-104">Hizmet bir X.509 sertifikası ile doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="f5128-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="f5128-105">İstemci, bir kullanıcı adı ve parola kullanarak kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="f5128-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="f5128-106">Örnek bir uygulama için bkz: [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="f5128-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="f5128-107">![Kullanıcı adı kimlik doğrulaması kullanarak ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="f5128-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="f5128-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="f5128-108">Characteristic</span></span>|<span data-ttu-id="f5128-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5128-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f5128-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="f5128-110">Security Mode</span></span>|<span data-ttu-id="f5128-111">İleti</span><span class="sxs-lookup"><span data-stu-id="f5128-111">Message</span></span>|  
|<span data-ttu-id="f5128-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f5128-112">Interoperability</span></span>|<span data-ttu-id="f5128-113">Windows Communication Foundation (WCF) yalnızca</span><span class="sxs-lookup"><span data-stu-id="f5128-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="f5128-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="f5128-114">Authentication (Server)</span></span>|<span data-ttu-id="f5128-115">İlk anlaşma sunucu kimlik doğrulaması gerektirir</span><span class="sxs-lookup"><span data-stu-id="f5128-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="f5128-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="f5128-116">Authentication (Client)</span></span>|<span data-ttu-id="f5128-117">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="f5128-117">User name/password</span></span>|  
|<span data-ttu-id="f5128-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="f5128-118">Integrity</span></span>|<span data-ttu-id="f5128-119">Evet, paylaşılan güvenlik bağlamını kullanarak</span><span class="sxs-lookup"><span data-stu-id="f5128-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="f5128-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="f5128-120">Confidentiality</span></span>|<span data-ttu-id="f5128-121">Evet, paylaşılan güvenlik bağlamını kullanarak</span><span class="sxs-lookup"><span data-stu-id="f5128-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="f5128-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="f5128-122">Transport</span></span>|<span data-ttu-id="f5128-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="f5128-123">HTTP</span></span>|  
|<span data-ttu-id="f5128-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f5128-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f5128-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="f5128-125">Service</span></span>  
 <span data-ttu-id="f5128-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="f5128-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f5128-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="f5128-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="f5128-128">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5128-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="f5128-129">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="f5128-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f5128-130">Kod</span><span class="sxs-lookup"><span data-stu-id="f5128-130">Code</span></span>  
 <span data-ttu-id="f5128-131">Aşağıdaki kod ileti güvenliği kullanan hizmet uç noktası oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5128-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="f5128-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f5128-132">Configuration</span></span>  
 <span data-ttu-id="f5128-133">Kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f5128-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f5128-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="f5128-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="f5128-135">Kod</span><span class="sxs-lookup"><span data-stu-id="f5128-135">Code</span></span>  
 <span data-ttu-id="f5128-136">Aşağıdaki kod istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5128-136">The following code creates the client.</span></span> <span data-ttu-id="f5128-137">Bağlama ileti mod güvenliği ve istemci kimlik bilgisi türü ayarlanır `UserName`.</span><span class="sxs-lookup"><span data-stu-id="f5128-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="f5128-138">Kullanıcı adı ve parola yalnızca kodu (Kısım yapılandırılabilir değildir) kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5128-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="f5128-139">Uygulama düzeyinde yapılması gerekir çünkü kullanıcı adını ve parolasını döndürmek için kod burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="f5128-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="f5128-140">Örneğin, kullanıcıdan veri sorgulamak için bir Windows Forms iletişim kutusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5128-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="f5128-141">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f5128-141">Configuration</span></span>  
 <span data-ttu-id="f5128-142">Aşağıdaki kod istemci yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f5128-142">The following code configures the client.</span></span> <span data-ttu-id="f5128-143">Bağlama ileti mod güvenliği ve istemci kimlik bilgisi türü ayarlanır `UserName`.</span><span class="sxs-lookup"><span data-stu-id="f5128-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="f5128-144">Kullanıcı adı ve parola yalnızca kodu (Kısım yapılandırılabilir değildir) kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f5128-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5128-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5128-145">See Also</span></span>  
 [<span data-ttu-id="f5128-146">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5128-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="f5128-147">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="f5128-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [<span data-ttu-id="f5128-148">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="f5128-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="f5128-149">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="f5128-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [<span data-ttu-id="f5128-150">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="f5128-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
