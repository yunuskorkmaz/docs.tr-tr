---
title: "&lt;netTcpBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bf42da647e598ad698bc36e6abff0d31350f3d96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="957cc-102">&lt;netTcpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="957cc-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="957cc-103">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="957cc-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="957cc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="957cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="957cc-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="957cc-105">\<bindings></span></span>  
<span data-ttu-id="957cc-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="957cc-106">\<netTcpBinding></span></span>  
<span data-ttu-id="957cc-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="957cc-107">\<binding></span></span>  
<span data-ttu-id="957cc-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="957cc-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="957cc-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="957cc-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="957cc-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="957cc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="957cc-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="957cc-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="957cc-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="957cc-112">Attributes</span></span>  
  
|<span data-ttu-id="957cc-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="957cc-113">Attribute</span></span>|<span data-ttu-id="957cc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="957cc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="957cc-115">mod</span><span class="sxs-lookup"><span data-stu-id="957cc-115">mode</span></span>|<span data-ttu-id="957cc-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="957cc-116">Optional.</span></span> <span data-ttu-id="957cc-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="957cc-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="957cc-118">Geçerli değerler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="957cc-118">Valid values are shown below.</span></span> <span data-ttu-id="957cc-119">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="957cc-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="957cc-120">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="957cc-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="957cc-121">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="957cc-121">mode Attribute</span></span>  
  
|<span data-ttu-id="957cc-122">Değer</span><span class="sxs-lookup"><span data-stu-id="957cc-122">Value</span></span>|<span data-ttu-id="957cc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="957cc-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="957cc-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="957cc-124">None</span></span>|<span data-ttu-id="957cc-125">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="957cc-125">Security is disabled.</span></span>|  
|<span data-ttu-id="957cc-126">Taşıma</span><span class="sxs-lookup"><span data-stu-id="957cc-126">Transport</span></span>|<span data-ttu-id="957cc-127">Taşıma güvenliği, TLS üzerinden TCP veya SPNego kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="957cc-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="957cc-128">Hizmet SSL sertifikalarıyla yapılandırılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="957cc-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="957cc-129">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="957cc-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="957cc-130">İleti</span><span class="sxs-lookup"><span data-stu-id="957cc-130">Message</span></span>|<span data-ttu-id="957cc-131">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="957cc-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="957cc-132">Varsayılan olarak, SOAP gövdesi imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="957cc-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="957cc-133">Bu mod hizmet kimlik bilgilerini bant, kullanmak için algoritma paketini dışında istemcide kullanılabilir olup olmadığı gibi özellikleri, çeşitli sunar ve hangi ileti gövdesi uygulamak için koruma düzeyi.</span><span class="sxs-lookup"><span data-stu-id="957cc-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="957cc-134">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="957cc-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="957cc-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="957cc-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="957cc-136">Taşıma güvenliği ile ileti güvenliği birleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="957cc-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="957cc-137">Taşıma güvenliği tarafından TLS TCP veya SPNego sağlanır ve bütünlüğü, gizlilik ve sunucu kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="957cc-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="957cc-138">SOAP iletisi güvenlik istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="957cc-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="957cc-139">Varsayılan olarak, kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır ve istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="957cc-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="957cc-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="957cc-140">Child Elements</span></span>  
  
|<span data-ttu-id="957cc-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="957cc-141">Element</span></span>|<span data-ttu-id="957cc-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="957cc-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="957cc-143">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="957cc-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="957cc-144">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="957cc-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="957cc-145">Bu öğe türünde <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="957cc-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="957cc-146">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="957cc-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="957cc-147">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="957cc-147">Defines the security settings for the message.</span></span> <span data-ttu-id="957cc-148">Bu öğe türünde <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="957cc-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="957cc-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="957cc-149">Parent Elements</span></span>  
  
|<span data-ttu-id="957cc-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="957cc-150">Element</span></span>|<span data-ttu-id="957cc-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="957cc-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="957cc-152">bağlama</span><span class="sxs-lookup"><span data-stu-id="957cc-152">binding</span></span>|<span data-ttu-id="957cc-153">Bağlama öğesi [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="957cc-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="957cc-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="957cc-154">Remarks</span></span>  
 <span data-ttu-id="957cc-155">Her standart bağlamaları parametreleri aktarımı güvenlik gereksinimleri denetlemek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="957cc-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="957cc-156">Bu parametreler genellikle ileti düzeyi veya aktarım düzeyinde güvenlik kullanılıp kullanılmadığını ve istemci kimlik bilgisi türü seçimine belirtilen güvenlik modunu içerir.</span><span class="sxs-lookup"><span data-stu-id="957cc-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="957cc-157">Bu parametreler varsa, bir kanal yığını uygun güvenlik ile oluşturulan seçenekleri seçimine dayalı olarak.</span><span class="sxs-lookup"><span data-stu-id="957cc-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="957cc-158">Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar bazı yaygın senaryo gereksinimleri karşılamak için tasarlanmış bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="957cc-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="957cc-159">Her bu bağlamaların bazı belirli hedeflenen senaryoları için güvenlik gereksinimlerini belirtimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="957cc-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="957cc-160">Bu yapılandırma öğesi için güvenlik belirtimler sağlar `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="957cc-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="957cc-161">Güvenli, güvenilir ve en iyi duruma getirilmiş bağlama makineler arası iletişim için uygun budur.</span><span class="sxs-lookup"><span data-stu-id="957cc-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="957cc-162">Varsayılan olarak TCP ileti güvenliği ve kimlik doğrulaması, WS-ReliableMessaging güvenilirlik ve ikili ileti kodlama için ileti teslimi ve Windows Güvenlik destekleyen bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="957cc-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="957cc-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="957cc-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="957cc-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="957cc-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="957cc-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="957cc-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="957cc-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="957cc-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="957cc-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="957cc-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="957cc-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="957cc-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
