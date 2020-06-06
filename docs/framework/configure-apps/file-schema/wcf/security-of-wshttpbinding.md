---
title: <security> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738587"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="26c63-102">\<security> / \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="26c63-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="26c63-103">Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="26c63-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="26c63-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26c63-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26c63-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="26c63-105">Attributes and Elements</span></span>  
 <span data-ttu-id="26c63-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="26c63-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26c63-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="26c63-107">Attributes</span></span>  
  
|<span data-ttu-id="26c63-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="26c63-108">Attribute</span></span>|<span data-ttu-id="26c63-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c63-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26c63-110">mod</span><span class="sxs-lookup"><span data-stu-id="26c63-110">mode</span></span>|<span data-ttu-id="26c63-111">Seçim.</span><span class="sxs-lookup"><span data-stu-id="26c63-111">-   Optional.</span></span> <span data-ttu-id="26c63-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="26c63-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="26c63-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="26c63-113">The default is `Message`.</span></span><br /><span data-ttu-id="26c63-114">-Bu öznitelik türündedir <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="26c63-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="26c63-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="26c63-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="26c63-116">Değer</span><span class="sxs-lookup"><span data-stu-id="26c63-116">Value</span></span>|<span data-ttu-id="26c63-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c63-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="26c63-118">Yok</span><span class="sxs-lookup"><span data-stu-id="26c63-118">None</span></span>|<span data-ttu-id="26c63-119">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="26c63-119">Security is disabled.</span></span>|  
|<span data-ttu-id="26c63-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="26c63-120">Transport</span></span>|<span data-ttu-id="26c63-121">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="26c63-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="26c63-122">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="26c63-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="26c63-123">İleti HTTPS kullanılarak tamamen güvenlidir ve hizmetin SSL sertifikası kullanılarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="26c63-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="26c63-124">İstemci kimlik doğrulaması özniteliği aracılığıyla denetlenir `ClientCredentials` .</span><span class="sxs-lookup"><span data-stu-id="26c63-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="26c63-125">[\<transport>](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="26c63-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="26c63-126">İleti</span><span class="sxs-lookup"><span data-stu-id="26c63-126">Message</span></span>|<span data-ttu-id="26c63-127">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="26c63-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="26c63-128">Varsayılan olarak, SOAP gövdesi şifrelenir ve Imzalanır.</span><span class="sxs-lookup"><span data-stu-id="26c63-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="26c63-129">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketinin ve güvenlik. Message özelliği aracılığıyla ileti gövdesine hangi koruma düzeyini uygulayamayacağı gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="26c63-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="26c63-130">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="26c63-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="26c63-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="26c63-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="26c63-132">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="26c63-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="26c63-133">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="26c63-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26c63-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="26c63-134">Child Elements</span></span>  
  
|<span data-ttu-id="26c63-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="26c63-135">Element</span></span>|<span data-ttu-id="26c63-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c63-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="26c63-137">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="26c63-137">Defines the transport security settings.</span></span> <span data-ttu-id="26c63-138">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="26c63-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="26c63-139">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="26c63-139">Defines the security settings for the message.</span></span> <span data-ttu-id="26c63-140">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="26c63-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26c63-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="26c63-141">Parent Elements</span></span>  
  
|<span data-ttu-id="26c63-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="26c63-142">Element</span></span>|<span data-ttu-id="26c63-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26c63-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="26c63-144">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="26c63-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26c63-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26c63-145">Remarks</span></span>  
 <span data-ttu-id="26c63-146">WSHttpBinding sınıfı, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="26c63-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="26c63-147">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="26c63-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c63-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26c63-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="26c63-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="26c63-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="26c63-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="26c63-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="26c63-151">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="26c63-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="26c63-152">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="26c63-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
