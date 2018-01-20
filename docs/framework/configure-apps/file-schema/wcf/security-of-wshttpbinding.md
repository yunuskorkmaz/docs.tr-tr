---
title: "&lt;wsHttpBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: dda6e48d3d2fec7f3ad6b9dd665e8a1092a47d60
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="76103-102">&lt;wsHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="76103-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="76103-103">Güvenlik özellikleri temsil eden [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="76103-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="76103-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="76103-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="76103-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="76103-105">\<bindings></span></span>  
<span data-ttu-id="76103-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="76103-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="76103-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="76103-107">\<binding></span></span>  
<span data-ttu-id="76103-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="76103-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76103-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76103-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76103-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="76103-110">Attributes and Elements</span></span>  
 <span data-ttu-id="76103-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="76103-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76103-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="76103-112">Attributes</span></span>  
  
|<span data-ttu-id="76103-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="76103-113">Attribute</span></span>|<span data-ttu-id="76103-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76103-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76103-115">mod</span><span class="sxs-lookup"><span data-stu-id="76103-115">mode</span></span>|<span data-ttu-id="76103-116">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="76103-116">-   Optional.</span></span> <span data-ttu-id="76103-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="76103-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="76103-118">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="76103-118">The default is `Message`.</span></span><br /><span data-ttu-id="76103-119">-Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="76103-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="76103-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="76103-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="76103-121">Değer</span><span class="sxs-lookup"><span data-stu-id="76103-121">Value</span></span>|<span data-ttu-id="76103-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76103-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76103-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="76103-123">None</span></span>|<span data-ttu-id="76103-124">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="76103-124">Security is disabled.</span></span>|  
|<span data-ttu-id="76103-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="76103-125">Transport</span></span>|<span data-ttu-id="76103-126">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="76103-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="76103-127">Hizmet, SSL sertifikalarıyla yapılandırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="76103-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="76103-128">İleti tamamen HTTPS kullanan güvenli ve hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="76103-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="76103-129">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="76103-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="76103-130">[ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="76103-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="76103-131">İleti</span><span class="sxs-lookup"><span data-stu-id="76103-131">Message</span></span>|<span data-ttu-id="76103-132">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="76103-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="76103-133">Varsayılan olarak, şifrelenmiş ve imza SOAP gövdesi durumdadır.</span><span class="sxs-lookup"><span data-stu-id="76103-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="76103-134">Bu mod hizmet kimlik bilgilerini bant, kullanmak için algoritma paketini dışında istemcide kullanılabilir olup olmadığı gibi özellikleri, çeşitli sunar ve hangi Security.Message özelliği aracılığıyla ileti gövdesi uygulamak için koruma düzeyi.</span><span class="sxs-lookup"><span data-stu-id="76103-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="76103-135">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="76103-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="76103-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="76103-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="76103-137">Bu modda, HTTPS bütünlüğü, gizlilik ve sunucu kimlik doğrulaması sağlar ve istemci kimlik doğrulaması SOAP iletisi güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="76103-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="76103-138">Varsayılan olarak, kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır ve istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="76103-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76103-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="76103-139">Child Elements</span></span>  
  
|<span data-ttu-id="76103-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="76103-140">Element</span></span>|<span data-ttu-id="76103-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76103-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76103-142">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="76103-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="76103-143">Taşıma güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="76103-143">Defines the transport security settings.</span></span> <span data-ttu-id="76103-144">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="76103-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="76103-145">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="76103-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="76103-146">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="76103-146">Defines the security settings for the message.</span></span> <span data-ttu-id="76103-147">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü.</span><span class="sxs-lookup"><span data-stu-id="76103-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76103-148">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="76103-148">Parent Elements</span></span>  
  
|<span data-ttu-id="76103-149">Öğe</span><span class="sxs-lookup"><span data-stu-id="76103-149">Element</span></span>|<span data-ttu-id="76103-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76103-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76103-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="76103-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="76103-152">HTTP taşıma uygulamaları için güvenli bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="76103-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76103-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76103-153">Remarks</span></span>  
 <span data-ttu-id="76103-154">WSHttpBinding sınıfı WS - uygulama hizmetleri ile birlikte çalışma için tasarlanmıştır \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="76103-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="76103-155">Bu bağlama için taşıma güvenliği, HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) vardır.</span><span class="sxs-lookup"><span data-stu-id="76103-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76103-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76103-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="76103-157">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="76103-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="76103-158">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="76103-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="76103-159">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76103-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="76103-160">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="76103-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="76103-161">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="76103-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
