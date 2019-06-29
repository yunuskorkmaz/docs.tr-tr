---
title: Sertifika İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: fb68487746a7dc9cec1d1473b445bccc7b2b23c2
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424870"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="1ebca-102">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1ebca-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="1ebca-103">Aşağıdaki senaryoda, bir Windows Communication Foundation (WCF) istemci ve hizmet ileti güvenlik modunu kullanarak güvenli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ebca-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="1ebca-104">Hem istemci hem de hizmet sertifikaları ile doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="1ebca-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="1ebca-105">Daha fazla bilgi için [dağıtılmış uygulama güvenliği](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="1ebca-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Bir istemci sertifikası ile gösteren ekran görüntüsü.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="1ebca-107">Örnek bir uygulama için bkz: [ileti güvenliği sertifikası](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="1ebca-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="1ebca-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="1ebca-108">Characteristic</span></span>|<span data-ttu-id="1ebca-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ebca-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1ebca-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="1ebca-110">Security Mode</span></span>|<span data-ttu-id="1ebca-111">`Message`</span><span class="sxs-lookup"><span data-stu-id="1ebca-111">Message</span></span>|  
|<span data-ttu-id="1ebca-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="1ebca-112">Interoperability</span></span>|<span data-ttu-id="1ebca-113">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="1ebca-113">WCF only</span></span>|  
|<span data-ttu-id="1ebca-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="1ebca-114">Authentication (Server)</span></span>|<span data-ttu-id="1ebca-115">Hizmet sertifikası kullanarak</span><span class="sxs-lookup"><span data-stu-id="1ebca-115">Using service certificate</span></span>|  
|<span data-ttu-id="1ebca-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="1ebca-116">Authentication (Client)</span></span>|<span data-ttu-id="1ebca-117">İstemci sertifikası kullanarak</span><span class="sxs-lookup"><span data-stu-id="1ebca-117">Using client certificate</span></span>|  
|<span data-ttu-id="1ebca-118">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="1ebca-118">Integrity</span></span>|<span data-ttu-id="1ebca-119">Evet</span><span class="sxs-lookup"><span data-stu-id="1ebca-119">Yes</span></span>|  
|<span data-ttu-id="1ebca-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="1ebca-120">Confidentiality</span></span>|<span data-ttu-id="1ebca-121">Evet</span><span class="sxs-lookup"><span data-stu-id="1ebca-121">Yes</span></span>|  
|<span data-ttu-id="1ebca-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="1ebca-122">Transport</span></span>|<span data-ttu-id="1ebca-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="1ebca-123">HTTP</span></span>|  
|<span data-ttu-id="1ebca-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="1ebca-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="1ebca-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="1ebca-125">Service</span></span>  
 <span data-ttu-id="1ebca-126">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1ebca-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="1ebca-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="1ebca-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="1ebca-128">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ebca-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="1ebca-129">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1ebca-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1ebca-130">Kod</span><span class="sxs-lookup"><span data-stu-id="1ebca-130">Code</span></span>  
 <span data-ttu-id="1ebca-131">Aşağıdaki kod, güvenli bir bağlam'kurmak için ileti güvenliği kullanan bir hizmet uç noktası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ebca-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="1ebca-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1ebca-132">Configuration</span></span>  
 <span data-ttu-id="1ebca-133">Aşağıdaki yapılandırmayı kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ebca-133">The following configuration can be used instead of the code.</span></span>  
  
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
                  bindingConfiguration="MessageAndCertificateClient"   
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
  
## <a name="client"></a><span data-ttu-id="1ebca-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="1ebca-134">Client</span></span>  
 <span data-ttu-id="1ebca-135">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1ebca-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="1ebca-136">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="1ebca-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="1ebca-137">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ebca-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="1ebca-138">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ebca-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="1ebca-139">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ebca-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="1ebca-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1ebca-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="1ebca-141">Kod</span><span class="sxs-lookup"><span data-stu-id="1ebca-141">Code</span></span>  
 <span data-ttu-id="1ebca-142">Aşağıdaki kod, istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ebca-142">The following code creates the client.</span></span> <span data-ttu-id="1ebca-143">İleti modu güvenlik bağlamadır ve istemci kimlik bilgisi türü `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="1ebca-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="1ebca-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1ebca-144">Configuration</span></span>  
 <span data-ttu-id="1ebca-145">Aşağıdaki yapılandırma, bir uç nokta davranışı'nı kullanarak istemci sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ebca-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="1ebca-146">Sertifikalar hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1ebca-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="1ebca-147">Ayrıca kodda bir <`identity`> öğesini bir etki alanı adı sistemi (DNS), beklenen sunucu kimliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="1ebca-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="1ebca-148">Kimlik hakkında daha fazla bilgi için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1ebca-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ebca-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ebca-149">See also</span></span>

- [<span data-ttu-id="1ebca-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1ebca-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="1ebca-151">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="1ebca-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1ebca-152">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="1ebca-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1ebca-153">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="1ebca-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
