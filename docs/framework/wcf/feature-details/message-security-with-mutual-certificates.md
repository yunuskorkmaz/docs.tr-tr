---
title: Karşılıklı Sertifikalar ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: e2aaf1a5e6ae1074a81c08fc798f22ea5e9ce139
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184618"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="c559a-102">Karşılıklı Sertifikalar ile İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c559a-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="c559a-103">Aşağıdaki senaryo, bir Windows Communication Foundation (WCF) hizmetini ve ileti güvenliği modunu kullanarak güvenli istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c559a-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="c559a-104">İstemci ve hizmet sertifikalarla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="c559a-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="c559a-105">X.509 sertifika belirteci profiliile WS-Security kullandığından bu senaryo birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c559a-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c559a-106">Bu senaryo, hizmet sertifikasının anlaşmasını gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="c559a-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="c559a-107">Hizmet sertifikası herhangi bir iletişim öncesinde müşteriye sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c559a-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="c559a-108">Sunucu sertifikası uygulama yla birlikte dağıtılabilir veya bant dışı bir iletişimde sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c559a-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="c559a-109">![Ortak sertifikalarla ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="c559a-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="c559a-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="c559a-110">Characteristic</span></span>|<span data-ttu-id="c559a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c559a-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c559a-112">Güvenlik Modu</span><span class="sxs-lookup"><span data-stu-id="c559a-112">Security Mode</span></span>|<span data-ttu-id="c559a-113">İleti</span><span class="sxs-lookup"><span data-stu-id="c559a-113">Message</span></span>|  
|<span data-ttu-id="c559a-114">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="c559a-114">Interoperability</span></span>|<span data-ttu-id="c559a-115">Evet, WS-Security ve X.509 sertifika belirteç profili uyumlu istemciler ve hizmetleri ile.</span><span class="sxs-lookup"><span data-stu-id="c559a-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="c559a-116">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c559a-116">Authentication</span></span>|<span data-ttu-id="c559a-117">Sunucu ve istemcinin karşılıklı kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="c559a-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="c559a-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="c559a-118">Integrity</span></span>|<span data-ttu-id="c559a-119">Evet</span><span class="sxs-lookup"><span data-stu-id="c559a-119">Yes</span></span>|  
|<span data-ttu-id="c559a-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="c559a-120">Confidentiality</span></span>|<span data-ttu-id="c559a-121">Evet</span><span class="sxs-lookup"><span data-stu-id="c559a-121">Yes</span></span>|  
|<span data-ttu-id="c559a-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="c559a-122">Transport</span></span>|<span data-ttu-id="c559a-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="c559a-123">HTTP</span></span>|  
|<span data-ttu-id="c559a-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="c559a-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="c559a-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="c559a-125">Service</span></span>  
 <span data-ttu-id="c559a-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="c559a-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c559a-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="c559a-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="c559a-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c559a-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="c559a-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="c559a-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c559a-130">Kod</span><span class="sxs-lookup"><span data-stu-id="c559a-130">Code</span></span>  
 <span data-ttu-id="c559a-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet bitiş noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c559a-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="c559a-132">Hizmet, kendisini doğrulamak için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c559a-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="c559a-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c559a-133">Configuration</span></span>  
 <span data-ttu-id="c559a-134">Aynı hizmeti oluşturmak için kod yerine aşağıdaki yapılandırma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c559a-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="c559a-135">İstemci</span><span class="sxs-lookup"><span data-stu-id="c559a-135">Client</span></span>  
 <span data-ttu-id="c559a-136">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir.</span><span class="sxs-lookup"><span data-stu-id="c559a-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c559a-137">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="c559a-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="c559a-138">Kodu (ve istemci kodunu) kullanarak tek başına bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c559a-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="c559a-139">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c559a-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="c559a-140">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucuyu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c559a-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="c559a-141">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c559a-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="c559a-142">Kod</span><span class="sxs-lookup"><span data-stu-id="c559a-142">Code</span></span>  
 <span data-ttu-id="c559a-143">Aşağıdaki kod istemciyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c559a-143">The following code creates the client.</span></span> <span data-ttu-id="c559a-144">Güvenlik modu İleti olarak ayarlanır ve istemci kimlik bilgisi türü Sertifika olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c559a-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="c559a-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c559a-145">Configuration</span></span>  
 <span data-ttu-id="c559a-146">Aşağıdaki istemciyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c559a-146">The following configures the client.</span></span> <span data-ttu-id="c559a-147">İstemci Sertifikası>kullanılarak bir istemci sertifikası belirtilmelidir. [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="c559a-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="c559a-148">Ayrıca, hizmet sertifikası [ \<varsayılan Sertifika>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="c559a-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c559a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c559a-149">See also</span></span>

- [<span data-ttu-id="c559a-150">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c559a-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="c559a-151">[Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c559a-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="c559a-152">[Nasıl yapilir: Geliştirme Sırasında Ulaşım Güvenliği için WCF'de Geçici Sertifikalar Oluşturma ve Yükleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="c559a-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
