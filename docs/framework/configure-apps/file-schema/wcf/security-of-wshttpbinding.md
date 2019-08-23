---
title: <security> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: e627a63221d0013c89495d7ff81e02047a03df89
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936503"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="6091a-102">\<\<WSHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="6091a-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="6091a-103">[ \<WSHttpBinding >](wshttpbinding.md)'nin güvenlik yeteneklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6091a-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="6091a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6091a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6091a-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6091a-105">\<bindings></span></span>  
<span data-ttu-id="6091a-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6091a-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="6091a-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6091a-107">\<binding></span></span>  
<span data-ttu-id="6091a-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="6091a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6091a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6091a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6091a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6091a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6091a-111">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="6091a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6091a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6091a-112">Attributes</span></span>  
  
|<span data-ttu-id="6091a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6091a-113">Attribute</span></span>|<span data-ttu-id="6091a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6091a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6091a-115">mod</span><span class="sxs-lookup"><span data-stu-id="6091a-115">mode</span></span>|<span data-ttu-id="6091a-116">Seçim.</span><span class="sxs-lookup"><span data-stu-id="6091a-116">-   Optional.</span></span> <span data-ttu-id="6091a-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6091a-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6091a-118">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="6091a-118">The default is `Message`.</span></span><br /><span data-ttu-id="6091a-119">-Bu öznitelik türündedir <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6091a-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6091a-120">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="6091a-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6091a-121">Değer</span><span class="sxs-lookup"><span data-stu-id="6091a-121">Value</span></span>|<span data-ttu-id="6091a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6091a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6091a-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="6091a-123">None</span></span>|<span data-ttu-id="6091a-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6091a-124">Security is disabled.</span></span>|  
|<span data-ttu-id="6091a-125">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6091a-125">Transport</span></span>|<span data-ttu-id="6091a-126">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6091a-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="6091a-127">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6091a-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="6091a-128">İleti HTTPS kullanılarak tamamen güvenlidir ve hizmetin SSL sertifikası kullanılarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6091a-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6091a-129">İstemci kimlik doğrulaması `ClientCredentials` özniteliği aracılığıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="6091a-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="6091a-130">[ >\<](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6091a-130">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="6091a-131">`Message`</span><span class="sxs-lookup"><span data-stu-id="6091a-131">Message</span></span>|<span data-ttu-id="6091a-132">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6091a-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6091a-133">Varsayılan olarak, SOAP gövdesi şifrelenir ve Imzalanır.</span><span class="sxs-lookup"><span data-stu-id="6091a-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="6091a-134">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketinin ve güvenlik. Message özelliği aracılığıyla ileti gövdesine hangi koruma düzeyini uygulayamayacağı gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="6091a-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="6091a-135">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="6091a-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="6091a-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6091a-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="6091a-137">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="6091a-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="6091a-138">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="6091a-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6091a-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6091a-139">Child Elements</span></span>  
  
|<span data-ttu-id="6091a-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="6091a-140">Element</span></span>|<span data-ttu-id="6091a-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6091a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6091a-142">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="6091a-142">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="6091a-143">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6091a-143">Defines the transport security settings.</span></span> <span data-ttu-id="6091a-144">Bu öğe <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6091a-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="6091a-145">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="6091a-145">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="6091a-146">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6091a-146">Defines the security settings for the message.</span></span> <span data-ttu-id="6091a-147">Bu öğe <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6091a-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6091a-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6091a-148">Parent Elements</span></span>  
  
|<span data-ttu-id="6091a-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="6091a-149">Element</span></span>|<span data-ttu-id="6091a-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6091a-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6091a-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6091a-151">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="6091a-152">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="6091a-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6091a-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6091a-153">Remarks</span></span>  
 <span data-ttu-id="6091a-154">WSHttpBinding sınıfı, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6091a-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="6091a-155">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="6091a-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6091a-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6091a-156">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="6091a-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6091a-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6091a-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6091a-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6091a-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6091a-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6091a-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6091a-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6091a-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6091a-161">\<binding></span></span>](../../../misc/binding.md)
