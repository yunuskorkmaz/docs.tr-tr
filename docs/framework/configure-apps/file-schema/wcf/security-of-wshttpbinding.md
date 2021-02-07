---
description: 'Hakkında daha fazla bilgi <security> edinin: <wsHttpBinding>'
title: <security> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 646d49bd67b2b544ae2616f206bfdeabf7806579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683066"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="ea17e-103">\<security> / \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ea17e-103">\<security> of \<wsHttpBinding></span></span>

<span data-ttu-id="ea17e-104">Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ea17e-104">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="ea17e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea17e-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea17e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea17e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ea17e-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="ea17e-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea17e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea17e-108">Attributes</span></span>  
  
|<span data-ttu-id="ea17e-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea17e-109">Attribute</span></span>|<span data-ttu-id="ea17e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea17e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea17e-111">mod</span><span class="sxs-lookup"><span data-stu-id="ea17e-111">mode</span></span>|<span data-ttu-id="ea17e-112">Seçim.</span><span class="sxs-lookup"><span data-stu-id="ea17e-112">-   Optional.</span></span> <span data-ttu-id="ea17e-113">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea17e-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="ea17e-114">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="ea17e-114">The default is `Message`.</span></span><br /><span data-ttu-id="ea17e-115">-Bu öznitelik türündedir <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="ea17e-115">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ea17e-116">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="ea17e-116">Mode Attribute</span></span>  
  
|<span data-ttu-id="ea17e-117">Değer</span><span class="sxs-lookup"><span data-stu-id="ea17e-117">Value</span></span>|<span data-ttu-id="ea17e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea17e-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ea17e-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ea17e-119">None</span></span>|<span data-ttu-id="ea17e-120">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ea17e-120">Security is disabled.</span></span>|  
|<span data-ttu-id="ea17e-121">Aktarım</span><span class="sxs-lookup"><span data-stu-id="ea17e-121">Transport</span></span>|<span data-ttu-id="ea17e-122">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ea17e-122">Security is provided using HTTPS.</span></span> <span data-ttu-id="ea17e-123">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea17e-123">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="ea17e-124">İleti HTTPS kullanılarak tamamen güvenlidir ve hizmetin SSL sertifikası kullanılarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ea17e-124">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="ea17e-125">İstemci kimlik doğrulaması özniteliği aracılığıyla denetlenir `ClientCredentials` .</span><span class="sxs-lookup"><span data-stu-id="ea17e-125">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="ea17e-126">[\<transport>](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ea17e-126">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="ea17e-127">İleti</span><span class="sxs-lookup"><span data-stu-id="ea17e-127">Message</span></span>|<span data-ttu-id="ea17e-128">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ea17e-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="ea17e-129">Varsayılan olarak, SOAP gövdesi şifrelenir ve Imzalanır.</span><span class="sxs-lookup"><span data-stu-id="ea17e-129">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="ea17e-130">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketinin ve güvenlik. Message özelliği aracılığıyla ileti gövdesine hangi koruma düzeyini uygulayamayacağı gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="ea17e-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="ea17e-131">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="ea17e-131">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="ea17e-132">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ea17e-132">TransportWithMessageCredential</span></span>|<span data-ttu-id="ea17e-133">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea17e-133">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="ea17e-134">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="ea17e-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea17e-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea17e-135">Child Elements</span></span>  
  
|<span data-ttu-id="ea17e-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea17e-136">Element</span></span>|<span data-ttu-id="ea17e-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea17e-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="ea17e-138">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ea17e-138">Defines the transport security settings.</span></span> <span data-ttu-id="ea17e-139">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="ea17e-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="ea17e-140">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ea17e-140">Defines the security settings for the message.</span></span> <span data-ttu-id="ea17e-141">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="ea17e-141">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea17e-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea17e-142">Parent Elements</span></span>  
  
|<span data-ttu-id="ea17e-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea17e-143">Element</span></span>|<span data-ttu-id="ea17e-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea17e-144">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="ea17e-145">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="ea17e-145">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea17e-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea17e-146">Remarks</span></span>  

 <span data-ttu-id="ea17e-147">WSHttpBinding sınıfı, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ea17e-147">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="ea17e-148">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="ea17e-148">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea17e-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea17e-149">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="ea17e-150">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ea17e-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ea17e-151">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ea17e-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ea17e-152">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ea17e-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ea17e-153">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ea17e-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
