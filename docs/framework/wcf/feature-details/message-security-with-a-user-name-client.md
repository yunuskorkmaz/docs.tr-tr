---
description: 'Hakkında daha fazla bilgi edinin: Kullanıcı adı Istemcisiyle Ileti güvenliği'
title: Kullaıcı Adı İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 4502635df3b52ba069c19fca7a73cc9395dd105d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756116"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="76f28-103">Kullaıcı Adı İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="76f28-103">Message Security with a User Name Client</span></span>

<span data-ttu-id="76f28-104">Aşağıdaki çizimde, ileti düzeyi güvenlik kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="76f28-104">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="76f28-105">Hizmetin kimliği bir X. 509.440 sertifikasıyla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="76f28-105">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="76f28-106">İstemci, bir Kullanıcı adı ve parola kullanarak kimlik doğrular.</span><span class="sxs-lookup"><span data-stu-id="76f28-106">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="76f28-107">Örnek bir uygulama için bkz. [Ileti güvenliği Kullanıcı adı](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="76f28-107">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="76f28-108">![Kullanıcı adı kimlik doğrulamasını kullanan ileti güvenliği](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42F5-B1AF-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="76f28-108">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="76f28-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="76f28-109">Characteristic</span></span>|<span data-ttu-id="76f28-110">Description</span><span class="sxs-lookup"><span data-stu-id="76f28-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="76f28-111">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="76f28-111">Security Mode</span></span>|<span data-ttu-id="76f28-112">İleti</span><span class="sxs-lookup"><span data-stu-id="76f28-112">Message</span></span>|  
|<span data-ttu-id="76f28-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="76f28-113">Interoperability</span></span>|<span data-ttu-id="76f28-114">Yalnızca Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="76f28-114">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="76f28-115">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="76f28-115">Authentication (Server)</span></span>|<span data-ttu-id="76f28-116">İlk anlaşma sunucu kimlik doğrulaması gerektiriyor</span><span class="sxs-lookup"><span data-stu-id="76f28-116">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="76f28-117">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="76f28-117">Authentication (Client)</span></span>|<span data-ttu-id="76f28-118">Kullanıcı adı/parola</span><span class="sxs-lookup"><span data-stu-id="76f28-118">User name/password</span></span>|  
|<span data-ttu-id="76f28-119">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="76f28-119">Integrity</span></span>|<span data-ttu-id="76f28-120">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="76f28-120">Yes, using shared security context</span></span>|  
|<span data-ttu-id="76f28-121">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="76f28-121">Confidentiality</span></span>|<span data-ttu-id="76f28-122">Evet, paylaşılan güvenlik bağlamını kullanma</span><span class="sxs-lookup"><span data-stu-id="76f28-122">Yes, using shared security context</span></span>|  
|<span data-ttu-id="76f28-123">Aktarım</span><span class="sxs-lookup"><span data-stu-id="76f28-123">Transport</span></span>|<span data-ttu-id="76f28-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="76f28-124">HTTP</span></span>|  
|<span data-ttu-id="76f28-125">Bağlama</span><span class="sxs-lookup"><span data-stu-id="76f28-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="76f28-126">Hizmet</span><span class="sxs-lookup"><span data-stu-id="76f28-126">Service</span></span>  

 <span data-ttu-id="76f28-127">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="76f28-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="76f28-128">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="76f28-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="76f28-129">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="76f28-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="76f28-130">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="76f28-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="76f28-131">Kod</span><span class="sxs-lookup"><span data-stu-id="76f28-131">Code</span></span>  

 <span data-ttu-id="76f28-132">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="76f28-132">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="76f28-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76f28-133">Configuration</span></span>  

 <span data-ttu-id="76f28-134">Kod yerine aşağıdaki yapılandırma kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="76f28-134">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="76f28-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="76f28-135">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="76f28-136">Kod</span><span class="sxs-lookup"><span data-stu-id="76f28-136">Code</span></span>  

 <span data-ttu-id="76f28-137">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76f28-137">The following code creates the client.</span></span> <span data-ttu-id="76f28-138">Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `UserName` .</span><span class="sxs-lookup"><span data-stu-id="76f28-138">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="76f28-139">Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).</span><span class="sxs-lookup"><span data-stu-id="76f28-139">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="76f28-140">Kullanıcı adını ve parolayı döndüren kod, uygulama düzeyinde yapılması gerektiğinden burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="76f28-140">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="76f28-141">Örneğin, verileri Kullanıcı için sorgulamak üzere bir Windows Forms iletişim kutusu kullanın.</span><span class="sxs-lookup"><span data-stu-id="76f28-141">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="76f28-142">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76f28-142">Configuration</span></span>  

 <span data-ttu-id="76f28-143">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="76f28-143">The following code configures the client.</span></span> <span data-ttu-id="76f28-144">Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `UserName` .</span><span class="sxs-lookup"><span data-stu-id="76f28-144">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="76f28-145">Kullanıcı adı ve parola yalnızca kod kullanılarak belirtilebilir (yapılandırılabilir değildir).</span><span class="sxs-lookup"><span data-stu-id="76f28-145">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76f28-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76f28-146">See also</span></span>

- [<span data-ttu-id="76f28-147">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="76f28-147">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="76f28-148">İleti Güvenliği Kullanıcı Adı</span><span class="sxs-lookup"><span data-stu-id="76f28-148">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="76f28-149">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="76f28-149">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="76f28-150">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="76f28-150">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
