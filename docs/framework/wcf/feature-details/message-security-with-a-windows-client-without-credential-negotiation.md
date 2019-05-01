---
title: Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 43bc222bb69aafa3fa3492d79d35fbc492055ead
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038611"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="b3045-102">Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b3045-102">Message Security with a Windows Client without Credential Negotiation</span></span>
<span data-ttu-id="b3045-103">Aşağıdaki senaryoda, bir Windows Communication Foundation (WCF) istemci ve hizmet Kerberos protokolü tarafından güvenliği sağlanan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3045-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="b3045-104">Hem hizmet hem de istemci aynı etki alanında veya güvenilen etki alanlarında olan.</span><span class="sxs-lookup"><span data-stu-id="b3045-104">Both the service and the client are in the same domain or trusted domains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3045-105">Bu senaryo arasındaki farkı ve [Windows İstemcisi ile ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) olduğu Bu senaryoda hizmeti kimlik bilgileri uygulama iletisi göndermeden önce hizmet ile gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="b3045-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="b3045-106">Ayrıca, bu Kerberos protokolü gerektiğinden, bu senaryo, bir Windows etki alanı ortamı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b3045-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>  
  
 <span data-ttu-id="b3045-107">![Güvenlik kimlik bilgileri görüşmesi olmadan ileti](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="b3045-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>  
  
|<span data-ttu-id="b3045-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="b3045-108">Characteristic</span></span>|<span data-ttu-id="b3045-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3045-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b3045-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="b3045-110">Security Mode</span></span>|<span data-ttu-id="b3045-111">İleti</span><span class="sxs-lookup"><span data-stu-id="b3045-111">Message</span></span>|  
|<span data-ttu-id="b3045-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="b3045-112">Interoperability</span></span>|<span data-ttu-id="b3045-113">Evet, Kerberos belirteci profili uyumlu istemcilerle WS-güvenlik</span><span class="sxs-lookup"><span data-stu-id="b3045-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|  
|<span data-ttu-id="b3045-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="b3045-114">Authentication (Server)</span></span>|<span data-ttu-id="b3045-115">İstemci ve sunucu, karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b3045-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="b3045-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="b3045-116">Authentication (Client)</span></span>|<span data-ttu-id="b3045-117">İstemci ve sunucu, karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b3045-117">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="b3045-118">Bütünlüğü</span><span class="sxs-lookup"><span data-stu-id="b3045-118">Integrity</span></span>|<span data-ttu-id="b3045-119">Evet</span><span class="sxs-lookup"><span data-stu-id="b3045-119">Yes</span></span>|  
|<span data-ttu-id="b3045-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="b3045-120">Confidentiality</span></span>|<span data-ttu-id="b3045-121">Evet</span><span class="sxs-lookup"><span data-stu-id="b3045-121">Yes</span></span>|  
|<span data-ttu-id="b3045-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="b3045-122">Transport</span></span>|<span data-ttu-id="b3045-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="b3045-123">HTTP</span></span>|  
|<span data-ttu-id="b3045-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="b3045-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="b3045-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="b3045-125">Service</span></span>  
 <span data-ttu-id="b3045-126">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b3045-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b3045-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="b3045-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="b3045-128">Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3045-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="b3045-129">Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b3045-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b3045-130">Kod</span><span class="sxs-lookup"><span data-stu-id="b3045-130">Code</span></span>  
 <span data-ttu-id="b3045-131">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3045-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="b3045-132">Kod hizmeti kimlik bilgileri görüşmesi yanı sıra, oluşumunu bir güvenlik bağlamı belirteci (SCT) devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b3045-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3045-133">Anlaşma olmadan Windows kimlik bilgisi türü kullanmak için hizmetin kullanıcı hesabını Active Directory etki alanı ile kayıtlı hizmet asıl adı (SPN) erişiminiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3045-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="b3045-134">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3045-134">You can do this in two ways:</span></span>  
  
1. <span data-ttu-id="b3045-135">Kullanım `NetworkService` veya `LocalSystem` hizmetinizi çalıştırmak için hesap.</span><span class="sxs-lookup"><span data-stu-id="b3045-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="b3045-136">Bu hesapların makinenin Active Directory etki alanına katıldığında kurulur SPN makineye erişimi olduğundan, WCF uygun SPN öğe içinde hizmet uç noktası hizmetin meta verilerinde (Web Hizmetleri Açıklama otomatik olarak oluşturur. Dil veya WSDL).</span><span class="sxs-lookup"><span data-stu-id="b3045-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>  
  
2. <span data-ttu-id="b3045-137">Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3045-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="b3045-138">Bu durumda, bu etki alanı hesabı için bir SPN oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3045-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="b3045-139">Bunu yapmanın bir yolu, Setspn.exe yardımcı programı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b3045-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="b3045-140">Hizmet hesabı için SPN'nin oluşturulduktan sonra WCF meta verilerini (WSDL) aracılığıyla hizmetin istemciler söz konusu SPN yayımlamak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b3045-140">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="b3045-141">Bu ortaya çıkarılan uç nokta için uç nokta kimliğini ayarlayarak yapılır ya da bir uygulama yapılandırma dosyası veya kod.</span><span class="sxs-lookup"><span data-stu-id="b3045-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="b3045-142">Aşağıdaki örnek kimliğini programlı olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b3045-142">The following example publishes the identity programmatically.</span></span>  
  
 <span data-ttu-id="b3045-143">SPN hakkında daha fazla bilgi, Kerberos protokolü ve Active Directory için bkz. [Kerberos teknik ek Windows için](https://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="b3045-143">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span></span> <span data-ttu-id="b3045-144">Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="b3045-144">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a><span data-ttu-id="b3045-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b3045-145">Configuration</span></span>  
 <span data-ttu-id="b3045-146">Aşağıdaki yapılandırmayı kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3045-146">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="b3045-147">İstemci</span><span class="sxs-lookup"><span data-stu-id="b3045-147">Client</span></span>  
 <span data-ttu-id="b3045-148">Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b3045-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b3045-149">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="b3045-149">Do one of the following:</span></span>  
  
- <span data-ttu-id="b3045-150">Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3045-150">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="b3045-151">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3045-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b3045-152">Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3045-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b3045-153">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b3045-153">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b3045-154">Kod</span><span class="sxs-lookup"><span data-stu-id="b3045-154">Code</span></span>  
 <span data-ttu-id="b3045-155">Aşağıdaki kod, istemciyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b3045-155">The following code configures the client.</span></span> <span data-ttu-id="b3045-156">İleti güvenlik modunu ayarlanır ve istemci kimlik bilgisi türü için Windows ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b3045-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="b3045-157">Unutmayın <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> ve <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliklerinin `false`.</span><span class="sxs-lookup"><span data-stu-id="b3045-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3045-158">Windows kimlik bilgisi türü görüşmesi olmadan kullanmak için İstemci hizmet hesabı SPN hizmeti ile iletişimi işlemi hızlandırılabilir önce yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3045-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="b3045-159">İstemci kimlik doğrulaması ve hizmeti ile iletişimi güvenli hale getirmek için Kerberos belirteci almak için SPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3045-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="b3045-160">Aşağıdaki örnek, sunucunun hizmetin SPN'si ile istemci yapılandırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3045-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="b3045-161">Kullanıyorsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetin meta veri içeriyorsa, istemci üretmek için sunucunun hizmetin SPN'si otomatik olarak istemciye hizmet meta verileri (WSDL) iletilir Bu bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b3045-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="b3045-162">Hizmet meta verilerde, SPN eklemek için hizmet yapılandırma hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Hizmeti" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b3045-162">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>  
>   
>  <span data-ttu-id="b3045-163">SPN, Kerberos ve Active Directory hakkında daha fazla bilgi için bkz. [Kerberos teknik ek Windows için](https://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="b3045-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](https://go.microsoft.com/fwlink/?LinkId=88330).</span></span> <span data-ttu-id="b3045-164">Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) konu.</span><span class="sxs-lookup"><span data-stu-id="b3045-164">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a><span data-ttu-id="b3045-165">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b3045-165">Configuration</span></span>  
 <span data-ttu-id="b3045-166">Aşağıdaki kod, istemciyi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="b3045-166">The following code configures the client.</span></span> <span data-ttu-id="b3045-167">Unutmayın [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi hizmet hesabının Active Directory etki alanında kayıtlı sunucunun hizmetin SPN'si eşleşecek şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3045-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3045-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3045-168">See also</span></span>

- [<span data-ttu-id="b3045-169">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3045-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="b3045-170">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="b3045-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b3045-171">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="b3045-171">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
