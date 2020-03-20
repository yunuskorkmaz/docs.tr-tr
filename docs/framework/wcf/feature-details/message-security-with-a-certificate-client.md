---
title: Sertifika İstemcisi ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 3660877194931c2be5b9b1c9aa54e2595701697f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184651"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="fad25-102">Sertifika İstemcisi ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="fad25-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="fad25-103">Aşağıdaki senaryo, ileti güvenliği modu kullanılarak güvenli bir Windows Communication Foundation (WCF) istemcisi ve hizmetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fad25-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="fad25-104">Hem istemci hem de hizmet sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="fad25-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="fad25-105">Daha fazla bilgi için Bkz. [Dağıtılmış Uygulama Güvenliği.](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)</span><span class="sxs-lookup"><span data-stu-id="fad25-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Sertifikası olan bir istemciyi gösteren ekran görüntüsü.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="fad25-107">Örnek bir uygulama için [İleti Güvenlik Sertifikası'na](../../../../docs/framework/wcf/samples/message-security-certificate.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fad25-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="fad25-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="fad25-108">Characteristic</span></span>|<span data-ttu-id="fad25-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fad25-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fad25-110">Güvenlik Modu</span><span class="sxs-lookup"><span data-stu-id="fad25-110">Security Mode</span></span>|<span data-ttu-id="fad25-111">İleti</span><span class="sxs-lookup"><span data-stu-id="fad25-111">Message</span></span>|  
|<span data-ttu-id="fad25-112">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="fad25-112">Interoperability</span></span>|<span data-ttu-id="fad25-113">Yalnızca WCF</span><span class="sxs-lookup"><span data-stu-id="fad25-113">WCF only</span></span>|  
|<span data-ttu-id="fad25-114">Kimlik Doğrulama (Sunucu)</span><span class="sxs-lookup"><span data-stu-id="fad25-114">Authentication (Server)</span></span>|<span data-ttu-id="fad25-115">Hizmet sertifikasını kullanma</span><span class="sxs-lookup"><span data-stu-id="fad25-115">Using service certificate</span></span>|  
|<span data-ttu-id="fad25-116">Kimlik Doğrulama (İstemci)</span><span class="sxs-lookup"><span data-stu-id="fad25-116">Authentication (Client)</span></span>|<span data-ttu-id="fad25-117">İstemci sertifikasını kullanma</span><span class="sxs-lookup"><span data-stu-id="fad25-117">Using client certificate</span></span>|  
|<span data-ttu-id="fad25-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="fad25-118">Integrity</span></span>|<span data-ttu-id="fad25-119">Evet</span><span class="sxs-lookup"><span data-stu-id="fad25-119">Yes</span></span>|  
|<span data-ttu-id="fad25-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="fad25-120">Confidentiality</span></span>|<span data-ttu-id="fad25-121">Evet</span><span class="sxs-lookup"><span data-stu-id="fad25-121">Yes</span></span>|  
|<span data-ttu-id="fad25-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="fad25-122">Transport</span></span>|<span data-ttu-id="fad25-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="fad25-123">HTTP</span></span>|  
|<span data-ttu-id="fad25-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="fad25-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="fad25-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="fad25-125">Service</span></span>  
 <span data-ttu-id="fad25-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="fad25-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fad25-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="fad25-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="fad25-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fad25-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="fad25-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="fad25-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="fad25-130">Kod</span><span class="sxs-lookup"><span data-stu-id="fad25-130">Code</span></span>  
 <span data-ttu-id="fad25-131">Aşağıdaki kod, güvenli bir bağlam oluşturmak için ileti güvenliğini kullanan bir hizmet bitiş noktasının nasıl oluşturultuğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fad25-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="fad25-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fad25-132">Configuration</span></span>  
 <span data-ttu-id="fad25-133">Kod yerine aşağıdaki yapılandırma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fad25-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="fad25-134">İstemci</span><span class="sxs-lookup"><span data-stu-id="fad25-134">Client</span></span>  
 <span data-ttu-id="fad25-135">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="fad25-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="fad25-136">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="fad25-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="fad25-137">Kodu (ve istemci kodunu) kullanarak tek başına bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fad25-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="fad25-138">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fad25-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="fad25-139">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fad25-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="fad25-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="fad25-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="fad25-141">Kod</span><span class="sxs-lookup"><span data-stu-id="fad25-141">Code</span></span>  
 <span data-ttu-id="fad25-142">Aşağıdaki kod istemciyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fad25-142">The following code creates the client.</span></span> <span data-ttu-id="fad25-143">Bağlama ileti modu güvenliği için ve istemci kimlik bilgisi türü `Certificate`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fad25-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="fad25-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fad25-144">Configuration</span></span>  
 <span data-ttu-id="fad25-145">Aşağıdaki yapılandırma, bir bitiş noktası davranışı kullanarak istemci sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fad25-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="fad25-146">Sertifikalar hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)</span><span class="sxs-lookup"><span data-stu-id="fad25-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="fad25-147">Kod ayrıca, beklenen `identity` sunucu kimliğinin Etki Alanı Adı Sistemi(DNS) belirtmek için <bir> öğesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fad25-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="fad25-148">Kimlik hakkında daha fazla bilgi için [Hizmet Kimliği ve Kimlik Doğrulama'ya](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="fad25-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fad25-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fad25-149">See also</span></span>

- [<span data-ttu-id="fad25-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fad25-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="fad25-151">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="fad25-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fad25-152">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="fad25-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- <span data-ttu-id="fad25-153">[Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fad25-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
