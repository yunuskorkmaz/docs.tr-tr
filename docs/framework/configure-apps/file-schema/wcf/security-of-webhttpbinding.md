---
title: "&lt;webHttpBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b3d5d00dcc79a746818975a6a8b125d3dc33933b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="0271d-102">&lt;webHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="0271d-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="0271d-103">İle yapılandırılmış bir uç nokta için güvenlik gereksinimlerini belirtir bir [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0271d-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="0271d-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0271d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0271d-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0271d-105">\<bindings></span></span>  
<span data-ttu-id="0271d-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0271d-106">\<webHttpBinding></span></span>  
<span data-ttu-id="0271d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0271d-107">\<binding></span></span>  
<span data-ttu-id="0271d-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0271d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0271d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0271d-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0271d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0271d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0271d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0271d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0271d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0271d-112">Attributes</span></span>  
  
|<span data-ttu-id="0271d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0271d-113">Attribute</span></span>|<span data-ttu-id="0271d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0271d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0271d-115">mod</span><span class="sxs-lookup"><span data-stu-id="0271d-115">mode</span></span>|<span data-ttu-id="0271d-116">Aktarım düzeyinde güvenlik veya hiçbir güvenlik bir uç noktası tarafından kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0271d-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="0271d-117">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0271d-117">The default is `None`.</span></span> <span data-ttu-id="0271d-118">Bu öznitelik türünde <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0271d-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0271d-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="0271d-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="0271d-120">Değer</span><span class="sxs-lookup"><span data-stu-id="0271d-120">Value</span></span>|<span data-ttu-id="0271d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0271d-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0271d-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="0271d-122">None</span></span>|<span data-ttu-id="0271d-123">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0271d-123">Security is disabled.</span></span>|  
|<span data-ttu-id="0271d-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="0271d-124">Transport</span></span>|<span data-ttu-id="0271d-125">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0271d-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="0271d-126">Hizmet, SSL sertifikalarıyla yapılandırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="0271d-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="0271d-127">HTTPS kullanarak ileti tamamen güvenlidir ve hizmet hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="0271d-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="0271d-128">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentialType` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0271d-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="0271d-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="0271d-129">TransportCredentialOnly</span></span>|<span data-ttu-id="0271d-130">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="0271d-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="0271d-131">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="0271d-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="0271d-132">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0271d-132">This mode should be used with caution.</span></span> <span data-ttu-id="0271d-133">Burada taşıma güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması tarafından sağlanan ortamlarda kullanılmalıdır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] altyapı.</span><span class="sxs-lookup"><span data-stu-id="0271d-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0271d-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0271d-134">Child Elements</span></span>  
  
|<span data-ttu-id="0271d-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="0271d-135">Element</span></span>|<span data-ttu-id="0271d-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0271d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0271d-137">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="0271d-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="0271d-138">Taşıma güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0271d-138">Defines the transport security settings.</span></span> <span data-ttu-id="0271d-139">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="0271d-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0271d-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0271d-140">Parent Elements</span></span>  
  
|<span data-ttu-id="0271d-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="0271d-141">Element</span></span>|<span data-ttu-id="0271d-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0271d-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0271d-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0271d-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="0271d-144">Uç noktaları için yapılandırmak için kullanılan bir bağlama öğesi [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web Hizmetleri bu SOAP iletilerine yerine HTTP isteklerine yanıt.</span><span class="sxs-lookup"><span data-stu-id="0271d-144">A binding element that is used to configure endpoints for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0271d-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0271d-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="0271d-146">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="0271d-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0271d-147">Bir kimlik bilgisi türü seçme</span><span class="sxs-lookup"><span data-stu-id="0271d-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="0271d-148">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="0271d-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0271d-149">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0271d-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0271d-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="0271d-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0271d-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0271d-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="0271d-152">WCF Web HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="0271d-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
