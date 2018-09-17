---
title: '&lt;webHttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 52146fa08ec63ef63fa996cdc09f9185b9f42e02
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698516"
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="dbf8e-102">&lt;webHttpBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="dbf8e-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="dbf8e-103">Yapılandırılmış uç noktaya ilişkin güvenlik gereksinimlerini belirleyen bir [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="dbf8e-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="dbf8e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dbf8e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dbf8e-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="dbf8e-105">\<bindings></span></span>  
<span data-ttu-id="dbf8e-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="dbf8e-106">\<webHttpBinding></span></span>  
<span data-ttu-id="dbf8e-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="dbf8e-107">\<binding></span></span>  
<span data-ttu-id="dbf8e-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="dbf8e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbf8e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbf8e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbf8e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbf8e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dbf8e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbf8e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbf8e-112">Attributes</span></span>  
  
|<span data-ttu-id="dbf8e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbf8e-113">Attribute</span></span>|<span data-ttu-id="dbf8e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbf8e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbf8e-115">mod</span><span class="sxs-lookup"><span data-stu-id="dbf8e-115">mode</span></span>|<span data-ttu-id="dbf8e-116">Aktarım düzeyi güvenlik veya hiçbir güvenlik bir uç noktası tarafından kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="dbf8e-117">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-117">The default is `None`.</span></span> <span data-ttu-id="dbf8e-118">Bu öznitelik türünde <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="dbf8e-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="dbf8e-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="dbf8e-120">Değer</span><span class="sxs-lookup"><span data-stu-id="dbf8e-120">Value</span></span>|<span data-ttu-id="dbf8e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbf8e-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbf8e-122">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="dbf8e-122">None</span></span>|<span data-ttu-id="dbf8e-123">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-123">Security is disabled.</span></span>|  
|<span data-ttu-id="dbf8e-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="dbf8e-124">Transport</span></span>|<span data-ttu-id="dbf8e-125">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="dbf8e-126">Hizmet SSL sertifikaları ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="dbf8e-127">İleti tamamen HTTPS kullanan güvenli ve hizmet hizmet SSL sertifikasını kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="dbf8e-128">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentialType` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="dbf8e-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="dbf8e-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="dbf8e-129">TransportCredentialOnly</span></span>|<span data-ttu-id="dbf8e-130">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="dbf8e-131">Bu, HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="dbf8e-132">Bu mod, dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-132">This mode should be used with caution.</span></span> <span data-ttu-id="dbf8e-133">Burada aktarım güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması WCF altyapısı tarafından sağlanan ortamlarda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbf8e-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbf8e-134">Child Elements</span></span>  
  
|<span data-ttu-id="dbf8e-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbf8e-135">Element</span></span>|<span data-ttu-id="dbf8e-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbf8e-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbf8e-137">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="dbf8e-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="dbf8e-138">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-138">Defines the transport security settings.</span></span> <span data-ttu-id="dbf8e-139">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbf8e-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbf8e-140">Parent Elements</span></span>  
  
|<span data-ttu-id="dbf8e-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbf8e-141">Element</span></span>|<span data-ttu-id="dbf8e-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbf8e-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbf8e-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="dbf8e-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="dbf8e-144">Bu SOAP iletileri yerine HTTP isteklerine yanıt Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbf8e-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbf8e-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="dbf8e-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dbf8e-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="dbf8e-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="dbf8e-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="dbf8e-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="dbf8e-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dbf8e-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dbf8e-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="dbf8e-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="dbf8e-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="dbf8e-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="dbf8e-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="dbf8e-152">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="dbf8e-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
