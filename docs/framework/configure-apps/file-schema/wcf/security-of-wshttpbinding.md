---
title: '&lt;wsHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: de2fc0f562b079d5310ed2cd81211e14d4257515
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468552"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="f0101-102">&lt;wsHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="f0101-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="f0101-103">Güvenlik özelliklerini gösteren [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f0101-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="f0101-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f0101-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f0101-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f0101-105">\<bindings></span></span>  
<span data-ttu-id="f0101-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f0101-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="f0101-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f0101-107">\<binding></span></span>  
<span data-ttu-id="f0101-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f0101-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0101-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0101-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0101-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0101-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0101-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0101-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0101-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0101-112">Attributes</span></span>  
  
|<span data-ttu-id="f0101-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f0101-113">Attribute</span></span>|<span data-ttu-id="f0101-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0101-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0101-115">mod</span><span class="sxs-lookup"><span data-stu-id="f0101-115">mode</span></span>|<span data-ttu-id="f0101-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f0101-116">-   Optional.</span></span> <span data-ttu-id="f0101-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0101-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="f0101-118">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f0101-118">The default is `Message`.</span></span><br /><span data-ttu-id="f0101-119">-Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f0101-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f0101-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="f0101-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="f0101-121">Değer</span><span class="sxs-lookup"><span data-stu-id="f0101-121">Value</span></span>|<span data-ttu-id="f0101-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0101-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0101-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="f0101-123">None</span></span>|<span data-ttu-id="f0101-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f0101-124">Security is disabled.</span></span>|  
|<span data-ttu-id="f0101-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="f0101-125">Transport</span></span>|<span data-ttu-id="f0101-126">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f0101-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="f0101-127">Hizmet SSL sertifikaları ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0101-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="f0101-128">İleti tamamen HTTPS kullanan güvenli ve hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="f0101-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="f0101-129">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f0101-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="f0101-130">' ın [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f0101-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="f0101-131">İleti</span><span class="sxs-lookup"><span data-stu-id="f0101-131">Message</span></span>|<span data-ttu-id="f0101-132">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f0101-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f0101-133">Varsayılan olarak, SOAP gövdesi şifreli ve imza var.</span><span class="sxs-lookup"><span data-stu-id="f0101-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="f0101-134">Çeşitli hizmet kimlik bilgilerini kullanmak için algoritma paketini olan bant dışı istemci kullanılabilir olup gibi özellikler, bu mod sunar ve ileti gövdesi Security.Message özelliği uygulamak için koruma düzeyini.</span><span class="sxs-lookup"><span data-stu-id="f0101-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="f0101-135">İstemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="f0101-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="f0101-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f0101-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="f0101-137">Bu modda, HTTPS kimlik doğrulaması bütünlüğü ve gizliliği sağlar ve istemci kimlik doğrulaması SOAP ileti güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0101-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="f0101-138">Varsayılan olarak, istemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="f0101-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0101-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0101-139">Child Elements</span></span>  
  
|<span data-ttu-id="f0101-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0101-140">Element</span></span>|<span data-ttu-id="f0101-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0101-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0101-142">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="f0101-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="f0101-143">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0101-143">Defines the transport security settings.</span></span> <span data-ttu-id="f0101-144">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="f0101-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="f0101-145">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="f0101-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="f0101-146">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0101-146">Defines the security settings for the message.</span></span> <span data-ttu-id="f0101-147">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü.</span><span class="sxs-lookup"><span data-stu-id="f0101-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0101-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0101-148">Parent Elements</span></span>  
  
|<span data-ttu-id="f0101-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0101-149">Element</span></span>|<span data-ttu-id="f0101-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0101-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0101-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f0101-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="f0101-152">HTTP taşıma uygulamalar için güvenli bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="f0101-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0101-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0101-153">Remarks</span></span>  
 <span data-ttu-id="f0101-154">WSHttpBinding sınıfı WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmış \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="f0101-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="f0101-155">Bu bağlama için Aktarım güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) olan.</span><span class="sxs-lookup"><span data-stu-id="f0101-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0101-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0101-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="f0101-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f0101-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f0101-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f0101-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f0101-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f0101-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f0101-160">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="f0101-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f0101-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f0101-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
