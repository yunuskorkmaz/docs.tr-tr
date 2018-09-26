---
title: '&lt;ws2007HttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
author: BrucePerlerMS
ms.openlocfilehash: 6eb7497990abb29693921d601b222a3b7e87bf6c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108929"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="0c94c-102">&lt;ws2007HttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="0c94c-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="0c94c-103">İle kullanılan güvenlik ayarlarını temsil eden [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="0c94c-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="0c94c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0c94c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0c94c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0c94c-105">\<bindings></span></span>  
<span data-ttu-id="0c94c-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="0c94c-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="0c94c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0c94c-107">\<binding></span></span>  
<span data-ttu-id="0c94c-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0c94c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c94c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c94c-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c94c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c94c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0c94c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c94c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c94c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c94c-112">Attributes</span></span>  
  
|<span data-ttu-id="0c94c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c94c-113">Attribute</span></span>|<span data-ttu-id="0c94c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c94c-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="0c94c-115">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0c94c-115">-   Optional.</span></span> <span data-ttu-id="0c94c-116">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c94c-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="0c94c-117">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0c94c-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="0c94c-118">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0c94c-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0c94c-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="0c94c-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="0c94c-120">Değer</span><span class="sxs-lookup"><span data-stu-id="0c94c-120">Value</span></span>|<span data-ttu-id="0c94c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c94c-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="0c94c-122">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0c94c-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="0c94c-123">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0c94c-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="0c94c-124">Hizmet ile Güvenli Yuva Katmanı (SSL) sertifikalarını yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c94c-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="0c94c-125">İleti tamamen HTTPS kullanan güvenli ve hizmet hizmet SSL sertifikasını kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="0c94c-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="0c94c-126">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="0c94c-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="0c94c-127">SOAP ileti güveliği kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0c94c-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="0c94c-128">Varsayılan olarak, SOAP gövdesi imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="0c94c-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="0c94c-129">Çeşitli hizmet kimlik bilgilerini kullanmak için algoritma paketini olan bant dışı istemci kullanılabilir olup gibi özellikler, bu mod sunar ve ileti gövdesi ile uygulamak için koruma düzeyini <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="0c94c-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="0c94c-130">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="0c94c-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="0c94c-131">Bu modda, HTTPS kimlik doğrulaması bütünlüğü ve gizliliği sağlar ve istemci kimlik doğrulaması SOAP ileti güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c94c-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="0c94c-132">Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="0c94c-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c94c-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c94c-133">Child Elements</span></span>  
  
|<span data-ttu-id="0c94c-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c94c-134">Element</span></span>|<span data-ttu-id="0c94c-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c94c-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c94c-136">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="0c94c-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="0c94c-137">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c94c-137">Defines the transport security settings.</span></span> <span data-ttu-id="0c94c-138">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="0c94c-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="0c94c-139">Bu ayarlar, yalnızca taşıma için modu ayarlandığında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0c94c-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="0c94c-140">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="0c94c-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="0c94c-141">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c94c-141">Defines the security settings for the message.</span></span> <span data-ttu-id="0c94c-142">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü.</span><span class="sxs-lookup"><span data-stu-id="0c94c-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="0c94c-143">Taşıma imkanı kullanılarak modu ayarlandığında, bu ayarlar uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="0c94c-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c94c-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c94c-144">Parent Elements</span></span>  
  
|<span data-ttu-id="0c94c-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c94c-145">Element</span></span>|<span data-ttu-id="0c94c-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c94c-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c94c-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="0c94c-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="0c94c-148">HTTP taşıma uygulamalar için güvenli bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="0c94c-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c94c-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c94c-149">Remarks</span></span>  
 <span data-ttu-id="0c94c-150">Bu öğe, WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmıştır \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="0c94c-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="0c94c-151">Bu bağlama için Aktarım güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) olan.</span><span class="sxs-lookup"><span data-stu-id="0c94c-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c94c-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c94c-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="0c94c-153">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0c94c-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0c94c-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0c94c-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0c94c-155">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0c94c-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0c94c-156">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="0c94c-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0c94c-157">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0c94c-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
