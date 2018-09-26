---
title: 'Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
author: BrucePerlerMS
ms.openlocfilehash: 40fe7b1fa6a61b56d5dfdde75a92834f096a8be4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082766"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="866b4-102">Nasıl yapılır: Taşıma Güveniği ve İleti Kimlik Bilgilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="866b4-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="866b4-103">Hem aktarım hem de ileti kimlik bilgileri ile bir hizmeti güvenli hale getirme en iyi şekilde hem aktarım hem de ileti güvenlik modu Windows Communication Foundation (WCF) kullanır.</span><span class="sxs-lookup"><span data-stu-id="866b4-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="866b4-104">İleti düzeyi güvenlik katı taşıma güvenlik mekanizmaları ile mümkün olmayan kimlik bilgilerini çeşitli sağlarken, toplamda bütünlüğü ve gizliliği, Aktarım Katmanı Güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="866b4-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="866b4-105">Bu konu, ileti kimlik bilgilerini kullanarak aktarım uygulamak için temel adımları gösterir. <xref:System.ServiceModel.WSHttpBinding> ve <xref:System.ServiceModel.NetTcpBinding> bağlar.</span><span class="sxs-lookup"><span data-stu-id="866b4-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="866b4-106">Güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenlik modunu ayarlama](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="866b4-106">For more information about setting the security mode, see [How to: Set the Security Mode](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="866b4-107">Güvenlik modunu ayarlama zaman `TransportWithMessageCredential`, aktarım düzeyi güvenlik sağlayan gerçek mekanizması taşıma belirler.</span><span class="sxs-lookup"><span data-stu-id="866b4-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="866b4-108">HTTP için Güvenli Yuva Katmanı (SSL) HTTP (HTTPS) üzerinden mekanizmadır; TCP için SSL TCP veya Windows üzerinde değil.</span><span class="sxs-lookup"><span data-stu-id="866b4-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="866b4-109">HTTP taşıma ise (kullanarak <xref:System.ServiceModel.WSHttpBinding>), HTTP üzerinden SSL aktarım düzeyi güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="866b4-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="866b4-110">Bu durumda, bu konunun ilerleyen bölümlerinde gösterilen şekilde bir bağlantı noktasına bağlı bir SSL sertifikasıyla hizmetini barındıran bilgisayarın yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="866b4-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="866b4-111">TCP aktarımı ise (kullanarak <xref:System.ServiceModel.NetTcpBinding>), varsayılan olarak sağlanan aktarım düzeyi güvenlik Windows Güvenlik ya da SSL TCP üzerinden olduğu.</span><span class="sxs-lookup"><span data-stu-id="866b4-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="866b4-112">TCP üzerinden SSL kullanılırken, sertifika kullanarak belirtilmelisiniz <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi, bu konunun ilerleyen bölümlerinde gösterilen şekilde.</span><span class="sxs-lookup"><span data-stu-id="866b4-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="866b4-113">WSHttpBinding, aktarım güvenliği (kodda) için bir sertifika ile kullanmak için</span><span class="sxs-lookup"><span data-stu-id="866b4-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="866b4-114">Makine üzerindeki bir bağlantı noktası bir SSL sertifikası bağlamak için HttpCfg.exe aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="866b4-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="866b4-115">Daha fazla bilgi için [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="866b4-115">For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2.  <span data-ttu-id="866b4-116">Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="866b4-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3.  <span data-ttu-id="866b4-117">Ayarlama <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="866b4-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="866b4-118">(Daha fazla bilgi için [kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.</span><span class="sxs-lookup"><span data-stu-id="866b4-118">(For more information, see [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="866b4-119">Bir örneğini oluşturmak <xref:System.Uri> sınıfı uygun bir temel adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="866b4-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="866b4-120">Not adresi "HTTPS" şeması kullanması gerekir ve makine ve SSL sertifikasını bağlı bağlantı noktası numarasını gerçek adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="866b4-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="866b4-121">(Alternatif olarak, temel adres yapılandırmasında ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="866b4-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="866b4-122">Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="866b4-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6.  <span data-ttu-id="866b4-123">Örneği oluşturmak <xref:System.ServiceModel.ServiceHost> ve çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="866b4-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="866b4-124">NetTcpBinding, (kod) aktarım güvenliği bir sertifika ile kullanmak için</span><span class="sxs-lookup"><span data-stu-id="866b4-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="866b4-125">Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="866b4-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="866b4-126">Ayarlama <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun değeri.</span><span class="sxs-lookup"><span data-stu-id="866b4-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="866b4-127">Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.</span><span class="sxs-lookup"><span data-stu-id="866b4-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3.  <span data-ttu-id="866b4-128">Bir örneğini oluşturmak <xref:System.Uri> sınıfı uygun bir temel adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="866b4-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="866b4-129">"Net.tcp" düzeni adresini kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="866b4-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="866b4-130">(Alternatif olarak, temel adres yapılandırmasında ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="866b4-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4.  <span data-ttu-id="866b4-131">Örneği oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="866b4-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5.  <span data-ttu-id="866b4-132">Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmeti için X.509 sertifikası açıkça ayarlamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="866b4-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6.  <span data-ttu-id="866b4-133">Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="866b4-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7.  <span data-ttu-id="866b4-134">Çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="866b4-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="866b4-135">NetTcpBinding Windows ile Aktarım güvenliği (kodda) kullanmak için</span><span class="sxs-lookup"><span data-stu-id="866b4-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="866b4-136">Bir örneğini oluşturmak <xref:System.ServiceModel.NetTcpBinding> ayarlayın ve sınıf <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> özelliğini <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="866b4-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="866b4-137">Windows ayarlayarak kullanılacak aktarım güvenliği <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> için <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="866b4-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="866b4-138">(Bu varsayılan olduğunu unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="866b4-138">(Note that this is the default.)</span></span>  
  
3.  <span data-ttu-id="866b4-139">Ayarlama <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> uygun değeri.</span><span class="sxs-lookup"><span data-stu-id="866b4-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="866b4-140">Aşağıdaki kod <xref:System.ServiceModel.MessageCredentialType.Certificate> değeri.</span><span class="sxs-lookup"><span data-stu-id="866b4-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="866b4-141">Bir örneğini oluşturmak <xref:System.Uri> sınıfı uygun bir temel adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="866b4-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="866b4-142">"Net.tcp" düzeni adresini kullanması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="866b4-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="866b4-143">(Alternatif olarak, temel adres yapılandırmasında ayarlayabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="866b4-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="866b4-144">Örneği oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="866b4-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6.  <span data-ttu-id="866b4-145">Kullanım <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> hizmeti için X.509 sertifikası açıkça ayarlamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="866b4-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7.  <span data-ttu-id="866b4-146">Kullanarak bir hizmet uç noktası ekleme <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="866b4-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8.  <span data-ttu-id="866b4-147">Çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="866b4-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="866b4-148">Yapılandırma kullanma</span><span class="sxs-lookup"><span data-stu-id="866b4-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="866b4-149">WSHttpBinding kullanmak için</span><span class="sxs-lookup"><span data-stu-id="866b4-149">To use the WSHttpBinding</span></span>  
  
1.  <span data-ttu-id="866b4-150">Bilgisayar bağlantı noktasına bağlı bir SSL sertifikasıyla yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="866b4-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="866b4-151">(Daha fazla bilgi için [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="866b4-151">(For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="866b4-152">Ayarlanacak gerekmez bir <`transport`> Bu yapılandırmaya sahip öğe değeri.</span><span class="sxs-lookup"><span data-stu-id="866b4-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2.  <span data-ttu-id="866b4-153">İleti düzeyi güvenliği için istemci kimlik bilgisi türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="866b4-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="866b4-154">Aşağıdaki örnek kümeleri `clientCredentialType` özniteliği <`message`> öğesine `UserName`.</span><span class="sxs-lookup"><span data-stu-id="866b4-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="866b4-155">NetTcpBinding aktarım güvenliği için bir sertifika ile kullanmak için</span><span class="sxs-lookup"><span data-stu-id="866b4-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1.  <span data-ttu-id="866b4-156">TCP üzerinden SSL için sertifikayı açıkça belirtmelisiniz `<behaviors>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="866b4-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="866b4-157">Aşağıdaki örnek, varsayılan depolama konumu (yerel makine ve kişisel depolar) sertifikayı veren tarafından sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="866b4-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2.  <span data-ttu-id="866b4-158">Ekleme bir [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) bağlamalar bölümü için</span><span class="sxs-lookup"><span data-stu-id="866b4-158">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3.  <span data-ttu-id="866b4-159">Bir bağlama öğesi ekleyin ve ayarlayın `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="866b4-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="866b4-160">Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliğini `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="866b4-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5.  <span data-ttu-id="866b4-161">Ekleme bir <`message>` öğesi ve kümesi `clientCredentialType` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="866b4-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="866b4-162">NetTcpBinding Windows ile Aktarım güvenliği için kullanılacak</span><span class="sxs-lookup"><span data-stu-id="866b4-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1.  <span data-ttu-id="866b4-163">Ekleme bir [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) bağlamalar bölümü için</span><span class="sxs-lookup"><span data-stu-id="866b4-163">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2.  <span data-ttu-id="866b4-164">Ekleme bir <`binding`> öğesi ve kümesi `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="866b4-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="866b4-165">Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliğini `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="866b4-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="866b4-166">Ekleme bir <`transport`> öğesi ve kümesi `clientCredentialType` özniteliğini `Windows`.</span><span class="sxs-lookup"><span data-stu-id="866b4-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5.  <span data-ttu-id="866b4-167">Ekleme bir <`message`> öğesi ve kümesi `clientCredentialType` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="866b4-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="866b4-168">Aşağıdaki kod, bir sertifika için değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="866b4-168">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="866b4-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="866b4-169">See Also</span></span>  
 [<span data-ttu-id="866b4-170">Nasıl yapılır: Güvenlik Modunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="866b4-170">How to: Set the Security Mode</span></span>](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [<span data-ttu-id="866b4-171">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="866b4-171">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="866b4-172">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="866b4-172">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
