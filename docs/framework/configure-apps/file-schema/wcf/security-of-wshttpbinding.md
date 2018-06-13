---
title: '&lt;wsHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 836e920ef7c95d4a7a2b752c2f76f29d8c880e7c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750472"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="18dc2-102">&lt;wsHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="18dc2-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="18dc2-103">Güvenlik özellikleri temsil eden [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="18dc2-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="18dc2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18dc2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18dc2-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="18dc2-105">\<bindings></span></span>  
<span data-ttu-id="18dc2-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="18dc2-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="18dc2-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="18dc2-107">\<binding></span></span>  
<span data-ttu-id="18dc2-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="18dc2-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18dc2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18dc2-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">  
   <transport  
         clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string"   
      defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      defaultRealm="string" />  
   <message  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
       establishSecurityContext="Boolean"   
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18dc2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="18dc2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18dc2-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="18dc2-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18dc2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="18dc2-112">Attributes</span></span>  
  
|<span data-ttu-id="18dc2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="18dc2-113">Attribute</span></span>|<span data-ttu-id="18dc2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18dc2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18dc2-115">mod</span><span class="sxs-lookup"><span data-stu-id="18dc2-115">mode</span></span>|<span data-ttu-id="18dc2-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="18dc2-116">-   Optional.</span></span> <span data-ttu-id="18dc2-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="18dc2-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="18dc2-118">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="18dc2-118">The default is `Message`.</span></span><br /><span data-ttu-id="18dc2-119">-Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="18dc2-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="18dc2-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="18dc2-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="18dc2-121">Değer</span><span class="sxs-lookup"><span data-stu-id="18dc2-121">Value</span></span>|<span data-ttu-id="18dc2-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18dc2-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18dc2-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="18dc2-123">None</span></span>|<span data-ttu-id="18dc2-124">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="18dc2-124">Security is disabled.</span></span>|  
|<span data-ttu-id="18dc2-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="18dc2-125">Transport</span></span>|<span data-ttu-id="18dc2-126">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="18dc2-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="18dc2-127">Hizmet, SSL sertifikalarıyla yapılandırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="18dc2-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="18dc2-128">İleti tamamen HTTPS kullanan güvenli ve hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="18dc2-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="18dc2-129">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="18dc2-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="18dc2-130">[ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="18dc2-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="18dc2-131">İleti</span><span class="sxs-lookup"><span data-stu-id="18dc2-131">Message</span></span>|<span data-ttu-id="18dc2-132">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="18dc2-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="18dc2-133">Varsayılan olarak, şifrelenmiş ve imza SOAP gövdesi durumdadır.</span><span class="sxs-lookup"><span data-stu-id="18dc2-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="18dc2-134">Bu mod hizmet kimlik bilgilerini bant, kullanmak için algoritma paketini dışında istemcide kullanılabilir olup olmadığı gibi özellikleri, çeşitli sunar ve hangi Security.Message özelliği aracılığıyla ileti gövdesi uygulamak için koruma düzeyi.</span><span class="sxs-lookup"><span data-stu-id="18dc2-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="18dc2-135">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="18dc2-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="18dc2-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="18dc2-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="18dc2-137">Bu modda, HTTPS bütünlüğü, gizlilik ve sunucu kimlik doğrulaması sağlar ve istemci kimlik doğrulaması SOAP iletisi güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="18dc2-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="18dc2-138">Varsayılan olarak, kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır ve istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="18dc2-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18dc2-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="18dc2-139">Child Elements</span></span>  
  
|<span data-ttu-id="18dc2-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="18dc2-140">Element</span></span>|<span data-ttu-id="18dc2-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18dc2-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18dc2-142">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="18dc2-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="18dc2-143">Taşıma güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="18dc2-143">Defines the transport security settings.</span></span> <span data-ttu-id="18dc2-144">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="18dc2-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="18dc2-145">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="18dc2-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="18dc2-146">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="18dc2-146">Defines the security settings for the message.</span></span> <span data-ttu-id="18dc2-147">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü.</span><span class="sxs-lookup"><span data-stu-id="18dc2-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18dc2-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="18dc2-148">Parent Elements</span></span>  
  
|<span data-ttu-id="18dc2-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="18dc2-149">Element</span></span>|<span data-ttu-id="18dc2-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18dc2-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18dc2-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="18dc2-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="18dc2-152">HTTP taşıma uygulamaları için güvenli bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="18dc2-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18dc2-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18dc2-153">Remarks</span></span>  
 <span data-ttu-id="18dc2-154">WSHttpBinding sınıfı WS - uygulama hizmetleri ile birlikte çalışma için tasarlanmıştır \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="18dc2-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="18dc2-155">Bu bağlama için taşıma güvenliği, HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) vardır.</span><span class="sxs-lookup"><span data-stu-id="18dc2-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18dc2-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18dc2-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="18dc2-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="18dc2-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="18dc2-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="18dc2-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="18dc2-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="18dc2-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="18dc2-160">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="18dc2-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="18dc2-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="18dc2-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
