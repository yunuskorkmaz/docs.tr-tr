---
title: Sertifika İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 2b2717bc68da9f07cd38e10a5d75b2a7df9add45
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602641"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="d7413-102">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d7413-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="d7413-103">Aşağıdaki senaryoda ileti güvenliği modu kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7413-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="d7413-104">İstemci ve hizmetin her ikisi de sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d7413-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="d7413-105">Daha fazla bilgi için bkz. [Dağıtılmış uygulama güvenliği](distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="d7413-105">For more information, see [Distributed Application Security](distributed-application-security.md).</span></span>

 ![Sertifikayı içeren bir istemciyi gösteren ekran görüntüsü.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="d7413-107">Örnek bir uygulama için bkz. [Ileti güvenliği sertifikası](../samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="d7413-107">For a sample application, see [Message Security Certificate](../samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="d7413-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="d7413-108">Characteristic</span></span>|<span data-ttu-id="d7413-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7413-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d7413-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="d7413-110">Security Mode</span></span>|<span data-ttu-id="d7413-111">İleti</span><span class="sxs-lookup"><span data-stu-id="d7413-111">Message</span></span>|  
|<span data-ttu-id="d7413-112">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d7413-112">Interoperability</span></span>|<span data-ttu-id="d7413-113">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="d7413-113">WCF only</span></span>|  
|<span data-ttu-id="d7413-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="d7413-114">Authentication (Server)</span></span>|<span data-ttu-id="d7413-115">Hizmet sertifikası kullanma</span><span class="sxs-lookup"><span data-stu-id="d7413-115">Using service certificate</span></span>|  
|<span data-ttu-id="d7413-116">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="d7413-116">Authentication (Client)</span></span>|<span data-ttu-id="d7413-117">İstemci sertifikası kullanma</span><span class="sxs-lookup"><span data-stu-id="d7413-117">Using client certificate</span></span>|  
|<span data-ttu-id="d7413-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="d7413-118">Integrity</span></span>|<span data-ttu-id="d7413-119">Yes</span><span class="sxs-lookup"><span data-stu-id="d7413-119">Yes</span></span>|  
|<span data-ttu-id="d7413-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="d7413-120">Confidentiality</span></span>|<span data-ttu-id="d7413-121">Yes</span><span class="sxs-lookup"><span data-stu-id="d7413-121">Yes</span></span>|  
|<span data-ttu-id="d7413-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d7413-122">Transport</span></span>|<span data-ttu-id="d7413-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="d7413-123">HTTP</span></span>|  
|<span data-ttu-id="d7413-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="d7413-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d7413-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="d7413-125">Service</span></span>  
 <span data-ttu-id="d7413-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d7413-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d7413-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="d7413-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="d7413-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7413-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="d7413-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d7413-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d7413-130">Kod</span><span class="sxs-lookup"><span data-stu-id="d7413-130">Code</span></span>  
 <span data-ttu-id="d7413-131">Aşağıdaki kod, güvenli bir bağlam oluşturmak için ileti güvenliği kullanan bir hizmet uç noktası oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7413-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="d7413-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7413-132">Configuration</span></span>  
 <span data-ttu-id="d7413-133">Aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7413-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="d7413-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="d7413-134">Client</span></span>  
 <span data-ttu-id="d7413-135">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d7413-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d7413-136">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="d7413-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="d7413-137">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="d7413-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="d7413-138">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7413-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d7413-139">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7413-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d7413-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d7413-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="d7413-141">Kod</span><span class="sxs-lookup"><span data-stu-id="d7413-141">Code</span></span>  
 <span data-ttu-id="d7413-142">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d7413-142">The following code creates the client.</span></span> <span data-ttu-id="d7413-143">Bağlama ileti modu güvenliğine, istemci kimlik bilgisi türü olarak ayarlanır `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="d7413-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="d7413-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7413-144">Configuration</span></span>  
 <span data-ttu-id="d7413-145">Aşağıdaki yapılandırma, bir uç nokta davranışı kullanarak istemci sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7413-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="d7413-146">Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="d7413-146">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="d7413-147">Kod ayrıca, `identity` beklenen sunucu kimliğinin etki alanı adı sistemi (DNS) belirtmek için bir <> öğesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7413-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="d7413-148">Kimlik hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d7413-148">For more information about identity, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7413-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7413-149">See also</span></span>

- [<span data-ttu-id="d7413-150">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="d7413-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="d7413-151">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="d7413-151">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [<span data-ttu-id="d7413-152">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="d7413-152">Working with Certificates</span></span>](working-with-certificates.md)
- <span data-ttu-id="d7413-153">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d7413-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
