---
title: '&lt;webHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 52146fa08ec63ef63fa996cdc09f9185b9f42e02
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489688"
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="fa3b8-102">&lt;webHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="fa3b8-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="fa3b8-103">Yapılandırılmış uç noktaya ilişkin güvenlik gereksinimlerini belirleyen bir [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fa3b8-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="fa3b8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fa3b8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa3b8-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="fa3b8-105">\<bindings></span></span>  
<span data-ttu-id="fa3b8-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="fa3b8-106">\<webHttpBinding></span></span>  
<span data-ttu-id="fa3b8-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fa3b8-107">\<binding></span></span>  
<span data-ttu-id="fa3b8-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="fa3b8-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa3b8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa3b8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa3b8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa3b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fa3b8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa3b8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa3b8-112">Attributes</span></span>  
  
|<span data-ttu-id="fa3b8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa3b8-113">Attribute</span></span>|<span data-ttu-id="fa3b8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa3b8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa3b8-115">mod</span><span class="sxs-lookup"><span data-stu-id="fa3b8-115">mode</span></span>|<span data-ttu-id="fa3b8-116">Aktarım düzeyi güvenlik veya hiçbir güvenlik bir uç noktası tarafından kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="fa3b8-117">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-117">The default is `None`.</span></span> <span data-ttu-id="fa3b8-118">Bu öznitelik türünde <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="fa3b8-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="fa3b8-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="fa3b8-120">Değer</span><span class="sxs-lookup"><span data-stu-id="fa3b8-120">Value</span></span>|<span data-ttu-id="fa3b8-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa3b8-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fa3b8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-122">None</span></span>|<span data-ttu-id="fa3b8-123">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-123">Security is disabled.</span></span>|  
|<span data-ttu-id="fa3b8-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="fa3b8-124">Transport</span></span>|<span data-ttu-id="fa3b8-125">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="fa3b8-126">Hizmet SSL sertifikaları ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="fa3b8-127">İleti tamamen HTTPS kullanan güvenli ve hizmet hizmet SSL sertifikasını kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="fa3b8-128">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentialType` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="fa3b8-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="fa3b8-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="fa3b8-129">TransportCredentialOnly</span></span>|<span data-ttu-id="fa3b8-130">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="fa3b8-131">Bu, HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="fa3b8-132">Bu mod, dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-132">This mode should be used with caution.</span></span> <span data-ttu-id="fa3b8-133">Burada aktarım güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması WCF altyapısı tarafından sağlanan ortamlarda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa3b8-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa3b8-134">Child Elements</span></span>  
  
|<span data-ttu-id="fa3b8-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa3b8-135">Element</span></span>|<span data-ttu-id="fa3b8-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa3b8-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa3b8-137">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="fa3b8-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="fa3b8-138">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-138">Defines the transport security settings.</span></span> <span data-ttu-id="fa3b8-139">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa3b8-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa3b8-140">Parent Elements</span></span>  
  
|<span data-ttu-id="fa3b8-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa3b8-141">Element</span></span>|<span data-ttu-id="fa3b8-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa3b8-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa3b8-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="fa3b8-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="fa3b8-144">Bu SOAP iletileri yerine HTTP isteklerine yanıt Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa3b8-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa3b8-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="fa3b8-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fa3b8-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fa3b8-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="fa3b8-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="fa3b8-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fa3b8-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fa3b8-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa3b8-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fa3b8-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="fa3b8-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="fa3b8-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fa3b8-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="fa3b8-152">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="fa3b8-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
