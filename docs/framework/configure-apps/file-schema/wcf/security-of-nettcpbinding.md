---
title: '&lt;netTcpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
ms.openlocfilehash: 045fb60f6ae0fb54dce7fd9bc8c634caee5fddcd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205336"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="9abd5-102">&lt;netTcpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="9abd5-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="9abd5-103">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9abd5-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="9abd5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9abd5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9abd5-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9abd5-105">\<bindings></span></span>  
<span data-ttu-id="9abd5-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9abd5-106">\<netTcpBinding></span></span>  
<span data-ttu-id="9abd5-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9abd5-107">\<binding></span></span>  
<span data-ttu-id="9abd5-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9abd5-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abd5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9abd5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9abd5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9abd5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9abd5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9abd5-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9abd5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9abd5-112">Attributes</span></span>  
  
|<span data-ttu-id="9abd5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9abd5-113">Attribute</span></span>|<span data-ttu-id="9abd5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9abd5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9abd5-115">mod</span><span class="sxs-lookup"><span data-stu-id="9abd5-115">mode</span></span>|<span data-ttu-id="9abd5-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9abd5-116">Optional.</span></span> <span data-ttu-id="9abd5-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="9abd5-118">Geçerli değerler, aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-118">Valid values are shown below.</span></span> <span data-ttu-id="9abd5-119">Varsayılan değer `Transport` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="9abd5-120">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9abd5-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9abd5-121">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="9abd5-121">mode Attribute</span></span>  
  
|<span data-ttu-id="9abd5-122">Değer</span><span class="sxs-lookup"><span data-stu-id="9abd5-122">Value</span></span>|<span data-ttu-id="9abd5-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9abd5-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9abd5-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="9abd5-124">None</span></span>|<span data-ttu-id="9abd5-125">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9abd5-125">Security is disabled.</span></span>|  
|<span data-ttu-id="9abd5-126">Taşıma</span><span class="sxs-lookup"><span data-stu-id="9abd5-126">Transport</span></span>|<span data-ttu-id="9abd5-127">Aktarım güvenliği TLS TCP veya SPNego kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9abd5-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="9abd5-128">Hizmet, SSL sertifikalarıyla yapılandırılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="9abd5-129">Bu mod koruma düzeyiyle denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9abd5-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="9abd5-130">İleti</span><span class="sxs-lookup"><span data-stu-id="9abd5-130">Message</span></span>|<span data-ttu-id="9abd5-131">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9abd5-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="9abd5-132">Varsayılan olarak, SOAP gövdesi imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="9abd5-133">Çeşitli hizmet kimlik bilgilerini kullanmak için algoritma paketini olan bant dışı istemci kullanılabilir olup gibi özellikler, bu mod sunar ve ileti gövdesi uygulamak için koruma düzeyini.</span><span class="sxs-lookup"><span data-stu-id="9abd5-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="9abd5-134">İstemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="9abd5-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="9abd5-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="9abd5-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="9abd5-136">Aktarım güvenliği ile ileti güvenliği amacıyla birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="9abd5-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="9abd5-137">Aktarım güvenliği TCP veya SPNego üzerinden TLS tarafından sağlanır ve sunucu kimlik doğrulaması bütünlüğü ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="9abd5-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="9abd5-138">SOAP ileti güvenliği, istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="9abd5-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="9abd5-139">Varsayılan olarak, istemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="9abd5-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9abd5-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9abd5-140">Child Elements</span></span>  
  
|<span data-ttu-id="9abd5-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="9abd5-141">Element</span></span>|<span data-ttu-id="9abd5-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9abd5-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9abd5-143">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="9abd5-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="9abd5-144">Taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9abd5-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="9abd5-145">Bu öğe türünde <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9abd5-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="9abd5-146">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="9abd5-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="9abd5-147">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9abd5-147">Defines the security settings for the message.</span></span> <span data-ttu-id="9abd5-148">Bu öğe türünde <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="9abd5-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9abd5-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9abd5-149">Parent Elements</span></span>  
  
|<span data-ttu-id="9abd5-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="9abd5-150">Element</span></span>|<span data-ttu-id="9abd5-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9abd5-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9abd5-152">bağlama</span><span class="sxs-lookup"><span data-stu-id="9abd5-152">binding</span></span>|<span data-ttu-id="9abd5-153">Bağlama öğesi [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9abd5-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9abd5-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9abd5-154">Remarks</span></span>  
 <span data-ttu-id="9abd5-155">Her standart bağlamaları parametreleri aktarımı güvenlik gereksinimleri kontrol etmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="9abd5-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="9abd5-156">Bu parametreler, genelde ileti düzeyi veya aktarım düzeyi güvenlik kullanılıp kullanılmadığını ve istemci kimlik bilgisi türü seçimi belirlenen güvenlik modu içerir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="9abd5-157">Bu parametreleri mevcut bir kanal yığını uygun güvenlik ile oluşturulmuş seçenekleri seçimi temel.</span><span class="sxs-lookup"><span data-stu-id="9abd5-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="9abd5-158">Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bağlamalar, bazı yaygın senaryo gereksinimleri karşılamak için tasarlanan bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="9abd5-159">Her biri bu bağlamaları belirli bazı hedeflenen senaryoları için güvenlik gereksinimlerini belirtilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9abd5-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="9abd5-160">Bu yapılandırma öğesi için güvenlik özelliklerini sağlayan `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="9abd5-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="9abd5-161">Çapraz makine haberleşmesi için güvenli, güvenilir ve iyileştirilmiş bağlama budur.</span><span class="sxs-lookup"><span data-stu-id="9abd5-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="9abd5-162">Varsayılan olarak TCP ileti güvenliği ve kimlik doğrulaması, güvenilirlik ve ikili ileti kodlama WS-ReliableMessaging ileti teslimi ve Windows güvenliği destekleyen bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9abd5-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abd5-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9abd5-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="9abd5-164">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9abd5-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="9abd5-165">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9abd5-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9abd5-166">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9abd5-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="9abd5-167">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="9abd5-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="9abd5-168">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9abd5-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
