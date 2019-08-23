---
title: Karşılıklı Sertifikalar ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: bd64531116b1588683c2f5c8964e78e41e371ecf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955348"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="f4c9c-102">Karşılıklı Sertifikalar ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f4c9c-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="f4c9c-103">Aşağıdaki senaryoda ileti güvenliği modu kullanılarak güvenliği sağlanmış bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="f4c9c-104">İstemci ve hizmet, sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="f4c9c-105">Bu senaryo, X. 509.440 sertifika belirteci profiliyle WS-Security kullandığından birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4c9c-106">Bu senaryo hizmet sertifikası anlaşmasını gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="f4c9c-107">Hizmet sertifikasının herhangi bir iletişimin öncesinde istemciye sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="f4c9c-108">Sunucu sertifikası uygulamayla dağıtılabilir veya bant dışı bir iletişimde sağlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="f4c9c-109">![Karşılıklı sertifikalarla ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="f4c9c-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="f4c9c-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="f4c9c-110">Characteristic</span></span>|<span data-ttu-id="f4c9c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4c9c-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f4c9c-112">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="f4c9c-112">Security Mode</span></span>|<span data-ttu-id="f4c9c-113">`Message`</span><span class="sxs-lookup"><span data-stu-id="f4c9c-113">Message</span></span>|  
|<span data-ttu-id="f4c9c-114">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f4c9c-114">Interoperability</span></span>|<span data-ttu-id="f4c9c-115">Evet, WS-Security ve X. 509.440 sertifika belirteci profiliyle uyumlu istemciler ve hizmetler ile.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="f4c9c-116">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f4c9c-116">Authentication</span></span>|<span data-ttu-id="f4c9c-117">Sunucu ve istemcinin karşılıklı kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="f4c9c-118">Doğruluğunu</span><span class="sxs-lookup"><span data-stu-id="f4c9c-118">Integrity</span></span>|<span data-ttu-id="f4c9c-119">Evet</span><span class="sxs-lookup"><span data-stu-id="f4c9c-119">Yes</span></span>|  
|<span data-ttu-id="f4c9c-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="f4c9c-120">Confidentiality</span></span>|<span data-ttu-id="f4c9c-121">Evet</span><span class="sxs-lookup"><span data-stu-id="f4c9c-121">Yes</span></span>|  
|<span data-ttu-id="f4c9c-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="f4c9c-122">Transport</span></span>|<span data-ttu-id="f4c9c-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="f4c9c-123">HTTP</span></span>|  
|<span data-ttu-id="f4c9c-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f4c9c-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f4c9c-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="f4c9c-125">Service</span></span>  
 <span data-ttu-id="f4c9c-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f4c9c-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="f4c9c-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="f4c9c-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="f4c9c-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f4c9c-130">Kod</span><span class="sxs-lookup"><span data-stu-id="f4c9c-130">Code</span></span>  
 <span data-ttu-id="f4c9c-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="f4c9c-132">Hizmetin kimliğini doğrulamak için bir sertifika gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="f4c9c-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f4c9c-133">Configuration</span></span>  
 <span data-ttu-id="f4c9c-134">Aynı hizmeti oluşturmak için aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f4c9c-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="f4c9c-135">Client</span></span>  
 <span data-ttu-id="f4c9c-136">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f4c9c-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="f4c9c-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="f4c9c-138">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="f4c9c-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="f4c9c-139">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="f4c9c-140">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="f4c9c-141">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f4c9c-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="f4c9c-142">Kod</span><span class="sxs-lookup"><span data-stu-id="f4c9c-142">Code</span></span>  
 <span data-ttu-id="f4c9c-143">Aşağıdaki kod istemcisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-143">The following code creates the client.</span></span> <span data-ttu-id="f4c9c-144">Güvenlik modu Ileti olarak ayarlanır ve istemci kimlik bilgileri türü sertifika olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="f4c9c-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f4c9c-145">Configuration</span></span>  
 <span data-ttu-id="f4c9c-146">Aşağıdaki, istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-146">The following configures the client.</span></span> <span data-ttu-id="f4c9c-147">Bir istemci sertifikasının, [ \<ClientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="f4c9c-148">Ayrıca, hizmet sertifikası [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4c9c-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4c9c-149">See also</span></span>

- [<span data-ttu-id="f4c9c-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4c9c-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="f4c9c-151">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="f4c9c-151">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
- [<span data-ttu-id="f4c9c-152">Nasıl yapılır: Geliştirme sırasında aktarım güvenliği için WCF 'de geçici sertifikalar oluşturma ve bunları yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f4c9c-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](https://go.microsoft.com/fwlink/?LinkId=244264)
