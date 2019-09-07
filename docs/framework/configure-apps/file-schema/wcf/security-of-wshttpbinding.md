---
title: <security> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f7a4ef98637a7c966665fdd02ad26929bd4ba6ac
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399722"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="d9578-102">\<\<WSHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d9578-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="d9578-103">[ \<WSHttpBinding >](wshttpbinding.md)'nin güvenlik yeteneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9578-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="d9578-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9578-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d9578-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d9578-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d9578-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d9578-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d9578-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d9578-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="d9578-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="d9578-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d9578-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="d9578-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9578-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9578-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9578-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9578-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d9578-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="d9578-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9578-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9578-113">Attributes</span></span>  
  
|<span data-ttu-id="d9578-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d9578-114">Attribute</span></span>|<span data-ttu-id="d9578-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9578-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9578-116">mod</span><span class="sxs-lookup"><span data-stu-id="d9578-116">mode</span></span>|<span data-ttu-id="d9578-117">Seçim.</span><span class="sxs-lookup"><span data-stu-id="d9578-117">-   Optional.</span></span> <span data-ttu-id="d9578-118">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9578-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d9578-119">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d9578-119">The default is `Message`.</span></span><br /><span data-ttu-id="d9578-120">-Bu öznitelik türündedir <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d9578-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d9578-121">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="d9578-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="d9578-122">Değer</span><span class="sxs-lookup"><span data-stu-id="d9578-122">Value</span></span>|<span data-ttu-id="d9578-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9578-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9578-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9578-124">None</span></span>|<span data-ttu-id="d9578-125">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d9578-125">Security is disabled.</span></span>|  
|<span data-ttu-id="d9578-126">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d9578-126">Transport</span></span>|<span data-ttu-id="d9578-127">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d9578-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="d9578-128">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9578-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="d9578-129">İleti HTTPS kullanılarak tamamen güvenlidir ve hizmetin SSL sertifikası kullanılarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d9578-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="d9578-130">İstemci kimlik doğrulaması `ClientCredentials` özniteliği aracılığıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="d9578-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="d9578-131">[ >\<](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d9578-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="d9578-132">`Message`</span><span class="sxs-lookup"><span data-stu-id="d9578-132">Message</span></span>|<span data-ttu-id="d9578-133">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d9578-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d9578-134">Varsayılan olarak, SOAP gövdesi şifrelenir ve Imzalanır.</span><span class="sxs-lookup"><span data-stu-id="d9578-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="d9578-135">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketinin ve güvenlik. Message özelliği aracılığıyla ileti gövdesine hangi koruma düzeyini uygulayamayacağı gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="d9578-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="d9578-136">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="d9578-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="d9578-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d9578-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="d9578-138">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9578-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="d9578-139">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="d9578-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9578-140">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9578-140">Child Elements</span></span>  
  
|<span data-ttu-id="d9578-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9578-141">Element</span></span>|<span data-ttu-id="d9578-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9578-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9578-143">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="d9578-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="d9578-144">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9578-144">Defines the transport security settings.</span></span> <span data-ttu-id="d9578-145">Bu öğe <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d9578-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="d9578-146">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="d9578-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="d9578-147">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9578-147">Defines the security settings for the message.</span></span> <span data-ttu-id="d9578-148">Bu öğe <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d9578-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9578-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9578-149">Parent Elements</span></span>  
  
|<span data-ttu-id="d9578-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9578-150">Element</span></span>|<span data-ttu-id="d9578-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9578-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9578-152">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d9578-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="d9578-153">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="d9578-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9578-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9578-154">Remarks</span></span>  
 <span data-ttu-id="d9578-155">WSHttpBinding sınıfı, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d9578-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="d9578-156">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="d9578-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9578-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9578-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="d9578-158">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d9578-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d9578-159">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d9578-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d9578-160">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d9578-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d9578-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d9578-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d9578-162">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d9578-162">\<binding></span></span>](../../../misc/binding.md)
