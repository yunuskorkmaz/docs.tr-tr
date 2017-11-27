---
title: "Sertifika İstemcisi ile İleti Güvenliği"
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
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: afc1e0def03040acaa5cffe3f67339a61cda7d5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="10b71-102">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="10b71-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="10b71-103">Aşağıdaki senaryoda gösterildiği bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenliğinin ileti güvenlik modu ile hizmet ve istemci.</span><span class="sxs-lookup"><span data-stu-id="10b71-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured using message security mode.</span></span> <span data-ttu-id="10b71-104">Hem istemci hem de hizmet sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="10b71-104">Both the client and the service are authenticated with certificates.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="10b71-105">[Dağıtılmış uygulama güvenliği](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="10b71-105"> [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="10b71-106">Örnek bir uygulama için bkz: [ileti güvenliği sertifikası](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="10b71-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="10b71-107">![İstemci sertifikası ile](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="10b71-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="10b71-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="10b71-108">Characteristic</span></span>|<span data-ttu-id="10b71-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10b71-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="10b71-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="10b71-110">Security Mode</span></span>|<span data-ttu-id="10b71-111">İleti</span><span class="sxs-lookup"><span data-stu-id="10b71-111">Message</span></span>|  
|<span data-ttu-id="10b71-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="10b71-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="10b71-113">yalnızca</span><span class="sxs-lookup"><span data-stu-id="10b71-113"> only</span></span>|  
|<span data-ttu-id="10b71-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="10b71-114">Authentication (Server)</span></span>|<span data-ttu-id="10b71-115">Hizmet sertifikası kullanarak</span><span class="sxs-lookup"><span data-stu-id="10b71-115">Using service certificate</span></span>|  
|<span data-ttu-id="10b71-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="10b71-116">Authentication (Client)</span></span>|<span data-ttu-id="10b71-117">İstemci sertifikası kullanarak</span><span class="sxs-lookup"><span data-stu-id="10b71-117">Using client certificate</span></span>|  
|<span data-ttu-id="10b71-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="10b71-118">Integrity</span></span>|<span data-ttu-id="10b71-119">Evet</span><span class="sxs-lookup"><span data-stu-id="10b71-119">Yes</span></span>|  
|<span data-ttu-id="10b71-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="10b71-120">Confidentiality</span></span>|<span data-ttu-id="10b71-121">Evet</span><span class="sxs-lookup"><span data-stu-id="10b71-121">Yes</span></span>|  
|<span data-ttu-id="10b71-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="10b71-122">Transport</span></span>|<span data-ttu-id="10b71-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="10b71-123">HTTP</span></span>|  
|<span data-ttu-id="10b71-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="10b71-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="10b71-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="10b71-125">Service</span></span>  
 <span data-ttu-id="10b71-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="10b71-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="10b71-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="10b71-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="10b71-128">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10b71-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="10b71-129">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="10b71-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="10b71-130">Kod</span><span class="sxs-lookup"><span data-stu-id="10b71-130">Code</span></span>  
 <span data-ttu-id="10b71-131">Aşağıdaki kod, ileti güvenliği güvenli içeriği kurmak için kullandığı bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10b71-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="10b71-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="10b71-132">Configuration</span></span>  
 <span data-ttu-id="10b71-133">Aşağıdaki yapılandırma kodu yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10b71-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
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
                  bindingConfiguration="MessageAndCerficiateClient"   
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="10b71-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="10b71-134">Client</span></span>  
 <span data-ttu-id="10b71-135">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="10b71-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="10b71-136">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="10b71-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="10b71-137">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10b71-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="10b71-138">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10b71-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="10b71-139">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="10b71-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="10b71-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="10b71-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="10b71-141">Kod</span><span class="sxs-lookup"><span data-stu-id="10b71-141">Code</span></span>  
 <span data-ttu-id="10b71-142">Aşağıdaki kod istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10b71-142">The following code creates the client.</span></span> <span data-ttu-id="10b71-143">Bağlama ileti mod güvenliği ve istemci kimlik bilgisi türü ayarlanır `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="10b71-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="10b71-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="10b71-144">Configuration</span></span>  
 <span data-ttu-id="10b71-145">Aşağıdaki yapılandırma bir uç noktası davranışı kullanarak istemci sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="10b71-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="10b71-146">Sertifikalar hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="10b71-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="10b71-147">Kod ayrıca kullanan bir <`identity`> öğesi bir etki alanı adı sistemi (DNS) beklenen sunucu kimliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="10b71-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="10b71-148">kimlik, bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="10b71-148"> identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10b71-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10b71-149">See Also</span></span>  
 [<span data-ttu-id="10b71-150">Güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="10b71-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="10b71-151">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="10b71-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="10b71-152">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="10b71-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="10b71-153">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="10b71-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
