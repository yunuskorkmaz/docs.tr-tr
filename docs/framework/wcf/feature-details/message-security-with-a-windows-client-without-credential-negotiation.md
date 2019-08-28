---
title: Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 724e7792e09bea23d95d32f86c2241de473d3876
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045869"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="5c526-102">Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5c526-102">Message Security with a Windows Client without Credential Negotiation</span></span>

<span data-ttu-id="5c526-103">Aşağıdaki senaryoda Kerberos protokolüyle güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5c526-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>

<span data-ttu-id="5c526-104">Hem hizmet hem de istemci aynı etki alanında veya güvenilen etki alanlarında.</span><span class="sxs-lookup"><span data-stu-id="5c526-104">Both the service and the client are in the same domain or trusted domains.</span></span>

> [!NOTE]
> <span data-ttu-id="5c526-105">Bu senaryo ve [Windows Istemcisiyle Ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) arasındaki fark, bu senaryonun uygulama iletisini göndermeden önce hizmet kimlik bilgilerini anlaşamayacağı bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="5c526-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="5c526-106">Buna ek olarak, Kerberos protokolünü gerektirdiğinden bu senaryo bir Windows etki alanı ortamı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5c526-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>

<span data-ttu-id="5c526-107">![Kimlik bilgisi anlaşması olmadan ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="5c526-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>

|<span data-ttu-id="5c526-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="5c526-108">Characteristic</span></span>|<span data-ttu-id="5c526-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c526-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="5c526-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="5c526-110">Security Mode</span></span>|<span data-ttu-id="5c526-111">`Message`</span><span class="sxs-lookup"><span data-stu-id="5c526-111">Message</span></span>|
|<span data-ttu-id="5c526-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="5c526-112">Interoperability</span></span>|<span data-ttu-id="5c526-113">Evet, WS-Kerberos belirteci ile profil uyumlu istemcilerle güvenlik</span><span class="sxs-lookup"><span data-stu-id="5c526-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|
|<span data-ttu-id="5c526-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="5c526-114">Authentication (Server)</span></span>|<span data-ttu-id="5c526-115">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="5c526-115">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="5c526-116">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="5c526-116">Authentication (Client)</span></span>|<span data-ttu-id="5c526-117">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="5c526-117">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="5c526-118">Doğruluğunu</span><span class="sxs-lookup"><span data-stu-id="5c526-118">Integrity</span></span>|<span data-ttu-id="5c526-119">Evet</span><span class="sxs-lookup"><span data-stu-id="5c526-119">Yes</span></span>|
|<span data-ttu-id="5c526-120">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="5c526-120">Confidentiality</span></span>|<span data-ttu-id="5c526-121">Evet</span><span class="sxs-lookup"><span data-stu-id="5c526-121">Yes</span></span>|
|<span data-ttu-id="5c526-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="5c526-122">Transport</span></span>|<span data-ttu-id="5c526-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="5c526-123">HTTP</span></span>|
|<span data-ttu-id="5c526-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="5c526-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="5c526-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="5c526-125">Service</span></span>

<span data-ttu-id="5c526-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5c526-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5c526-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="5c526-127">Do one of the following:</span></span>

- <span data-ttu-id="5c526-128">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5c526-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="5c526-129">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5c526-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="5c526-130">Kod</span><span class="sxs-lookup"><span data-stu-id="5c526-130">Code</span></span>

<span data-ttu-id="5c526-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5c526-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="5c526-132">Kod, hizmet kimlik bilgileri anlaşmasını ve güvenlik bağlamı belirtecinin (SCT) kurulmasını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5c526-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>

> [!NOTE]
> <span data-ttu-id="5c526-133">Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmetin Kullanıcı hesabının Active Directory etki alanına kayıtlı hizmet asıl adına (SPN) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c526-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="5c526-134">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5c526-134">You can do this in two ways:</span></span>

1. <span data-ttu-id="5c526-135">Hizmetini çalıştırmak için `LocalSystem`veyahesabını kullanın. `NetworkService`</span><span class="sxs-lookup"><span data-stu-id="5c526-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="5c526-136">Makine Active Directory etki alanına katıldığında, bu hesapların bir makine SPN 'sine erişimi olduğundan, WCF otomatik olarak hizmetin meta verilerinde hizmetin uç noktasında uygun SPN öğesini otomatik olarak oluşturur (Web Hizmetleri açıklaması Dil veya WSDL).</span><span class="sxs-lookup"><span data-stu-id="5c526-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>

2. <span data-ttu-id="5c526-137">Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c526-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="5c526-138">Bu durumda, bu etki alanı hesabı için bir SPN oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c526-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="5c526-139">Bunu yapmanın bir yolu, Setspn. exe yardımcı programı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="5c526-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="5c526-140">Hizmet hesabı için SPN oluşturulduktan sonra, bu SPN 'YI, meta verileri (WSDL) aracılığıyla hizmetin istemcilerine yayımlamak üzere WCF 'yi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="5c526-140">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="5c526-141">Bu, bir uygulama yapılandırma dosyası veya kodu gibi, gösterilen uç nokta için uç nokta kimliği ayarlanarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="5c526-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="5c526-142">Aşağıdaki örnek, kimliği programlı olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="5c526-142">The following example publishes the identity programmatically.</span></span>

<span data-ttu-id="5c526-143">SPN 'Ler, Kerberos protokolü ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](https://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="5c526-143">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span></span> <span data-ttu-id="5c526-144">Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="5c526-144">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a><span data-ttu-id="5c526-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5c526-145">Configuration</span></span>

<span data-ttu-id="5c526-146">Aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c526-146">The following configuration can be used instead of the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors />
    <services>
      <service behaviorConfiguration="" name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="KerberosBinding"
                  name="WSHttpBinding_ICalculator"
                  contract="ServiceModel.ICalculator"
                  listenUri="net.tcp://localhost/metadata" >
         <identity>
            <servicePrincipalName value="service_spn_name" />
         </identity>
        </endpoint>
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="KerberosBinding">
          <security>
            <message negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="5c526-147">İstemci</span><span class="sxs-lookup"><span data-stu-id="5c526-147">Client</span></span>

<span data-ttu-id="5c526-148">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5c526-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5c526-149">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="5c526-149">Do one of the following:</span></span>

- <span data-ttu-id="5c526-150">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="5c526-150">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="5c526-151">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5c526-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5c526-152">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5c526-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5c526-153">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5c526-153">For example:</span></span>

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="5c526-154">Kod</span><span class="sxs-lookup"><span data-stu-id="5c526-154">Code</span></span>

<span data-ttu-id="5c526-155">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5c526-155">The following code configures the client.</span></span> <span data-ttu-id="5c526-156">Güvenlik modu Ileti olarak ayarlanır ve istemci kimlik bilgisi türü Windows olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5c526-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="5c526-157"><xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> Ve özelliklerinin<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> olarak`false`ayarlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5c526-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="5c526-158">Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmet ile iletişim kurmadan önce istemcinin hizmetin hesap SPN 'si ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c526-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="5c526-159">İstemci, kimlik doğrulaması yapmak ve hizmetle iletişimin güvenliğini sağlamak için Kerberos belirtecini almak üzere SPN 'YI kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c526-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="5c526-160">Aşağıdaki örnek, istemcisinin hizmetin SPN 'si ile nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c526-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="5c526-161">İstemcisini oluşturmak için [ServiceModel meta veri yardımcı programı aracı 'nı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanıyorsanız, hizmetin meta verileri bu bilgileri IÇERIYORSA hizmetin SPN 'si otomatik olarak hizmetin meta VERILERI (wsdl) üzerinden istemciye yayılır.</span><span class="sxs-lookup"><span data-stu-id="5c526-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="5c526-162">Hizmetin meta verilerine SPN 'yi dahil etmek için hizmeti yapılandırma hakkında daha fazla bilgi için, bu konunun devamındaki "hizmet" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5c526-162">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>
>
> <span data-ttu-id="5c526-163">SPN 'Ler, Kerberos ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](https://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="5c526-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span></span> <span data-ttu-id="5c526-164">Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="5c526-164">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a><span data-ttu-id="5c526-165">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5c526-165">Configuration</span></span>

<span data-ttu-id="5c526-166">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5c526-166">The following code configures the client.</span></span> <span data-ttu-id="5c526-167">ServicePrincipalName > öğesinin, hizmetin Active Directory etki alanındaki hesabı için kayıtlı olan [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) hizmet SPN 'si ile eşleşecek şekilde ayarlanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5c526-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://localhost/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator">
        <identity>
          <servicePrincipalName value="service_spn_name" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5c526-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c526-168">See also</span></span>

- [<span data-ttu-id="5c526-169">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5c526-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="5c526-170">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="5c526-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5c526-171">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="5c526-171">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
