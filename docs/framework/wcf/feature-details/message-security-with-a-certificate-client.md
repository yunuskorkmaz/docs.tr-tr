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
ms.workload: dotnet
ms.openlocfilehash: e778b48b3ff00c3053992f8e754f674cd7705ece
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="8b338-102">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8b338-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="8b338-103">Aşağıdaki senaryoda gösterildiği bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenliğinin ileti güvenlik modu ile hizmet ve istemci.</span><span class="sxs-lookup"><span data-stu-id="8b338-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured using message security mode.</span></span> <span data-ttu-id="8b338-104">Hem istemci hem de hizmet sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="8b338-104">Both the client and the service are authenticated with certificates.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="8b338-105">[Dağıtılmış uygulama güvenliği](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="8b338-105"> [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="8b338-106">Örnek bir uygulama için bkz: [ileti güvenliği sertifikası](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="8b338-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="8b338-107">![İstemci sertifikası ile](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="8b338-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="8b338-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="8b338-108">Characteristic</span></span>|<span data-ttu-id="8b338-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b338-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8b338-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="8b338-110">Security Mode</span></span>|<span data-ttu-id="8b338-111">İleti</span><span class="sxs-lookup"><span data-stu-id="8b338-111">Message</span></span>|  
|<span data-ttu-id="8b338-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="8b338-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8b338-113">yalnızca</span><span class="sxs-lookup"><span data-stu-id="8b338-113"> only</span></span>|  
|<span data-ttu-id="8b338-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="8b338-114">Authentication (Server)</span></span>|<span data-ttu-id="8b338-115">Hizmet sertifikası kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b338-115">Using service certificate</span></span>|  
|<span data-ttu-id="8b338-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="8b338-116">Authentication (Client)</span></span>|<span data-ttu-id="8b338-117">İstemci sertifikası kullanarak</span><span class="sxs-lookup"><span data-stu-id="8b338-117">Using client certificate</span></span>|  
|<span data-ttu-id="8b338-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="8b338-118">Integrity</span></span>|<span data-ttu-id="8b338-119">Evet</span><span class="sxs-lookup"><span data-stu-id="8b338-119">Yes</span></span>|  
|<span data-ttu-id="8b338-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="8b338-120">Confidentiality</span></span>|<span data-ttu-id="8b338-121">Evet</span><span class="sxs-lookup"><span data-stu-id="8b338-121">Yes</span></span>|  
|<span data-ttu-id="8b338-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="8b338-122">Transport</span></span>|<span data-ttu-id="8b338-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="8b338-123">HTTP</span></span>|  
|<span data-ttu-id="8b338-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="8b338-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="8b338-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="8b338-125">Service</span></span>  
 <span data-ttu-id="8b338-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8b338-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8b338-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="8b338-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="8b338-128">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b338-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="8b338-129">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="8b338-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8b338-130">Kod</span><span class="sxs-lookup"><span data-stu-id="8b338-130">Code</span></span>  
 <span data-ttu-id="8b338-131">Aşağıdaki kod, ileti güvenliği güvenli içeriği kurmak için kullandığı bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b338-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="8b338-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8b338-132">Configuration</span></span>  
 <span data-ttu-id="8b338-133">Aşağıdaki yapılandırma kodu yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b338-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="8b338-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="8b338-134">Client</span></span>  
 <span data-ttu-id="8b338-135">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8b338-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8b338-136">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="8b338-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="8b338-137">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b338-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="8b338-138">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b338-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="8b338-139">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b338-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="8b338-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8b338-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="8b338-141">Kod</span><span class="sxs-lookup"><span data-stu-id="8b338-141">Code</span></span>  
 <span data-ttu-id="8b338-142">Aşağıdaki kod istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b338-142">The following code creates the client.</span></span> <span data-ttu-id="8b338-143">Bağlama ileti mod güvenliği ve istemci kimlik bilgisi türü ayarlanır `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="8b338-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="8b338-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8b338-144">Configuration</span></span>  
 <span data-ttu-id="8b338-145">Aşağıdaki yapılandırma bir uç noktası davranışı kullanarak istemci sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b338-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="8b338-146">Sertifikalar hakkında daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8b338-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="8b338-147">Kod ayrıca kullanan bir <`identity`> öğesi bir etki alanı adı sistemi (DNS) beklenen sunucu kimliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="8b338-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8b338-148">kimlik, bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8b338-148"> identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b338-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b338-149">See Also</span></span>  
 [<span data-ttu-id="8b338-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8b338-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="8b338-151">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="8b338-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8b338-152">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="8b338-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="8b338-153">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="8b338-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
