---
title: 'Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma'
description: WCF 'de aktarım ve Ileti güvenlik modlarını en iyi şekilde sunan ileti kimlik bilgileriyle aktarım güvenliğini nasıl uygulayacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246655"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="d49b0-103">Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="d49b0-103">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="d49b0-104">Hem aktarım hem de ileti kimlik bilgileriyle bir hizmetin güvenliğini sağlamak, Windows Communication Foundation (WCF) içinde hem aktarım hem de Ileti güvenliği modlarından en iyi şekilde yararlanır.</span><span class="sxs-lookup"><span data-stu-id="d49b0-104">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d49b0-105">Sum olarak, aktarım katmanı güvenliği bütünlük ve gizlilik sağlar, ancak ileti katmanı güvenliği, katı taşıma güvenlik mekanizmalarıyla mümkün olmayan çeşitli kimlik bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d49b0-105">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="d49b0-106">Bu konuda, ve bağlamaları kullanılarak ileti kimlik bilgileriyle taşıma uygulamak için temel adımlar <xref:System.ServiceModel.WSHttpBinding> gösterilmektedir <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-106">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="d49b0-107">Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenlik modunu ayarlama](../how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="d49b0-107">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="d49b0-108">Güvenlik modu olarak ayarlandığında `TransportWithMessageCredential` , taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler.</span><span class="sxs-lookup"><span data-stu-id="d49b0-108">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="d49b0-109">HTTP için mekanizma, HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL); TCP, TCP veya Windows üzerinde SSL 'dir.</span><span class="sxs-lookup"><span data-stu-id="d49b0-109">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="d49b0-110">Aktarım HTTP ise (kullanılarak <xref:System.ServiceModel.WSHttpBinding> ), http üzerinden SSL, aktarım düzeyi güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d49b0-110">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="d49b0-111">Bu durumda, hizmeti barındıran bilgisayarı, bu konunun ilerleyen kısımlarında gösterildiği gibi, bir bağlantı noktasına bağlanan bir SSL sertifikası ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b0-111">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="d49b0-112">Aktarım TCP ise (kullanılarak <xref:System.ServiceModel.NetTcpBinding> ), varsayılan olarak, belirtilen aktarım düzeyi güvenliği Windows güvenliği veya TCP ÜZERINDEN SSL olur.</span><span class="sxs-lookup"><span data-stu-id="d49b0-112">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="d49b0-113">TCP üzerinden SSL kullanırken, <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> Bu konunun ilerleyen kısımlarında gösterildiği gibi, yöntemini kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d49b0-113">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="d49b0-114">Taşıma güvenliği için bir sertifikayla WSHttpBinding 'i kullanmak için (kodda)</span><span class="sxs-lookup"><span data-stu-id="d49b0-114">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="d49b0-115">Bir SSL sertifikasını makinedeki bir bağlantı noktasına bağlamak için HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-115">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="d49b0-116">Daha fazla bilgi için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="d49b0-116">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="d49b0-117">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-117">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="d49b0-118"><xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-118">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="d49b0-119">(Daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](selecting-a-credential-type.md).) Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d49b0-119">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="d49b0-120"><xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d49b0-120">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="d49b0-121">Adresin "HTTPS" düzenini kullanması gerektiğini ve makinenin gerçek adını ve SSL sertifikasının bağlandığı bağlantı noktası numarasını içermesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-121">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="d49b0-122">(Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="d49b0-122">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="d49b0-123">Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-123">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="d49b0-124">Örneğini oluşturun <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ICommunicationObject.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-124">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="d49b0-125">Bir aktarım güvenliği için bir sertifikayla NetTcpBinding kullanmak için (kodda)</span><span class="sxs-lookup"><span data-stu-id="d49b0-125">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="d49b0-126">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-126">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="d49b0-127">Öğesini <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-127">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="d49b0-128">Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d49b0-128">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="d49b0-129"><xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d49b0-129">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="d49b0-130">Adresin "net. TCP" düzenini kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-130">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="d49b0-131">(Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="d49b0-131">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="d49b0-132">Sınıfının örneğini oluşturun <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-132">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="d49b0-133"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Hizmetin X. 509.440 sertifikasını açıkça ayarlamak için sınıfının yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-133">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="d49b0-134">Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-134">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="d49b0-135"><xref:System.ServiceModel.ICommunicationObject.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-135">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="d49b0-136">Aktarım güvenliği için Windows ile NetTcpBinding 'i kullanmak için (kodda)</span><span class="sxs-lookup"><span data-stu-id="d49b0-136">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="d49b0-137">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-137">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="d49b0-138">' İ ' ye ayarlayarak aktarım güvenliğini Windows kullanacak şekilde <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> ayarlayın <xref:System.ServiceModel.TcpClientCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-138">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="d49b0-139">(Bunun varsayılan değer olduğunu unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="d49b0-139">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="d49b0-140">Öğesini <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-140">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="d49b0-141">Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d49b0-141">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="d49b0-142"><xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d49b0-142">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="d49b0-143">Adresin "net. TCP" düzenini kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-143">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="d49b0-144">(Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="d49b0-144">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="d49b0-145">Sınıfının örneğini oluşturun <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-145">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="d49b0-146"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Hizmetin X. 509.440 sertifikasını açıkça ayarlamak için sınıfının yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-146">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="d49b0-147">Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="d49b0-147">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="d49b0-148"><xref:System.ServiceModel.ICommunicationObject.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-148">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="d49b0-149">Yapılandırma kullanma</span><span class="sxs-lookup"><span data-stu-id="d49b0-149">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="d49b0-150">WSHttpBinding 'i kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d49b0-150">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="d49b0-151">Bilgisayarı bir bağlantı noktasına bağlaan SSL sertifikası ile yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-151">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="d49b0-152">(Daha fazla bilgi için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="d49b0-152">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="d49b0-153">`transport`Bu yapılandırmayla bir <> öğesi değeri ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d49b0-153">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="d49b0-154">İleti düzeyi güvenlik için istemci kimlik bilgisi türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="d49b0-154">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="d49b0-155">Aşağıdaki örnek, `clientCredentialType` <`message`> öğesinin özniteliğini olarak ayarlar `UserName` .</span><span class="sxs-lookup"><span data-stu-id="d49b0-155">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="d49b0-156">Aktarım güvenliği için bir sertifikayla NetTcpBinding kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d49b0-156">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="d49b0-157">TCP üzerinden SSL için, sertifikayı öğesinde açıkça belirtmeniz gerekir `<behaviors>` .</span><span class="sxs-lookup"><span data-stu-id="d49b0-157">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="d49b0-158">Aşağıdaki örnek, varsayılan depo konumundaki (yerel makine ve kişisel Mağazalar) veren tarafından bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d49b0-158">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="d49b0-159">[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)Bağlamalar bölümüne bir ekleyin</span><span class="sxs-lookup"><span data-stu-id="d49b0-159">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="d49b0-160">Bir Binding öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-160">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="d49b0-161">Bir <`security`> öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="d49b0-161">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="d49b0-162"><bir `message>` öğesi ekleyin ve `clientCredentialType` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-162">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="d49b0-163">Aktarım güvenliği için Windows ile NetTcpBinding 'i kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d49b0-163">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="d49b0-164">[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)Bağlamalar bölümüne bir ekleyin,</span><span class="sxs-lookup"><span data-stu-id="d49b0-164">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="d49b0-165">Bir <`binding`> öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-165">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="d49b0-166">Bir <`security`> öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="d49b0-166">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="d49b0-167">Bir <`transport`> öğesi ekleyin ve `clientCredentialType` özniteliğini olarak ayarlayın `Windows` .</span><span class="sxs-lookup"><span data-stu-id="d49b0-167">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="d49b0-168">Bir <`message`> öğesi ekleyin ve `clientCredentialType` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d49b0-168">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="d49b0-169">Aşağıdaki kod, değeri bir sertifika olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d49b0-169">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d49b0-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d49b0-170">See also</span></span>

- [<span data-ttu-id="d49b0-171">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="d49b0-171">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="d49b0-172">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d49b0-172">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="d49b0-173">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d49b0-173">Securing Services and Clients</span></span>](securing-services-and-clients.md)
