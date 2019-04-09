---
title: <security> , <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 68d3aa4da793e0338c2b0b704335bafce7cc3e31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073955"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="dcd01-102">\<Güvenlik >, \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="dcd01-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="dcd01-103">Güvenlik özelliklerini gösteren [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="dcd01-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="dcd01-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dcd01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dcd01-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="dcd01-105">\<bindings></span></span>  
<span data-ttu-id="dcd01-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="dcd01-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="dcd01-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="dcd01-107">\<binding></span></span>  
<span data-ttu-id="dcd01-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="dcd01-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd01-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcd01-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcd01-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcd01-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dcd01-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dcd01-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcd01-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dcd01-112">Attributes</span></span>  
  
|<span data-ttu-id="dcd01-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dcd01-113">Attribute</span></span>|<span data-ttu-id="dcd01-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcd01-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcd01-115">mod</span><span class="sxs-lookup"><span data-stu-id="dcd01-115">mode</span></span>|<span data-ttu-id="dcd01-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dcd01-116">-   Optional.</span></span> <span data-ttu-id="dcd01-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcd01-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="dcd01-118">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="dcd01-118">The default is `Message`.</span></span><br /><span data-ttu-id="dcd01-119">-Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="dcd01-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="dcd01-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="dcd01-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="dcd01-121">Değer</span><span class="sxs-lookup"><span data-stu-id="dcd01-121">Value</span></span>|<span data-ttu-id="dcd01-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcd01-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dcd01-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="dcd01-123">None</span></span>|<span data-ttu-id="dcd01-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="dcd01-124">Security is disabled.</span></span>|  
|<span data-ttu-id="dcd01-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="dcd01-125">Transport</span></span>|<span data-ttu-id="dcd01-126">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dcd01-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="dcd01-127">Hizmet SSL sertifikaları ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dcd01-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="dcd01-128">İleti tamamen HTTPS kullanan güvenli ve hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="dcd01-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="dcd01-129">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dcd01-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="dcd01-130">' ın [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="dcd01-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="dcd01-131">İleti</span><span class="sxs-lookup"><span data-stu-id="dcd01-131">Message</span></span>|<span data-ttu-id="dcd01-132">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dcd01-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="dcd01-133">Varsayılan olarak, SOAP gövdesi şifreli ve imza var.</span><span class="sxs-lookup"><span data-stu-id="dcd01-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="dcd01-134">Çeşitli hizmet kimlik bilgilerini kullanmak için algoritma paketini olan bant dışı istemci kullanılabilir olup gibi özellikler, bu mod sunar ve ileti gövdesi Security.Message özelliği uygulamak için koruma düzeyini.</span><span class="sxs-lookup"><span data-stu-id="dcd01-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="dcd01-135">İstemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="dcd01-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="dcd01-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="dcd01-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="dcd01-137">Bu modda, HTTPS kimlik doğrulaması bütünlüğü ve gizliliği sağlar ve istemci kimlik doğrulaması SOAP ileti güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="dcd01-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="dcd01-138">Varsayılan olarak, istemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="dcd01-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcd01-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcd01-139">Child Elements</span></span>  
  
|<span data-ttu-id="dcd01-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="dcd01-140">Element</span></span>|<span data-ttu-id="dcd01-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcd01-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcd01-142">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="dcd01-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="dcd01-143">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dcd01-143">Defines the transport security settings.</span></span> <span data-ttu-id="dcd01-144">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="dcd01-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="dcd01-145">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="dcd01-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="dcd01-146">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dcd01-146">Defines the security settings for the message.</span></span> <span data-ttu-id="dcd01-147">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü.</span><span class="sxs-lookup"><span data-stu-id="dcd01-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcd01-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcd01-148">Parent Elements</span></span>  
  
|<span data-ttu-id="dcd01-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="dcd01-149">Element</span></span>|<span data-ttu-id="dcd01-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcd01-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcd01-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="dcd01-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="dcd01-152">HTTP taşıma uygulamalar için güvenli bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="dcd01-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcd01-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcd01-153">Remarks</span></span>  
 <span data-ttu-id="dcd01-154">WSHttpBinding sınıfı WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmış \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="dcd01-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="dcd01-155">Bu bağlama için Aktarım güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) olan.</span><span class="sxs-lookup"><span data-stu-id="dcd01-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd01-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcd01-156">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="dcd01-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dcd01-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dcd01-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="dcd01-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="dcd01-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dcd01-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dcd01-160">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="dcd01-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dcd01-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="dcd01-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
