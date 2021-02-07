---
description: 'Hakkında daha fazla bilgi edinin: kimlik bilgisi anlaşması olmadan Windows Istemcisiyle Ileti güvenliği'
title: Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: e9edd63c80d868024d8a4b664c42456bb454cb69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99727020"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a><span data-ttu-id="e1d95-103">Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e1d95-103">Message Security with a Windows Client without Credential Negotiation</span></span>

<span data-ttu-id="e1d95-104">Aşağıdaki senaryoda Kerberos protokolüyle güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e1d95-104">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by the Kerberos protocol.</span></span>

<span data-ttu-id="e1d95-105">Hem hizmet hem de istemci aynı etki alanında veya güvenilen etki alanlarında.</span><span class="sxs-lookup"><span data-stu-id="e1d95-105">Both the service and the client are in the same domain or trusted domains.</span></span>

> [!NOTE]
> <span data-ttu-id="e1d95-106">Bu senaryo ve [Windows Istemcisiyle Ileti güvenliği](message-security-with-a-windows-client.md) arasındaki fark, bu senaryonun uygulama iletisini göndermeden önce hizmet kimlik bilgilerini anlaşamayacağı bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-106">The difference between this scenario and [Message Security with a Windows Client](message-security-with-a-windows-client.md) is that this scenario does not negotiate the service credential with the service prior to sending the application message.</span></span> <span data-ttu-id="e1d95-107">Buna ek olarak, Kerberos protokolünü gerektirdiğinden bu senaryo bir Windows etki alanı ortamı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1d95-107">Additionally, because this requires the Kerberos protocol, this scenario requires a Windows domain environment.</span></span>

<span data-ttu-id="e1d95-108">![Kimlik bilgisi anlaşması olmadan ileti güvenliği](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span><span class="sxs-lookup"><span data-stu-id="e1d95-108">![Message security without credential negotiation](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")</span></span>

|<span data-ttu-id="e1d95-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="e1d95-109">Characteristic</span></span>|<span data-ttu-id="e1d95-110">Description</span><span class="sxs-lookup"><span data-stu-id="e1d95-110">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="e1d95-111">Güvenlik modu</span><span class="sxs-lookup"><span data-stu-id="e1d95-111">Security Mode</span></span>|<span data-ttu-id="e1d95-112">İleti</span><span class="sxs-lookup"><span data-stu-id="e1d95-112">Message</span></span>|
|<span data-ttu-id="e1d95-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="e1d95-113">Interoperability</span></span>|<span data-ttu-id="e1d95-114">Evet, Kerberos belirteci profili ile uyumlu istemcilerle WS-Security</span><span class="sxs-lookup"><span data-stu-id="e1d95-114">Yes, WS-Security with Kerberos token-profile compatible clients</span></span>|
|<span data-ttu-id="e1d95-115">Kimlik doğrulaması (sunucu)</span><span class="sxs-lookup"><span data-stu-id="e1d95-115">Authentication (Server)</span></span>|<span data-ttu-id="e1d95-116">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e1d95-116">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="e1d95-117">Kimlik doğrulaması (Istemci)</span><span class="sxs-lookup"><span data-stu-id="e1d95-117">Authentication (Client)</span></span>|<span data-ttu-id="e1d95-118">Sunucu ve istemcinin karşılıklı kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e1d95-118">Mutual authentication of the server and client</span></span>|
|<span data-ttu-id="e1d95-119">Bütünlük</span><span class="sxs-lookup"><span data-stu-id="e1d95-119">Integrity</span></span>|<span data-ttu-id="e1d95-120">Yes</span><span class="sxs-lookup"><span data-stu-id="e1d95-120">Yes</span></span>|
|<span data-ttu-id="e1d95-121">Gizlilik</span><span class="sxs-lookup"><span data-stu-id="e1d95-121">Confidentiality</span></span>|<span data-ttu-id="e1d95-122">Yes</span><span class="sxs-lookup"><span data-stu-id="e1d95-122">Yes</span></span>|
|<span data-ttu-id="e1d95-123">Aktarım</span><span class="sxs-lookup"><span data-stu-id="e1d95-123">Transport</span></span>|<span data-ttu-id="e1d95-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="e1d95-124">HTTP</span></span>|
|<span data-ttu-id="e1d95-125">Bağlama</span><span class="sxs-lookup"><span data-stu-id="e1d95-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a><span data-ttu-id="e1d95-126">Hizmet</span><span class="sxs-lookup"><span data-stu-id="e1d95-126">Service</span></span>

<span data-ttu-id="e1d95-127">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e1d95-128">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e1d95-128">Do one of the following:</span></span>

- <span data-ttu-id="e1d95-129">Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1d95-129">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="e1d95-130">Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e1d95-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="e1d95-131">Kod</span><span class="sxs-lookup"><span data-stu-id="e1d95-131">Code</span></span>

<span data-ttu-id="e1d95-132">Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1d95-132">The following code creates a service endpoint that uses message security.</span></span> <span data-ttu-id="e1d95-133">Kod, hizmet kimlik bilgileri anlaşmasını ve güvenlik bağlamı belirtecinin (SCT) kurulmasını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-133">The code disables service credential negotiation, and the establishment of a security context token (SCT).</span></span>

> [!NOTE]
> <span data-ttu-id="e1d95-134">Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmetin Kullanıcı hesabının Active Directory etki alanına kayıtlı hizmet asıl adına (SPN) erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-134">To use the Windows credential type without negotiation, the service's user account must have access to service principal name (SPN) that is registered with the Active Directory domain.</span></span> <span data-ttu-id="e1d95-135">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1d95-135">You can do this in two ways:</span></span>

1. <span data-ttu-id="e1d95-136">`NetworkService` `LocalSystem` Hizmetini çalıştırmak için veya hesabını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1d95-136">Use the `NetworkService` or `LocalSystem` account to run your service.</span></span> <span data-ttu-id="e1d95-137">Makine Active Directory etki alanına katıldığında, bu hesapların kurulduğu makine SPN 'sine erişimi olduğundan, WCF otomatik olarak hizmetin meta verilerinde (Web Hizmetleri Açıklama Dili veya WSDL) uygun SPN öğesini otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1d95-137">Because those accounts have access to the machine SPN that is established when the machine joins the Active Directory domain, WCF automatically generates the proper SPN element inside the service's endpoint in the service's metadata (Web Services Description Language, or WSDL).</span></span>

2. <span data-ttu-id="e1d95-138">Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1d95-138">Use an arbitrary Active Directory domain account to run your service.</span></span> <span data-ttu-id="e1d95-139">Bu durumda, bu etki alanı hesabı için bir SPN oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1d95-139">In this case, you need to establish an SPN for that domain account.</span></span> <span data-ttu-id="e1d95-140">Bunu yapmanın bir yolu Setspn.exe yardımcı program aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-140">One way of doing this is to use the Setspn.exe utility tool.</span></span> <span data-ttu-id="e1d95-141">Hizmet hesabı için SPN oluşturulduktan sonra, bu SPN 'YI, meta verileri (WSDL) aracılığıyla hizmetin istemcilerine yayımlamak üzere WCF 'yi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e1d95-141">Once the SPN is created for the service's account, configure WCF to publish that SPN to the service's clients through its metadata (WSDL).</span></span> <span data-ttu-id="e1d95-142">Bu, bir uygulama yapılandırma dosyası veya kodu gibi, gösterilen uç nokta için uç nokta kimliği ayarlanarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-142">This is done by setting the endpoint identity for the exposed endpoint, either though an application configuration file or code.</span></span> <span data-ttu-id="e1d95-143">Aşağıdaki örnek, kimliği programlı olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="e1d95-143">The following example publishes the identity programmatically.</span></span>

<span data-ttu-id="e1d95-144">SPN 'Ler, Kerberos protokolü ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e1d95-144">For more information about SPNs, the Kerberos protocol, and Active Directory, see [Kerberos Technical Supplement for Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="e1d95-145">Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="e1d95-145">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md).</span></span>

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a><span data-ttu-id="e1d95-146">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1d95-146">Configuration</span></span>

<span data-ttu-id="e1d95-147">Aşağıdaki yapılandırma kod yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1d95-147">The following configuration can be used instead of the code.</span></span>

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

## <a name="client"></a><span data-ttu-id="e1d95-148">İstemci</span><span class="sxs-lookup"><span data-stu-id="e1d95-148">Client</span></span>

<span data-ttu-id="e1d95-149">Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-149">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e1d95-150">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e1d95-150">Do one of the following:</span></span>

- <span data-ttu-id="e1d95-151">Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).</span><span class="sxs-lookup"><span data-stu-id="e1d95-151">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="e1d95-152">Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1d95-152">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e1d95-153">Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1d95-153">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e1d95-154">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e1d95-154">For example:</span></span>

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="e1d95-155">Kod</span><span class="sxs-lookup"><span data-stu-id="e1d95-155">Code</span></span>

<span data-ttu-id="e1d95-156">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-156">The following code configures the client.</span></span> <span data-ttu-id="e1d95-157">Güvenlik modu Ileti olarak ayarlanır ve istemci kimlik bilgisi türü Windows olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-157">The security mode is set to Message, and the client credential type is set to Windows.</span></span> <span data-ttu-id="e1d95-158"><xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A>Ve <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliklerinin olarak ayarlandığını unutmayın `false` .</span><span class="sxs-lookup"><span data-stu-id="e1d95-158">Note that the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> and <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> properties are set to `false`.</span></span>

> [!NOTE]
> <span data-ttu-id="e1d95-159">Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmet ile iletişim kurmadan önce istemcinin hizmetin hesap SPN 'si ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1d95-159">To use Windows credential type without negotiation, the client must be configured with the service's account SPN prior to commencing the communication with the service.</span></span> <span data-ttu-id="e1d95-160">İstemci, kimlik doğrulaması yapmak ve hizmetle iletişimin güvenliğini sağlamak için Kerberos belirtecini almak üzere SPN 'YI kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-160">The client uses the SPN to get the Kerberos token to authenticate and secure the communication with the service.</span></span> <span data-ttu-id="e1d95-161">Aşağıdaki örnek, istemcisinin hizmetin SPN 'si ile nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1d95-161">The following sample shows how to configure the client with the service's SPN.</span></span> <span data-ttu-id="e1d95-162">İstemciyi oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanıyorsanız, hizmetin meta verileri bu bilgileri IÇERIYORSA hizmetin SPN 'si otomatik olarak hizmetin meta VERILERINDEN (wsdl) istemciye yayılır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-162">If you are using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the client, the service's SPN will be automatically propagated to the client from the service's metadata (WSDL), if the service's metadata contains that information.</span></span> <span data-ttu-id="e1d95-163">Hizmetin meta verilerine SPN 'yi dahil etmek için hizmeti yapılandırma hakkında daha fazla bilgi için, bu konunun devamındaki "hizmet" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e1d95-163">For more information about how to configure the service to include its SPN in the service's metadata, see the "Service" section later in this topic .</span></span>
>
> <span data-ttu-id="e1d95-164">SPN 'Ler, Kerberos ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e1d95-164">For more information about SPNs, Kerberos, and Active Directory, see [Kerberos Technical Supplement for Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span> <span data-ttu-id="e1d95-165">Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](securitybindingelement-authentication-modes.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="e1d95-165">For more information about endpoint identities, see [SecurityBindingElement Authentication Modes](securitybindingelement-authentication-modes.md) topic.</span></span>

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a><span data-ttu-id="e1d95-166">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e1d95-166">Configuration</span></span>

<span data-ttu-id="e1d95-167">Aşağıdaki kod istemcisini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e1d95-167">The following code configures the client.</span></span> <span data-ttu-id="e1d95-168">[\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md)Öğesinin, Active Directory etki alanındaki hizmet hesabı için kayıtlı olarak hizmetin SPN 'sine eşleşecek şekilde ayarlanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1d95-168">Note that the [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) element must be set to match the service's SPN as registered for the service's account in the Active Directory domain.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e1d95-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1d95-169">See also</span></span>

- [<span data-ttu-id="e1d95-170">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="e1d95-170">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="e1d95-171">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="e1d95-171">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="e1d95-172">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e1d95-172">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
