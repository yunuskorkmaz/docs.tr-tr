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
ms.workload: dotnet
ms.openlocfilehash: 3afd67e7f2d42cec458db7919529e09e4607f1ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="68725-102">&lt;webHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="68725-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="68725-103">İle yapılandırılmış bir uç nokta için güvenlik gereksinimlerini belirtir bir [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="68725-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="68725-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="68725-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="68725-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="68725-105">\<bindings></span></span>  
<span data-ttu-id="68725-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="68725-106">\<webHttpBinding></span></span>  
<span data-ttu-id="68725-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="68725-107">\<binding></span></span>  
<span data-ttu-id="68725-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="68725-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68725-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68725-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68725-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68725-110">Attributes and Elements</span></span>  
 <span data-ttu-id="68725-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68725-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68725-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68725-112">Attributes</span></span>  
  
|<span data-ttu-id="68725-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="68725-113">Attribute</span></span>|<span data-ttu-id="68725-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68725-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68725-115">mod</span><span class="sxs-lookup"><span data-stu-id="68725-115">mode</span></span>|<span data-ttu-id="68725-116">Aktarım düzeyinde güvenlik veya hiçbir güvenlik bir uç noktası tarafından kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="68725-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="68725-117">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="68725-117">The default is `None`.</span></span> <span data-ttu-id="68725-118">Bu öznitelik türünde <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="68725-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="68725-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="68725-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="68725-120">Değer</span><span class="sxs-lookup"><span data-stu-id="68725-120">Value</span></span>|<span data-ttu-id="68725-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68725-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="68725-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="68725-122">None</span></span>|<span data-ttu-id="68725-123">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="68725-123">Security is disabled.</span></span>|  
|<span data-ttu-id="68725-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="68725-124">Transport</span></span>|<span data-ttu-id="68725-125">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="68725-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="68725-126">Hizmet, SSL sertifikalarıyla yapılandırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="68725-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="68725-127">HTTPS kullanarak ileti tamamen güvenlidir ve hizmet hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="68725-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="68725-128">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentialType` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="68725-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="68725-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="68725-129">TransportCredentialOnly</span></span>|<span data-ttu-id="68725-130">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="68725-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="68725-131">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="68725-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="68725-132">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68725-132">This mode should be used with caution.</span></span> <span data-ttu-id="68725-133">Burada taşıma güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması tarafından sağlanan ortamlarda kullanılmalıdır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] altyapı.</span><span class="sxs-lookup"><span data-stu-id="68725-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68725-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68725-134">Child Elements</span></span>  
  
|<span data-ttu-id="68725-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="68725-135">Element</span></span>|<span data-ttu-id="68725-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68725-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68725-137">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="68725-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="68725-138">Taşıma güvenlik ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68725-138">Defines the transport security settings.</span></span> <span data-ttu-id="68725-139">Bu öğe karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="68725-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68725-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68725-140">Parent Elements</span></span>  
  
|<span data-ttu-id="68725-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="68725-141">Element</span></span>|<span data-ttu-id="68725-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68725-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68725-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="68725-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="68725-144">Uç noktaları için yapılandırmak için kullanılan bir bağlama öğesi [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web Hizmetleri bu SOAP iletilerine yerine HTTP isteklerine yanıt.</span><span class="sxs-lookup"><span data-stu-id="68725-144">A binding element that is used to configure endpoints for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68725-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68725-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="68725-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="68725-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="68725-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="68725-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="68725-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="68725-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="68725-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="68725-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="68725-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="68725-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="68725-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="68725-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="68725-152">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="68725-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
