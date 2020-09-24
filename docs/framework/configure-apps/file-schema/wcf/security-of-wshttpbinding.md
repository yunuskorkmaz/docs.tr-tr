---
title: <security> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 9f984759fb52242bf8030a101b567c14627dd314
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158701"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="6489b-102">\<security> / \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6489b-102">\<security> of \<wsHttpBinding></span></span>

<span data-ttu-id="6489b-103">Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="6489b-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="6489b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6489b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6489b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6489b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6489b-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="6489b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6489b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6489b-107">Attributes</span></span>  
  
|<span data-ttu-id="6489b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6489b-108">Attribute</span></span>|<span data-ttu-id="6489b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6489b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6489b-110">mod</span><span class="sxs-lookup"><span data-stu-id="6489b-110">mode</span></span>|<span data-ttu-id="6489b-111">Seçim.</span><span class="sxs-lookup"><span data-stu-id="6489b-111">-   Optional.</span></span> <span data-ttu-id="6489b-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6489b-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6489b-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="6489b-113">The default is `Message`.</span></span><br /><span data-ttu-id="6489b-114">-Bu öznitelik türündedir <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="6489b-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6489b-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="6489b-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="6489b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="6489b-116">Value</span></span>|<span data-ttu-id="6489b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6489b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6489b-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6489b-118">None</span></span>|<span data-ttu-id="6489b-119">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6489b-119">Security is disabled.</span></span>|  
|<span data-ttu-id="6489b-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="6489b-120">Transport</span></span>|<span data-ttu-id="6489b-121">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6489b-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="6489b-122">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6489b-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="6489b-123">İleti HTTPS kullanılarak tamamen güvenlidir ve hizmetin SSL sertifikası kullanılarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6489b-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6489b-124">İstemci kimlik doğrulaması özniteliği aracılığıyla denetlenir `ClientCredentials` .</span><span class="sxs-lookup"><span data-stu-id="6489b-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="6489b-125">[\<transport>](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6489b-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="6489b-126">İleti</span><span class="sxs-lookup"><span data-stu-id="6489b-126">Message</span></span>|<span data-ttu-id="6489b-127">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6489b-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6489b-128">Varsayılan olarak, SOAP gövdesi şifrelenir ve Imzalanır.</span><span class="sxs-lookup"><span data-stu-id="6489b-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="6489b-129">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketinin ve güvenlik. Message özelliği aracılığıyla ileti gövdesine hangi koruma düzeyini uygulayamayacağı gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="6489b-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="6489b-130">Oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="6489b-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="6489b-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6489b-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="6489b-132">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="6489b-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="6489b-133">Varsayılan olarak, oturum başına istemci kimlik doğrulaması gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="6489b-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6489b-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6489b-134">Child Elements</span></span>  
  
|<span data-ttu-id="6489b-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="6489b-135">Element</span></span>|<span data-ttu-id="6489b-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6489b-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="6489b-137">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6489b-137">Defines the transport security settings.</span></span> <span data-ttu-id="6489b-138">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="6489b-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="6489b-139">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6489b-139">Defines the security settings for the message.</span></span> <span data-ttu-id="6489b-140">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="6489b-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6489b-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6489b-141">Parent Elements</span></span>  
  
|<span data-ttu-id="6489b-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="6489b-142">Element</span></span>|<span data-ttu-id="6489b-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6489b-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="6489b-144">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="6489b-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6489b-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6489b-145">Remarks</span></span>  

 <span data-ttu-id="6489b-146">WSHttpBinding sınıfı, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6489b-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="6489b-147">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="6489b-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6489b-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6489b-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="6489b-149">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6489b-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6489b-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6489b-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6489b-151">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6489b-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6489b-152">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6489b-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
