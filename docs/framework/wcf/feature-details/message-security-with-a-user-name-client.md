---
title: Kullaıcı Adı İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 547c23509096b66c1fdbd46117a10f4de1692387
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212042"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="d5404-102">Kullaıcı Adı İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d5404-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="d5404-103">Aşağıdaki çizimde, ileti düzeyi güvenlik kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d5404-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="d5404-104">Hizmetin kimliği bir X. 509.440 sertifikasıyla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d5404-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="d5404-105">İstemci, bir Kullanıcı adı ve parola kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="d5404-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="d5404-106">Örnek bir uygulama için bkz. [Ileti güvenliği Kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="d5404-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="d5404-107">![Kullanıcı adı kimlik doğrulamasını kullanan ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42F5-B1AF-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="d5404-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="d5404-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d5404-108">Characteristic</span></span>|<span data-ttu-id="d5404-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5404-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d5404-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="d5404-110">Security Mode</span></span>|<span data-ttu-id="d5404-111">İleti</span><span class="sxs-lookup"><span data-stu-id="d5404-111">Message</span></span>|  
|<span data-ttu-id="d5404-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d5404-112">Interoperability</span></span>|<span data-ttu-id="d5404-113">Yalnızca Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="d5404-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="d5404-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="d5404-114">Authentication (Server)</span></span>|<span data-ttu-id="d5404-115">İlk anlaşma sunucu kimlik doğrulaması gerektiriyor</span><span class="sxs-lookup"><span data-stu-id="d5404-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="d5404-116">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="d5404-116">Authentication (Client)</span></span>|<span data-ttu-id="d5404-117">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="d5404-117">User name/password</span></span>|  
|<span data-ttu-id="d5404-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="d5404-118">Integrity</span></span>|<span data-ttu-id="d5404-119">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="d5404-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="d5404-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="d5404-120">Confidentiality</span></span>|<span data-ttu-id="d5404-121">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="d5404-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="d5404-122">Aktarma</span><span class="sxs-lookup"><span data-stu-id="d5404-122">Transport</span></span>|<span data-ttu-id="d5404-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="d5404-123">HTTP</span></span>|  
|<span data-ttu-id="d5404-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d5404-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d5404-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="d5404-125">Service</span></span>  
 <span data-ttu-id="d5404-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d5404-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d5404-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="d5404-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="d5404-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5404-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="d5404-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d5404-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d5404-130">Kod</span><span class="sxs-lookup"><span data-stu-id="d5404-130">Code</span></span>  
 <span data-ttu-id="d5404-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d5404-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="d5404-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d5404-132">Configuration</span></span>  
 <span data-ttu-id="d5404-133">Kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d5404-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="d5404-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="d5404-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="d5404-135">Kod</span><span class="sxs-lookup"><span data-stu-id="d5404-135">Code</span></span>  
 <span data-ttu-id="d5404-136">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d5404-136">The following code creates the client.</span></span> <span data-ttu-id="d5404-137">Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü ise `UserName`olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d5404-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="d5404-138">Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).</span><span class="sxs-lookup"><span data-stu-id="d5404-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="d5404-139">Kullanıcı adını ve parolayı döndüren kod, uygulama düzeyinde yapılması gerektiğinden burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="d5404-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="d5404-140">Örneğin, verileri Kullanıcı için sorgulamak üzere bir Windows Forms iletişim kutusu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5404-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="d5404-141">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d5404-141">Configuration</span></span>  
 <span data-ttu-id="d5404-142">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d5404-142">The following code configures the client.</span></span> <span data-ttu-id="d5404-143">Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü ise `UserName`olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d5404-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="d5404-144">Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).</span><span class="sxs-lookup"><span data-stu-id="d5404-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5404-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5404-145">See also</span></span>

- [<span data-ttu-id="d5404-146">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d5404-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="d5404-147">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="d5404-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [<span data-ttu-id="d5404-148">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="d5404-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d5404-149">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="d5404-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="d5404-150">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d5404-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
