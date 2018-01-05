---
title: "Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği"
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
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f069ff100a2fba1f6bace1d9a81ed69314261eae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="03e63-102">Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="03e63-102">Message Security with a Windows Client without Credential Negotiation</span></span>
<span data-ttu-id="03e63-103">Aşağıdaki senaryoda gösterildiği bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kerberos protokolü tarafından güvenli hale getirilmiş hizmet ve istemci.</span><span class="sxs-lookup"><span data-stu-id="03e63-103">The following scenario shows a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service secured by the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="03e63-104">Hem hizmet hem de istemci aynı etki alanında veya güvenilen etki alanlarında olan.</span><span class="sxs-lookup"><span data-stu-id="03e63-104">Both the service and the client are in the same domain or trusted domains.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03e63-105">Bu senaryo arasındaki farkı ve [Windows İstemcisi ile ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) olduğu Bu senaryoda uygulama iletiyi göndermeden önce hizmetiyle hizmet kimlik bilgilerini gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="03e63-105">The difference between this scenario and [Message Security with a Windows Client](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="03e63-106">Ayrıca, bu Kerberos protokolü gerektirdiğinden, bu senaryo, bir Windows etki alanı ortamında gerektirir.</span><span class="sxs-lookup"><span data-stu-id="03e63-106">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>  
  
 <span data-ttu-id="03e63-107">![Güvenlik kimlik bilgileri görüşmesi olmadan ileti](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="03e63-107">![Message security without credential negotiation](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>  
  
|<span data-ttu-id="03e63-108">Özelliği</span><span class="sxs-lookup"><span data-stu-id="03e63-108">Characteristic</span></span>|<span data-ttu-id="03e63-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03e63-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="03e63-110">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="03e63-110">Security Mode</span></span>|<span data-ttu-id="03e63-111">İleti</span><span class="sxs-lookup"><span data-stu-id="03e63-111">Message</span></span>|  
|<span data-ttu-id="03e63-112">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="03e63-112">Interoperability</span></span>|<span data-ttu-id="03e63-113">Evet, Kerberos belirteci profili uyumlu istemcileri ile WS güvenliği</span><span class="sxs-lookup"><span data-stu-id="03e63-113">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|  
|<span data-ttu-id="03e63-114">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="03e63-114">Authentication (Server)</span></span>|<span data-ttu-id="03e63-115">İstemci ve sunucu, karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="03e63-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="03e63-116">Kimlik doğrulaması (istemci)</span><span class="sxs-lookup"><span data-stu-id="03e63-116">Authentication (Client)</span></span>|<span data-ttu-id="03e63-117">İstemci ve sunucu, karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="03e63-117">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="03e63-118">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="03e63-118">Integrity</span></span>|<span data-ttu-id="03e63-119">Evet</span><span class="sxs-lookup"><span data-stu-id="03e63-119">Yes</span></span>|  
|<span data-ttu-id="03e63-120">Gizliliği</span><span class="sxs-lookup"><span data-stu-id="03e63-120">Confidentiality</span></span>|<span data-ttu-id="03e63-121">Evet</span><span class="sxs-lookup"><span data-stu-id="03e63-121">Yes</span></span>|  
|<span data-ttu-id="03e63-122">Taşıma</span><span class="sxs-lookup"><span data-stu-id="03e63-122">Transport</span></span>|<span data-ttu-id="03e63-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="03e63-123">HTTP</span></span>|  
|<span data-ttu-id="03e63-124">Bağlama</span><span class="sxs-lookup"><span data-stu-id="03e63-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="03e63-125">Hizmet</span><span class="sxs-lookup"><span data-stu-id="03e63-125">Service</span></span>  
 <span data-ttu-id="03e63-126">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="03e63-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="03e63-127">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="03e63-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="03e63-128">Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="03e63-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="03e63-129">Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="03e63-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="03e63-130">Kod</span><span class="sxs-lookup"><span data-stu-id="03e63-130">Code</span></span>  
 <span data-ttu-id="03e63-131">Aşağıdaki kod, ileti güvenliği kullanan hizmet uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="03e63-131">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="03e63-132">Kod hizmeti kimlik bilgileri görüşmesi ve bir güvenlik bağlamı belirteci (SCT) oluşturulmasını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="03e63-132">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03e63-133">Windows kimlik bilgisi türü anlaşma olmadan kullanmak için hizmetin kullanıcı hesabının Active Directory etki alanı ile kayıtlı hizmet asıl adı (SPN) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03e63-133">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="03e63-134">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="03e63-134">You can do this in two ways:</span></span>  
  
1.  <span data-ttu-id="03e63-135">Kullanım `NetworkService` veya `LocalSystem` , hizmetinizi çalıştırmak için hesap.</span><span class="sxs-lookup"><span data-stu-id="03e63-135">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="03e63-136">Bu hesapların makine Active Directory etki alanına katıldığında, kurulur SPN makine erişiminiz olduğundan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygun SPN öğe içinde hizmet uç noktası hizmetin meta veriler (Web Hizmetleri otomatik olarak oluşturur Açıklama Dili veya WSDL).</span><span class="sxs-lookup"><span data-stu-id="03e63-136">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>  
  
2.  <span data-ttu-id="03e63-137">Hizmetinizi çalıştırmak için rasgele bir Active Directory etki alanı hesabı kullanın.</span><span class="sxs-lookup"><span data-stu-id="03e63-137">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="03e63-138">Bu durumda, bu etki alanı hesabı için bir SPN oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03e63-138">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="03e63-139">Bunu yapmanın bir yolu, Setspn.exe yardımcı programı aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="03e63-139">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="03e63-140">Hizmet hesabı için SPN oluşturulduktan sonra yapılandırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu SPN hizmetin istemcileri meta verilerini (WSDL) aracılığıyla yayımlamak için.</span><span class="sxs-lookup"><span data-stu-id="03e63-140">Once the SPN is created for the service's account, configure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="03e63-141">Bu uç nokta kimliği gösterilen uç noktası için ayarlayarak yapılır ya da bir uygulama yapılandırma dosyası veya kod.</span><span class="sxs-lookup"><span data-stu-id="03e63-141">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="03e63-142">Aşağıdaki örnek kimliği programlı olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="03e63-142">The following example publishes the identity programmatically.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="03e63-143">SPN'ler, Kerberos protokolü ve Active Directory bkz [Kerberos teknik Eki'ni Windows için](http://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="03e63-143"> SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="03e63-144">uç nokta kimlikleri bkz [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="03e63-144"> endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a><span data-ttu-id="03e63-145">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="03e63-145">Configuration</span></span>  
 <span data-ttu-id="03e63-146">Aşağıdaki yapılandırma kodu yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03e63-146">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="03e63-147">İstemci</span><span class="sxs-lookup"><span data-stu-id="03e63-147">Client</span></span>  
 <span data-ttu-id="03e63-148">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="03e63-148">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="03e63-149">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="03e63-149">Do one of the following:</span></span>  
  
-   <span data-ttu-id="03e63-150">Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="03e63-150">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="03e63-151">Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="03e63-151">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="03e63-152">Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın.</span><span class="sxs-lookup"><span data-stu-id="03e63-152">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="03e63-153">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="03e63-153">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="03e63-154">Kod</span><span class="sxs-lookup"><span data-stu-id="03e63-154">Code</span></span>  
 <span data-ttu-id="03e63-155">Aşağıdaki kod istemci yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="03e63-155">The following code configures the client.</span></span> <span data-ttu-id="03e63-156">İletiye güvenlik modunu ayarlama ve istemci kimlik bilgisi türü Windows ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="03e63-156">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="03e63-157">Unutmayın <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> ve <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliklerinin `false`.</span><span class="sxs-lookup"><span data-stu-id="03e63-157">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03e63-158">Windows kimlik bilgisi türü anlaşma olmadan kullanmak için İstemci hizmet hesabı SPN hizmetiyle iletişim başlatmadan önce yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="03e63-158">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="03e63-159">İstemci kimlik doğrulaması ve hizmeti ile iletişimi güvenli hale getirmek için Kerberos belirteci almak için SPN kullanır.</span><span class="sxs-lookup"><span data-stu-id="03e63-159">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="03e63-160">Aşağıdaki örnek, sunucunun hizmetin SPN'si ile istemci yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="03e63-160">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="03e63-161">Kullanıyorsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetin meta veri içeriyorsa, istemci oluşturmak için sunucunun hizmetin SPN'si otomatik olarak istemciye hizmetin meta verilerini (WSDL) yayılır Bu bilgileri.</span><span class="sxs-lookup"><span data-stu-id="03e63-161">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="03e63-162">hizmetin meta verilerde kendi SPN eklemek için bu konunun devamındaki "Hizmet" bölümüne bakın hizmeti nasıl yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="03e63-162"> how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>  
>   
>  <span data-ttu-id="03e63-163">SPN'ler, Kerberos ve Active Directory hakkında daha fazla bilgi için bkz: [Kerberos teknik Eki'ni Windows için](http://go.microsoft.com/fwlink/?LinkId=88330).</span><span class="sxs-lookup"><span data-stu-id="03e63-163">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](http://go.microsoft.com/fwlink/?LinkId=88330).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="03e63-164">uç nokta kimlikleri bkz [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) konu.</span><span class="sxs-lookup"><span data-stu-id="03e63-164"> endpoint identities, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) topic.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a><span data-ttu-id="03e63-165">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="03e63-165">Configuration</span></span>  
 <span data-ttu-id="03e63-166">Aşağıdaki kod istemci yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="03e63-166">The following code configures the client.</span></span> <span data-ttu-id="03e63-167">Unutmayın [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi, sunucunun hizmetin SPN'si Active Directory etki alanındaki hizmet hesabının kayıtlı adıyla eşleşecek şekilde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03e63-167">Note that the [\<servicePrincipalName>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03e63-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03e63-168">See Also</span></span>  
 [<span data-ttu-id="03e63-169">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="03e63-169">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="03e63-170">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="03e63-170">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="03e63-171">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="03e63-171">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
