---
description: 'Hakkında daha fazla bilgi edinin: sertifika Istemcisiyle Ileti güvenliği'
title: Sertifika İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: f1924510c5860b377568da204bbd9154e4970c24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99727072"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="fc665-103">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="fc665-103">Message Security with a Certificate Client</span></span>

<span data-ttu-id="fc665-104">Aşağıdaki senaryoda ileti güvenliği modu kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fc665-104">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="fc665-105">İstemci ve hizmetin her ikisi de sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="fc665-105">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="fc665-106">Daha fazla bilgi için bkz. [Dağıtılmış uygulama güvenliği](distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="fc665-106">For more information, see [Distributed Application Security](distributed-application-security.md).</span></span>

 ![Sertifikayı içeren bir istemciyi gösteren ekran görüntüsü.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="fc665-108">Örnek bir uygulama için bkz. [Ileti güvenliği sertifikası](../samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="fc665-108">For a sample application, see [Message Security Certificate](../samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="fc665-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="fc665-109">Characteristic</span></span>|<span data-ttu-id="fc665-110">Description</span><span class="sxs-lookup"><span data-stu-id="fc665-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fc665-111">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="fc665-111">Security Mode</span></span>|<span data-ttu-id="fc665-112">İleti</span><span class="sxs-lookup"><span data-stu-id="fc665-112">Message</span></span>|  
|<span data-ttu-id="fc665-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="fc665-113">Interoperability</span></span>|<span data-ttu-id="fc665-114">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="fc665-114">WCF only</span></span>|  
|<span data-ttu-id="fc665-115">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="fc665-115">Authentication (Server)</span></span>|<span data-ttu-id="fc665-116">Hizmet sertifikası kullanma</span><span class="sxs-lookup"><span data-stu-id="fc665-116">Using service certificate</span></span>|  
|<span data-ttu-id="fc665-117">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="fc665-117">Authentication (Client)</span></span>|<span data-ttu-id="fc665-118">İstemci sertifikası kullanma</span><span class="sxs-lookup"><span data-stu-id="fc665-118">Using client certificate</span></span>|  
|<span data-ttu-id="fc665-119">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="fc665-119">Integrity</span></span>|<span data-ttu-id="fc665-120">Yes</span><span class="sxs-lookup"><span data-stu-id="fc665-120">Yes</span></span>|  
|<span data-ttu-id="fc665-121">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="fc665-121">Confidentiality</span></span>|<span data-ttu-id="fc665-122">Yes</span><span class="sxs-lookup"><span data-stu-id="fc665-122">Yes</span></span>|  
|<span data-ttu-id="fc665-123">Aktarım</span><span class="sxs-lookup"><span data-stu-id="fc665-123">Transport</span></span>|<span data-ttu-id="fc665-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="fc665-124">HTTP</span></span>|  
|<span data-ttu-id="fc665-125">Bağlama</span><span class="sxs-lookup"><span data-stu-id="fc665-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="fc665-126">Hizmet</span><span class="sxs-lookup"><span data-stu-id="fc665-126">Service</span></span>  

 <span data-ttu-id="fc665-127">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fc665-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fc665-128">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="fc665-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="fc665-129">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc665-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="fc665-130">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="fc665-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fc665-131">Kod</span><span class="sxs-lookup"><span data-stu-id="fc665-131">Code</span></span>  

 <span data-ttu-id="fc665-132">Aşağıdaki kod, güvenli bir bağlam oluşturmak için ileti güvenliği kullanan bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc665-132">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="fc665-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc665-133">Configuration</span></span>  

 <span data-ttu-id="fc665-134">Aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc665-134">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="fc665-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="fc665-135">Client</span></span>  

 <span data-ttu-id="fc665-136">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fc665-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fc665-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="fc665-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="fc665-138">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="fc665-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="fc665-139">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc665-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="fc665-140">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc665-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="fc665-141">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc665-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="fc665-142">Kod</span><span class="sxs-lookup"><span data-stu-id="fc665-142">Code</span></span>  

 <span data-ttu-id="fc665-143">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc665-143">The following code creates the client.</span></span> <span data-ttu-id="fc665-144">Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="fc665-144">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="fc665-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc665-145">Configuration</span></span>  

 <span data-ttu-id="fc665-146">Aşağıdaki yapılandırma, bir uç nokta davranışı kullanarak istemci sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc665-146">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="fc665-147">Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fc665-147">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="fc665-148">Kod ayrıca, `identity` beklenen sunucu kimliğinin etki alanı adı sistemi (DNS) belirtmek için bir <> öğesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc665-148">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="fc665-149">Kimlik hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fc665-149">For more information about identity, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc665-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc665-150">See also</span></span>

- [<span data-ttu-id="fc665-151">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="fc665-151">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="fc665-152">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="fc665-152">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [<span data-ttu-id="fc665-153">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="fc665-153">Working with Certificates</span></span>](working-with-certificates.md)
- <span data-ttu-id="fc665-154">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fc665-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
