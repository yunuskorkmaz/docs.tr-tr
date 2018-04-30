---
title: WCF Güvenliğini Programlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
caps.latest.revision: 25
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 63f5c2c61a374b92b018419c83c9429e6ad796d8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="programming-wcf-security"></a><span data-ttu-id="ed807-102">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="ed807-102">Programming WCF Security</span></span>
<span data-ttu-id="ed807-103">Bu konu güvenli oluşturmak için kullanılan temel programlama görevleri açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="ed807-103">This topic describes the fundamental programming tasks used to create a secure [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="ed807-104">Bu konu, yalnızca kimlik doğrulaması, gizliliği ve bütünlük, topluca olarak bilinen kapsar *Aktarım güvenlik*.</span><span class="sxs-lookup"><span data-stu-id="ed807-104">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="ed807-105">Bu konuda yetkilendirme (kaynaklarına veya hizmetlerine erişim denetimi); kapsamaz Yetkilendirme hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="ed807-105">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed807-106">Özellikle de hesaba için güvenlik kavramları değerli bir giriş için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], MSDN'de bulunan desenleri ve uygulamalar öğreticileri kümesini görmek [senaryoları, desenleri ve uygulama kılavuzunu Web Services Enhancements (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span><span class="sxs-lookup"><span data-stu-id="ed807-106">For a valuable introduction to security concepts, especially in regard to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span></span>  
  
 <span data-ttu-id="ed807-107">Programlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aşağıdaki üç adımı üzerinde tabanlı güvenlik: güvenlik modu, bir istemci kimlik bilgisi türü ve kimlik bilgisi değerleri.</span><span class="sxs-lookup"><span data-stu-id="ed807-107">Programming [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="ed807-108">Kod veya yapılandırma yoluyla bu adımları gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ed807-108">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="ed807-109">Güvenlik modunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="ed807-109">Setting the Security Mode</span></span>  
 <span data-ttu-id="ed807-110">Aşağıdaki güvenlik modunda'yla programlama için genel adımlar açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ed807-110">The following explains the general steps for programming with the security mode in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
1.  <span data-ttu-id="ed807-111">Uygulama gereksinimlerinize uygun önceden tanımlanmış bağlamaları birini seçin.</span><span class="sxs-lookup"><span data-stu-id="ed807-111">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="ed807-112">Bağlama tercih listesi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ed807-112">For a list of the binding choices, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="ed807-113">Varsayılan olarak etkin güvenlik neredeyse her bağlama yok.</span><span class="sxs-lookup"><span data-stu-id="ed807-113">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="ed807-114">Bir özel durum <xref:System.ServiceModel.BasicHttpBinding> sınıfı (yapılandırmayı kullanarak [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span><span class="sxs-lookup"><span data-stu-id="ed807-114">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="ed807-115">Seçtiğiniz bağlama taşıma belirler.</span><span class="sxs-lookup"><span data-stu-id="ed807-115">The binding you select determines the transport.</span></span> <span data-ttu-id="ed807-116">Örneğin, <xref:System.ServiceModel.WSHttpBinding> HTTP taşıma; kullanır <xref:System.ServiceModel.NetTcpBinding> TCP kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed807-116">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2.  <span data-ttu-id="ed807-117">Bağlama için güvenlik modlarından birini seçin.</span><span class="sxs-lookup"><span data-stu-id="ed807-117">Select one of the security modes for the binding.</span></span> <span data-ttu-id="ed807-118">Seçtiğiniz bağlama kullanılabilir modu seçenekleri belirlediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ed807-118">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="ed807-119">Örneğin, <xref:System.ServiceModel.WSDualHttpBinding> (Bu bir seçenek değil) taşıma güvenliği izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="ed807-119">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="ed807-120">Benzer şekilde, ne <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> veya <xref:System.ServiceModel.NetNamedPipeBinding> ileti güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed807-120">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="ed807-121">Üç seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="ed807-121">You have three choices:</span></span>  
  
    1.  `Transport`  
  
         <span data-ttu-id="ed807-122">Taşıma güvenliği seçmiş olduğunuz bağlama kullanan mekanizmasını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ed807-122">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="ed807-123">Örneğin, kullanıyorsanız `WSHttpBinding` güvenlik mekanizması Güvenli Yuva Katmanı (SSL) (aynı zamanda HTTPS protokolü için mekanizması) olur.</span><span class="sxs-lookup"><span data-stu-id="ed807-123">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="ed807-124">Genel olarak bakıldığında, taşıma güvenliği ana avantajı, hangi aktarım olsun, kullanmakta olduğunuz iyi verimlilik sağlar ' dir.</span><span class="sxs-lookup"><span data-stu-id="ed807-124">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="ed807-125">Ancak, iki sınırlamaları vardır: aktarım mekanizması bir kullanıcının kimliğini doğrulamak için kullanılan kimlik bilgisi türünü belirleyen ilk sunucudur.</span><span class="sxs-lookup"><span data-stu-id="ed807-125">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="ed807-126">Yalnızca hizmet kimlik bilgilerini farklı türde talep diğer hizmetlerle birlikte çalışmak gerekiyorsa bir dezavantajı budur.</span><span class="sxs-lookup"><span data-stu-id="ed807-126">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="ed807-127">İkinci güvenlik ileti düzeyinde uygulanmadığından güvenlik bir atlama atlamalı şekilde uçtan uca yerine, uygulanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ed807-127">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="ed807-128">Yalnızca istemci ile hizmet arasında ileti yolu aracılar içeriyorsa bu ikinci sınırlama bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="ed807-128">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="ed807-129">Hangi aktarım kullanılacak hakkında daha fazla bilgi için bkz: [taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="ed807-129">For more information about which transport to use, see [Choosing a Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span></span> <span data-ttu-id="ed807-130">Taşıma güvenliği kullanma hakkında daha fazla bilgi için bkz: [taşıma güvenliği genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ed807-130">For more information about using transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
    2.  `Message`  
  
         <span data-ttu-id="ed807-131">İleti güvenliği her ileti gerekli üst bilgileri içerir ve ileti tutmak için veri güvenli anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ed807-131">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="ed807-132">Üstbilgileri oluşumunu değiştiğinden, herhangi bir sayıda kimlik bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ed807-132">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="ed807-133">Bu, diğer hizmetlerle birlikte bir aktarım mekanizması sağlayamıyor bir belirli kimlik bilgisi türü bu talebi birlikte veya ileti burada her bir hizmet farklı bir kimlik bilgisi türü talep birden fazla hizmet ile birlikte kullanılmalıdır bir etmen haline gelir.</span><span class="sxs-lookup"><span data-stu-id="ed807-133">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="ed807-134">Daha fazla bilgi için bkz: [ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="ed807-134">For more information, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
    3.  `TransportWithMessageCredential`  
  
         <span data-ttu-id="ed807-135">İleti aktarma güvenliğini sağlamak için Aktarım katmanı bu seçenek kullanır, her ileti Zengin kimlik bilgilerini içerir ancak diğer hizmetlerin gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed807-135">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="ed807-136">Bu, ileti güvenliği zengin kimlik bilgilerini avantajı ile taşıma güvenliği performans avantajı birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ed807-136">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="ed807-137">Bu aşağıdaki bağlamalarla kullanılabilir: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, ve <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ed807-137">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="ed807-138">Taşıma güvenliği için HTTP (diğer bir deyişle, HTTPS) kullanmaya karar verirseniz, aynı zamanda bir SSL sertifikası ile ana bilgisayar yapılandırma ve SSL bağlantı noktası etkinleştirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed807-138">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="ed807-139">Daha fazla bilgi için bkz: [HTTP taşıma güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="ed807-139">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
4.  <span data-ttu-id="ed807-140">Kullanıyorsanız <xref:System.ServiceModel.WSHttpBinding> ve gerekmez güvenli bir oturumu ayarlamak <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="ed807-140">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="ed807-141">Simetrik anahtar (istemci ve sunucu iletişim kapatılana kadar bir konuşma uzunluğu için aynı anahtarı kullanan) kullanarak bir kanal istemci ve hizmet oluşturduğunuzda, güvenli bir oturum gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ed807-141">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="ed807-142">İstemci kimlik bilgisi türü ayarlama</span><span class="sxs-lookup"><span data-stu-id="ed807-142">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="ed807-143">Bir istemci kimlik bilgisi türü uygun şekilde seçin.</span><span class="sxs-lookup"><span data-stu-id="ed807-143">Select a client credential type as appropriate.</span></span> <span data-ttu-id="ed807-144">Daha fazla bilgi için bkz: [bir kimlik bilgisi türü seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="ed807-144">For more information, see [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span></span> <span data-ttu-id="ed807-145">Aşağıdaki istemci kimlik bilgisi türleri kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="ed807-145">The following client credential types are available:</span></span>  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 <span data-ttu-id="ed807-146">Mod nasıl ayarladığınıza bağlı olarak, kimlik bilgisi türü ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed807-146">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="ed807-147">Örneğin, seçtiğiniz `wsHttpBinding`ve ayrıca ayarlayın, sonra da "İletisi," moda ayarladıysanız `clientCredentialType` özniteliği aşağıdaki değerlerden birine ileti öğesinin: `None`, `Windows`, `UserName`, `Certificate` , ve `IssuedToken`aşağıdaki yapılandırma örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ed807-147">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ed807-148">Kod:</span><span class="sxs-lookup"><span data-stu-id="ed807-148">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="ed807-149">Hizmet kimlik bilgisi değerleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="ed807-149">Setting Service Credential Values</span></span>  
 <span data-ttu-id="ed807-150">Bir istemci kimlik bilgisi türü seçtikten sonra hizmet ve kullanmak için istemci gerçek ilişkin kimlik bilgilerini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed807-150">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="ed807-151">Hizmette kimlik bilgileri kullanılarak ayarlanan <xref:System.ServiceModel.Description.ServiceCredentials> sınıfı ve tarafından döndürülen <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği <xref:System.ServiceModel.ServiceHostBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ed807-151">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="ed807-152">Kullanımdaki bağlama hizmet kimlik bilgisi türü, seçilen güvenlik modu ve istemci kimlik bilgileri türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed807-152">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="ed807-153">Aşağıdaki kod, bir hizmeti kimlik bilgileri için bir sertifika ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed807-153">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="ed807-154">İstemci kimlik bilgileri değerlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="ed807-154">Setting Client Credential Values</span></span>  
 <span data-ttu-id="ed807-155">İstemcide, istemci kimlik bilgisi değerleri kullanarak ayarlayın <xref:System.ServiceModel.Description.ClientCredentials> sınıfı ve tarafından döndürülen <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ed807-155">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="ed807-156">Aşağıdaki kod, TCP protokolü kullanılarak bir istemcide bir kimlik bilgisi olarak bir sertifika ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed807-156">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ed807-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed807-157">See Also</span></span>  
 [<span data-ttu-id="ed807-158">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="ed807-158">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="ed807-159">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="ed807-159">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
