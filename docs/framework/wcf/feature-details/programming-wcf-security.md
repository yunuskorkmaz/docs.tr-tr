---
title: WCF Güvenliğini Programlama
description: Kimlik doğrulama, gizlilik ve bütünlük gibi güvenli bir WCF uygulaması oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 8e77c667dd8904c10bbab88e1413690677cef53b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244991"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="4dae3-103">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="4dae3-103">Programming WCF Security</span></span>
<span data-ttu-id="4dae3-104">Bu konuda, güvenli bir Windows Communication Foundation (WCF) uygulaması oluşturmak için kullanılan temel programlama görevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4dae3-104">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="4dae3-105">Bu konu, toplu olarak *Aktarım güvenliği*olarak bilinen kimlik doğrulama, gizlilik ve bütünlüğü içerir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-105">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="4dae3-106">Bu konu, yetkilendirmeyi kapsamaz (kaynaklara veya hizmetlere erişimin denetimi); Yetkilendirme hakkında bilgi için bkz. [Yetkilendirme](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="4dae3-106">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4dae3-107">Özellikle WCF ile ilgili olarak güvenlik kavramlarına değerli bir giriş için, [Web Hizmetleri geliştirmeleri (WVAS) 3,0 Için senaryolar, desenler ve uygulama KıLAVUZLARıNDAKI](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10))MSDN 'de bulunan desenler ve uygulamalar öğreticilerine bakın.</span><span class="sxs-lookup"><span data-stu-id="4dae3-107">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="4dae3-108">WCF güvenliğini programlama, aşağıdaki üç adımı temel alır: güvenlik modu, istemci kimlik bilgileri türü ve kimlik bilgisi değerleri.</span><span class="sxs-lookup"><span data-stu-id="4dae3-108">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="4dae3-109">Bu adımları kod veya yapılandırma aracılığıyla yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dae3-109">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="4dae3-110">Güvenlik modunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="4dae3-110">Setting the Security Mode</span></span>  
 <span data-ttu-id="4dae3-111">Aşağıda, WCF 'de güvenlik moduyla programlama için genel adımlar açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="4dae3-111">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="4dae3-112">Uygulama gereksinimlerinize uygun olan önceden tanımlanmış bağlamalardan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="4dae3-112">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="4dae3-113">Bağlama seçeneklerinin bir listesi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="4dae3-113">For a list of the binding choices, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="4dae3-114">Varsayılan olarak, neredeyse her bağlamada Güvenlik etkindir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-114">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="4dae3-115">Tek istisna, <xref:System.ServiceModel.BasicHttpBinding> sınıftır (yapılandırma,, [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).</span><span class="sxs-lookup"><span data-stu-id="4dae3-115">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="4dae3-116">Seçtiğiniz bağlama, taşımayı belirler.</span><span class="sxs-lookup"><span data-stu-id="4dae3-116">The binding you select determines the transport.</span></span> <span data-ttu-id="4dae3-117">Örneğin, <xref:System.ServiceModel.WSHttpBinding> taşıma olarak http 'yi kullanır; <xref:System.ServiceModel.NetTcpBinding> TCP kullanır.</span><span class="sxs-lookup"><span data-stu-id="4dae3-117">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="4dae3-118">Bağlama için güvenlik modlarından birini seçin.</span><span class="sxs-lookup"><span data-stu-id="4dae3-118">Select one of the security modes for the binding.</span></span> <span data-ttu-id="4dae3-119">Seçtiğiniz bağlamanın kullanılabilir mod seçimlerini belirlediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4dae3-119">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="4dae3-120">Örneğin, <xref:System.ServiceModel.WSDualHttpBinding> Aktarım güvenliğine izin vermez (bir seçenek değildir).</span><span class="sxs-lookup"><span data-stu-id="4dae3-120">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="4dae3-121">Benzer şekilde, <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ne ne de <xref:System.ServiceModel.NetNamedPipeBinding> ileti güvenliği izin vermez.</span><span class="sxs-lookup"><span data-stu-id="4dae3-121">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="4dae3-122">Üç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="4dae3-122">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="4dae3-123">Taşıma güvenliği, seçtiğiniz bağlamanın kullandığı mekanizmaya bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4dae3-123">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="4dae3-124">Örneğin, kullanıyorsanız, `WSHttpBinding` güvenlik mekanizması Güvenli Yuva Katmanı (SSL) (aynı zamanda https Protokolü mekanizması) olur.</span><span class="sxs-lookup"><span data-stu-id="4dae3-124">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="4dae3-125">Genel olarak, aktarım güvenliğinin temel avantajı, hangi taşımanın kullanıldığı önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-125">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="4dae3-126">Ancak, bu iki sınırlamalara sahiptir: ilki, taşıma mekanizmasının bir kullanıcının kimliğini doğrulamak için kullanılan kimlik bilgisi türünü belirlemesi.</span><span class="sxs-lookup"><span data-stu-id="4dae3-126">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="4dae3-127">Bu, yalnızca bir hizmetin farklı kimlik bilgilerini talep eden diğer hizmetlerle birlikte çalışması gerektiğinde bir dezavantajdır.</span><span class="sxs-lookup"><span data-stu-id="4dae3-127">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="4dae3-128">İkincisi ise, güvenlik ileti düzeyinde uygulanmadığından, güvenlik, uçtan uca değil, atlama bir şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4dae3-128">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="4dae3-129">Bu ikinci sınırlama yalnızca istemci ve hizmet arasındaki ileti yolu aracılar içeriyorsa bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="4dae3-129">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="4dae3-130">Hangi taşımanın kullanılacağı hakkında daha fazla bilgi için bkz. [bir taşıma seçme](choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="4dae3-130">For more information about which transport to use, see [Choosing a Transport](choosing-a-transport.md).</span></span> <span data-ttu-id="4dae3-131">Taşıma güvenliğini kullanma hakkında daha fazla bilgi için bkz. [Transport Security Overview](transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4dae3-131">For more information about using transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="4dae3-132">İleti güvenliği her iletinin, iletiyi güvenli tutmak için gerekli üst bilgileri ve verileri içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-132">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="4dae3-133">Üst bilgilerin bileşimi değiştiğinden, istediğiniz sayıda kimlik bilgilerini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dae3-133">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="4dae3-134">Bu, bir taşıma mekanizmasının sağlayamediği belirli bir kimlik bilgisi türünü talep eden diğer hizmetlerle birlikte çalışıyorsanız veya ileti, her hizmetin farklı bir kimlik bilgisi türü talep ettiği birden fazla hizmetle birlikte kullanılması gerekiyorsa bir faktör haline gelir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-134">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="4dae3-135">Daha fazla bilgi için bkz. [Ileti güvenliği](message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="4dae3-135">For more information, see [Message Security](message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="4dae3-136">Bu seçim, ileti aktarımını güvenli hale getirmek için aktarım katmanını kullanır, her ileti diğer hizmetlere gereken zengin kimlik bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-136">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="4dae3-137">Bu, aktarım güvenliğinin performans avantajlarından yararlanarak ileti güvenliğinin zengin kimlik bilgileri avantajını birleştirir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-137">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="4dae3-138">Bu, aşağıdaki bağlamalarla kullanılabilir: <xref:System.ServiceModel.BasicHttpBinding> , <xref:System.ServiceModel.WSFederationHttpBinding> , <xref:System.ServiceModel.NetPeerTcpBinding> ve <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="4dae3-138">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="4dae3-139">HTTP için Transport Security 'yi (diğer bir deyişle, HTTPS) kullanmaya karar verirseniz, ana bilgisayarı bir SSL sertifikası ile yapılandırmanız ve bir bağlantı noktasında SSL 'yi etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-139">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="4dae3-140">Daha fazla bilgi için bkz. [http aktarım güvenliği](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="4dae3-140">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="4dae3-141">Kullanıyorsanız <xref:System.ServiceModel.WSHttpBinding> ve güvenli bir oturum oluşturmanız gerekmiyorsa, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğini olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="4dae3-141">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="4dae3-142">İstemci ve hizmet simetrik anahtar kullanarak bir kanal oluştururken güvenli bir oturum oluşur (iletişim kutusu kapatılıncaya kadar hem istemci hem de sunucu bir konuşma uzunluğu için aynı anahtarı kullanır).</span><span class="sxs-lookup"><span data-stu-id="4dae3-142">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="4dae3-143">Istemci kimlik bilgisi türünü ayarlama</span><span class="sxs-lookup"><span data-stu-id="4dae3-143">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="4dae3-144">Uygun şekilde bir istemci kimlik bilgisi türü seçin.</span><span class="sxs-lookup"><span data-stu-id="4dae3-144">Select a client credential type as appropriate.</span></span> <span data-ttu-id="4dae3-145">Daha fazla bilgi için bkz. [kimlik bilgisi türü seçme](selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="4dae3-145">For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).</span></span> <span data-ttu-id="4dae3-146">Aşağıdaki istemci kimlik bilgisi türleri kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4dae3-146">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="4dae3-147">Modu nasıl ayarlayadığınıza bağlı olarak, kimlik bilgisi türünü ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-147">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="4dae3-148">Örneğin, `wsHttpBinding` öğesini seçtiyseniz ve modunu "ileti" olarak ayarladıysanız, `clientCredentialType` `None` `Windows` `UserName` `Certificate` `IssuedToken` aşağıdaki yapılandırma örneğinde gösterildiği gibi ileti öğesinin özniteliğini aşağıdaki değerlerden birine de ayarlayabilirsiniz:,,,, ve.</span><span class="sxs-lookup"><span data-stu-id="4dae3-148">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4dae3-149">Veya kodda:</span><span class="sxs-lookup"><span data-stu-id="4dae3-149">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="4dae3-150">Hizmet kimlik bilgisi değerlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="4dae3-150">Setting Service Credential Values</span></span>  
 <span data-ttu-id="4dae3-151">Bir istemci kimlik bilgisi türünü seçtikten sonra, hizmet ve İstemcinin kullanacağı gerçek kimlik bilgilerini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-151">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="4dae3-152">Hizmette, kimlik bilgileri sınıfı kullanılarak ayarlanır <xref:System.ServiceModel.Description.ServiceCredentials> ve <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> sınıfının özelliği tarafından döndürülür <xref:System.ServiceModel.ServiceHostBase> .</span><span class="sxs-lookup"><span data-stu-id="4dae3-152">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="4dae3-153">Kullanımdaki bağlama hizmet kimlik bilgisi türünü, seçilen güvenlik modunu ve istemci kimlik bilgisinin türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="4dae3-153">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="4dae3-154">Aşağıdaki kod, bir hizmet kimlik bilgileri için bir sertifika ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4dae3-154">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="4dae3-155">Istemci kimlik bilgisi değerlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="4dae3-155">Setting Client Credential Values</span></span>  
 <span data-ttu-id="4dae3-156">İstemcisinde, <xref:System.ServiceModel.Description.ClientCredentials> sınıfını kullanarak ve sınıfının özelliği tarafından döndürülen istemci kimlik bilgileri değerlerini ayarlayın <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> .</span><span class="sxs-lookup"><span data-stu-id="4dae3-156">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="4dae3-157">Aşağıdaki kod, bir sertifikayı TCP protokolünü kullanarak bir istemci üzerinde kimlik bilgileri olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4dae3-157">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4dae3-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dae3-158">See also</span></span>

- [<span data-ttu-id="4dae3-159">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="4dae3-159">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="4dae3-160">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="4dae3-160">Common Security Scenarios</span></span>](common-security-scenarios.md)
