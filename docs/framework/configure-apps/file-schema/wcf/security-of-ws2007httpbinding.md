---
title: <security> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ab5969da6a2d7cb59c057fd5bb909add6b6398a4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399782"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="6e8d8-102">\<\<WS2007HttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="6e8d8-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="6e8d8-103">WS2007HttpBinding > öğesiyle kullanılan [ \<](ws2007httpbinding.md) güvenlik ayarlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="6e8d8-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e8d8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e8d8-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6e8d8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6e8d8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6e8d8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6e8d8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6e8d8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="6e8d8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="6e8d8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6e8d8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="6e8d8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e8d8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e8d8-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e8d8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e8d8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6e8d8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e8d8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e8d8-113">Attributes</span></span>  
  
|<span data-ttu-id="6e8d8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e8d8-114">Attribute</span></span>|<span data-ttu-id="6e8d8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e8d8-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6e8d8-116">Seçim.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-116">-   Optional.</span></span> <span data-ttu-id="6e8d8-117">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6e8d8-118">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="6e8d8-119">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6e8d8-120">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="6e8d8-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6e8d8-121">Değer</span><span class="sxs-lookup"><span data-stu-id="6e8d8-121">Value</span></span>|<span data-ttu-id="6e8d8-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e8d8-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6e8d8-123">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="6e8d8-124">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="6e8d8-125">Hizmetin Güvenli Yuva Katmanı (SSL) sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="6e8d8-126">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6e8d8-127">İstemci kimlik doğrulaması, [ \<Transport >](transport-of-ws2007httpbinding.md) öğesi `ClientCredentials` özniteliği aracılığıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="6e8d8-128">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6e8d8-129">Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="6e8d8-130">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine hangi koruma düzeyi üzerinden <xref:System.ServiceModel.Security.SecurityMessageProperty>uygulanacağını gibi çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="6e8d8-131">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="6e8d8-132">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="6e8d8-133">Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e8d8-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e8d8-134">Child Elements</span></span>  
  
|<span data-ttu-id="6e8d8-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e8d8-135">Element</span></span>|<span data-ttu-id="6e8d8-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e8d8-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e8d8-137">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="6e8d8-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="6e8d8-138">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-138">Defines the transport security settings.</span></span> <span data-ttu-id="6e8d8-139">Bu öğe <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="6e8d8-140">Bu ayarlar yalnızca, mod aktarım olarak ayarlandığında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="6e8d8-141">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="6e8d8-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="6e8d8-142">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-142">Defines the security settings for the message.</span></span> <span data-ttu-id="6e8d8-143">Bu öğe <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="6e8d8-144">Bu ayarlar, mod aktarım olarak ayarlandığında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e8d8-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e8d8-145">Parent Elements</span></span>  
  
|<span data-ttu-id="6e8d8-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e8d8-146">Element</span></span>|<span data-ttu-id="6e8d8-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e8d8-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e8d8-148">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="6e8d8-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="6e8d8-149">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e8d8-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e8d8-150">Remarks</span></span>  
 <span data-ttu-id="6e8d8-151">Bu öğe, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="6e8d8-152">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="6e8d8-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8d8-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e8d8-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="6e8d8-154">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6e8d8-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6e8d8-155">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6e8d8-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6e8d8-156">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6e8d8-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6e8d8-157">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6e8d8-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6e8d8-158">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6e8d8-158">\<binding></span></span>](../../../misc/binding.md)
