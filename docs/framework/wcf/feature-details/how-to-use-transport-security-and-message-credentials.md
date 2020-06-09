---
title: 'Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f49c0eb46141081b91100a5ae1869cbcf556e353
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579390"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="3855e-102">Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="3855e-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="3855e-103">Hem aktarım hem de ileti kimlik bilgileriyle bir hizmetin güvenliğini sağlamak, Windows Communication Foundation (WCF) içinde hem aktarım hem de Ileti güvenliği modlarından en iyi şekilde yararlanır.</span><span class="sxs-lookup"><span data-stu-id="3855e-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3855e-104">Sum olarak, aktarım katmanı güvenliği bütünlük ve gizlilik sağlar, ancak ileti katmanı güvenliği, katı taşıma güvenlik mekanizmalarıyla mümkün olmayan çeşitli kimlik bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3855e-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="3855e-105">Bu konuda, ve bağlamaları kullanılarak ileti kimlik bilgileriyle taşıma uygulamak için temel adımlar <xref:System.ServiceModel.WSHttpBinding> gösterilmektedir <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="3855e-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="3855e-106">Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenlik modunu ayarlama](../how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="3855e-106">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="3855e-107">Güvenlik modu olarak ayarlandığında `TransportWithMessageCredential` , taşıma, aktarım düzeyi güvenliği sağlayan gerçek mekanizmayı belirler.</span><span class="sxs-lookup"><span data-stu-id="3855e-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="3855e-108">HTTP için mekanizma, HTTP (HTTPS) üzerinden Güvenli Yuva Katmanı (SSL); TCP, TCP veya Windows üzerinde SSL 'dir.</span><span class="sxs-lookup"><span data-stu-id="3855e-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="3855e-109">Aktarım HTTP ise (kullanılarak <xref:System.ServiceModel.WSHttpBinding> ), http üzerinden SSL, aktarım düzeyi güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3855e-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="3855e-110">Bu durumda, hizmeti barındıran bilgisayarı, bu konunun ilerleyen kısımlarında gösterildiği gibi, bir bağlantı noktasına bağlanan bir SSL sertifikası ile yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3855e-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="3855e-111">Aktarım TCP ise (kullanılarak <xref:System.ServiceModel.NetTcpBinding> ), varsayılan olarak, belirtilen aktarım düzeyi güvenliği Windows güvenliği veya TCP ÜZERINDEN SSL olur.</span><span class="sxs-lookup"><span data-stu-id="3855e-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="3855e-112">TCP üzerinden SSL kullanırken, <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> Bu konunun ilerleyen kısımlarında gösterildiği gibi, yöntemini kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3855e-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="3855e-113">Taşıma güvenliği için bir sertifikayla WSHttpBinding 'i kullanmak için (kodda)</span><span class="sxs-lookup"><span data-stu-id="3855e-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="3855e-114">Bir SSL sertifikasını makinedeki bir bağlantı noktasına bağlamak için HttpCfg. exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="3855e-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="3855e-115">Daha fazla bilgi için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="3855e-115">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="3855e-116">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="3855e-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="3855e-117"><xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="3855e-118">(Daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](selecting-a-credential-type.md).) Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3855e-118">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="3855e-119"><xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3855e-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="3855e-120">Adresin "HTTPS" düzenini kullanması gerektiğini ve makinenin gerçek adını ve SSL sertifikasının bağlandığı bağlantı noktası numarasını içermesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="3855e-121">(Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="3855e-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="3855e-122">Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="3855e-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="3855e-123">Örneğini oluşturun <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ICommunicationObject.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3855e-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="3855e-124">Bir aktarım güvenliği için bir sertifikayla NetTcpBinding kullanmak için (kodda)</span><span class="sxs-lookup"><span data-stu-id="3855e-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="3855e-125">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="3855e-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="3855e-126">Öğesini <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="3855e-127">Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3855e-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="3855e-128"><xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3855e-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="3855e-129">Adresin "net. TCP" düzenini kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="3855e-130">(Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="3855e-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="3855e-131">Sınıfının örneğini oluşturun <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="3855e-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="3855e-132"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Hizmetin X. 509.440 sertifikasını açıkça ayarlamak için sınıfının yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3855e-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="3855e-133">Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="3855e-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="3855e-134"><xref:System.ServiceModel.ICommunicationObject.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3855e-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="3855e-135">Aktarım güvenliği için Windows ile NetTcpBinding 'i kullanmak için (kodda)</span><span class="sxs-lookup"><span data-stu-id="3855e-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="3855e-136">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.NetTcpBinding> ve <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini olarak ayarlayın <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="3855e-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="3855e-137">' İ ' ye ayarlayarak aktarım güvenliğini Windows kullanacak şekilde <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> ayarlayın <xref:System.ServiceModel.TcpClientCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="3855e-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="3855e-138">(Bunun varsayılan değer olduğunu unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="3855e-138">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="3855e-139">Öğesini <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="3855e-140">Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3855e-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="3855e-141"><xref:System.Uri>Uygun bir temel adresle sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3855e-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="3855e-142">Adresin "net. TCP" düzenini kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="3855e-143">(Alternatif olarak, yapılandırmada temel adresi ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="3855e-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="3855e-144">Sınıfının örneğini oluşturun <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="3855e-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="3855e-145"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> Hizmetin X. 509.440 sertifikasını açıkça ayarlamak için sınıfının yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3855e-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="3855e-146">Yöntemini kullanarak bir hizmet uç noktası ekleyin <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> .</span><span class="sxs-lookup"><span data-stu-id="3855e-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="3855e-147"><xref:System.ServiceModel.ICommunicationObject.Open%2A>Aşağıdaki kodda gösterildiği gibi yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3855e-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="3855e-148">Yapılandırma kullanma</span><span class="sxs-lookup"><span data-stu-id="3855e-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="3855e-149">WSHttpBinding 'i kullanmak için</span><span class="sxs-lookup"><span data-stu-id="3855e-149">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="3855e-150">Bilgisayarı bir bağlantı noktasına bağlaan SSL sertifikası ile yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3855e-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="3855e-151">(Daha fazla bilgi için bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="3855e-151">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="3855e-152">`transport`Bu yapılandırmayla bir <> öğesi değeri ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3855e-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="3855e-153">İleti düzeyi güvenlik için istemci kimlik bilgisi türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="3855e-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="3855e-154">Aşağıdaki örnek, `clientCredentialType` <`message`> öğesinin özniteliğini olarak ayarlar `UserName` .</span><span class="sxs-lookup"><span data-stu-id="3855e-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="3855e-155">Aktarım güvenliği için bir sertifikayla NetTcpBinding kullanmak için</span><span class="sxs-lookup"><span data-stu-id="3855e-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="3855e-156">TCP üzerinden SSL için, sertifikayı öğesinde açıkça belirtmeniz gerekir `<behaviors>` .</span><span class="sxs-lookup"><span data-stu-id="3855e-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="3855e-157">Aşağıdaki örnek, varsayılan depo konumundaki (yerel makine ve kişisel Mağazalar) veren tarafından bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3855e-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2. <span data-ttu-id="3855e-158">[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)Bağlamalar bölümüne bir ekleyin</span><span class="sxs-lookup"><span data-stu-id="3855e-158">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="3855e-159">Bir Binding öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="3855e-160">Bir <`security`> öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="3855e-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="3855e-161"><bir `message>` öğesi ekleyin ve `clientCredentialType` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="3855e-162">Aktarım güvenliği için Windows ile NetTcpBinding 'i kullanmak için</span><span class="sxs-lookup"><span data-stu-id="3855e-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="3855e-163">[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)Bağlamalar bölümüne bir ekleyin,</span><span class="sxs-lookup"><span data-stu-id="3855e-163">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="3855e-164">Bir <`binding`> öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="3855e-165">Bir <`security`> öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="3855e-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="3855e-166">Bir <`transport`> öğesi ekleyin ve `clientCredentialType` özniteliğini olarak ayarlayın `Windows` .</span><span class="sxs-lookup"><span data-stu-id="3855e-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="3855e-167">Bir <`message`> öğesi ekleyin ve `clientCredentialType` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3855e-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="3855e-168">Aşağıdaki kod, değeri bir sertifika olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3855e-168">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3855e-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3855e-169">See also</span></span>

- [<span data-ttu-id="3855e-170">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3855e-170">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="3855e-171">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3855e-171">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="3855e-172">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3855e-172">Securing Services and Clients</span></span>](securing-services-and-clients.md)
