---
title: "&lt;ws2007HttpBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 355fa3a7031c9650d52d258b9d5ef67b291e6e17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="d4c8d-102">&lt;ws2007HttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="d4c8d-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="d4c8d-103">İle kullanılan güvenlik ayarlarını temsil eden [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="d4c8d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d4c8d-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-105">\<bindings></span></span>  
<span data-ttu-id="d4c8d-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="d4c8d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-107">\<binding></span></span>  
<span data-ttu-id="d4c8d-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c8d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4c8d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4c8d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4c8d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4c8d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4c8d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4c8d-112">Attributes</span></span>  
  
|<span data-ttu-id="d4c8d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d4c8d-113">Attribute</span></span>|<span data-ttu-id="d4c8d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4c8d-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d4c8d-115">-İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-115">-   Optional.</span></span> <span data-ttu-id="d4c8d-116">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d4c8d-117">Varsayılan, `Message` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="d4c8d-118">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d4c8d-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="d4c8d-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="d4c8d-120">Değer</span><span class="sxs-lookup"><span data-stu-id="d4c8d-120">Value</span></span>|<span data-ttu-id="d4c8d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4c8d-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="d4c8d-122">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="d4c8d-123">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="d4c8d-124">Hizmet Güvenli Yuva Katmanı (SSL) sertifikaları ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="d4c8d-125">HTTPS kullanarak ileti tamamen güvenlidir ve hizmet hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="d4c8d-126">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="d4c8d-127">Güvenlik SOAP ileti güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="d4c8d-128">Varsayılan olarak, SOAP gövdesi imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="d4c8d-129">Bu mod hizmet kimlik bilgilerini bant, kullanmak için algoritma paketini dışında istemcide kullanılabilir olup olmadığı gibi özellikleri, çeşitli sunar ve hangi düzeyde koruma ileti gövdesi uygulamak için <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="d4c8d-130">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="d4c8d-131">Bu modda, HTTPS bütünlüğü, gizlilik ve sunucu kimlik doğrulaması sağlar ve istemci kimlik doğrulaması SOAP iletisi güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="d4c8d-132">Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturumu boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4c8d-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4c8d-133">Child Elements</span></span>  
  
|<span data-ttu-id="d4c8d-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4c8d-134">Element</span></span>|<span data-ttu-id="d4c8d-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4c8d-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4c8d-136">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="d4c8d-137">Taşıma güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-137">Defines the transport security settings.</span></span> <span data-ttu-id="d4c8d-138">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="d4c8d-139">Bu ayarlar yalnızca modu taşımaya ayarlandığında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="d4c8d-140">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="d4c8d-141">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-141">Defines the security settings for the message.</span></span> <span data-ttu-id="d4c8d-142">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="d4c8d-143">Aktarım katmanına modu ayarlandığında bu ayarları uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4c8d-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4c8d-144">Parent Elements</span></span>  
  
|<span data-ttu-id="d4c8d-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4c8d-145">Element</span></span>|<span data-ttu-id="d4c8d-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4c8d-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4c8d-147">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="d4c8d-148">HTTP taşıma uygulamaları için güvenli bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4c8d-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4c8d-149">Remarks</span></span>  
 <span data-ttu-id="d4c8d-150">Bu öğe WS - uygulama hizmetleri ile birlikte çalışma için tasarlanmış * belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-150">This element is designed for interoperation with services that implement WS-* specifications.</span></span> <span data-ttu-id="d4c8d-151">Bu bağlama için taşıma güvenliği, HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) vardır.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c8d-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4c8d-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="d4c8d-153">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d4c8d-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d4c8d-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d4c8d-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d4c8d-155">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4c8d-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d4c8d-156">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="d4c8d-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d4c8d-157">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d4c8d-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
