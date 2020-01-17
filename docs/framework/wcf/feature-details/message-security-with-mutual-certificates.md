---
title: Karşılıklı Sertifikalar ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: e784e254fb9314e69457d81a70400f7be30d9c13
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211991"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="61de8-102">Karşılıklı Sertifikalar ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="61de8-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="61de8-103">Aşağıdaki senaryoda ileti güvenliği modu kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61de8-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="61de8-104">İstemci ve hizmet, sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="61de8-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="61de8-105">Bu senaryo, X. 509.440 sertifika belirteci profiliyle WS-Security kullandığından birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="61de8-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61de8-106">Bu senaryo hizmet sertifikası anlaşmasını gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="61de8-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="61de8-107">Hizmet sertifikasının herhangi bir iletişimin öncesinde istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61de8-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="61de8-108">Sunucu sertifikası uygulamayla dağıtılabilir veya bant dışı bir iletişimde sağlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="61de8-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="61de8-109">![Karşılıklı sertifikalarla ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="61de8-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="61de8-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="61de8-110">Characteristic</span></span>|<span data-ttu-id="61de8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61de8-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="61de8-112">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="61de8-112">Security Mode</span></span>|<span data-ttu-id="61de8-113">İleti</span><span class="sxs-lookup"><span data-stu-id="61de8-113">Message</span></span>|  
|<span data-ttu-id="61de8-114">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="61de8-114">Interoperability</span></span>|<span data-ttu-id="61de8-115">Evet, WS-Security ve X. 509.440 sertifika belirteci profiliyle uyumlu istemciler ve hizmetler ile.</span><span class="sxs-lookup"><span data-stu-id="61de8-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="61de8-116">Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="61de8-116">Authentication</span></span>|<span data-ttu-id="61de8-117">Sunucu ve istemcinin karşılıklı kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="61de8-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="61de8-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="61de8-118">Integrity</span></span>|<span data-ttu-id="61de8-119">Evet</span><span class="sxs-lookup"><span data-stu-id="61de8-119">Yes</span></span>|  
|<span data-ttu-id="61de8-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="61de8-120">Confidentiality</span></span>|<span data-ttu-id="61de8-121">Evet</span><span class="sxs-lookup"><span data-stu-id="61de8-121">Yes</span></span>|  
|<span data-ttu-id="61de8-122">Aktarma</span><span class="sxs-lookup"><span data-stu-id="61de8-122">Transport</span></span>|<span data-ttu-id="61de8-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="61de8-123">HTTP</span></span>|  
|<span data-ttu-id="61de8-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="61de8-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="61de8-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="61de8-125">Service</span></span>  
 <span data-ttu-id="61de8-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="61de8-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="61de8-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="61de8-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="61de8-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61de8-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="61de8-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="61de8-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="61de8-130">Kod</span><span class="sxs-lookup"><span data-stu-id="61de8-130">Code</span></span>  
 <span data-ttu-id="61de8-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61de8-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="61de8-132">Hizmetin kimliğini doğrulamak için bir sertifika gerekir.</span><span class="sxs-lookup"><span data-stu-id="61de8-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="61de8-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="61de8-133">Configuration</span></span>  
 <span data-ttu-id="61de8-134">Aynı hizmeti oluşturmak için aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61de8-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
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
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="61de8-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="61de8-135">Client</span></span>  
 <span data-ttu-id="61de8-136">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="61de8-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="61de8-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="61de8-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="61de8-138">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="61de8-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="61de8-139">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="61de8-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="61de8-140">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="61de8-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="61de8-141">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="61de8-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="61de8-142">Kod</span><span class="sxs-lookup"><span data-stu-id="61de8-142">Code</span></span>  
 <span data-ttu-id="61de8-143">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61de8-143">The following code creates the client.</span></span> <span data-ttu-id="61de8-144">Güvenlik modu Ileti olarak ayarlanır ve istemci kimlik bilgileri türü sertifika olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="61de8-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="61de8-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="61de8-145">Configuration</span></span>  
 <span data-ttu-id="61de8-146">Aşağıdaki, istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="61de8-146">The following configures the client.</span></span> <span data-ttu-id="61de8-147">İstemci sertifikasının [\<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="61de8-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="61de8-148">Ayrıca, hizmet sertifikası [\<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="61de8-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61de8-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61de8-149">See also</span></span>

- [<span data-ttu-id="61de8-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="61de8-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="61de8-151">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="61de8-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="61de8-152">[Nasıl yapılır: geliştirme sırasında aktarım güvenliği için WCF 'de geçici sertifikalar oluşturma ve bunları kullanma](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="61de8-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
