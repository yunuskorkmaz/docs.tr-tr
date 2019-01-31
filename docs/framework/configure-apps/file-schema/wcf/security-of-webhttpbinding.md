---
title: <security> , <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 7f714ffb89d5ff990239bd1a02ffaeead4ad7d91
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278804"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="ff982-102">\<Güvenlik >, \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ff982-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="ff982-103">Yapılandırılmış uç noktaya ilişkin güvenlik gereksinimlerini belirleyen bir [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ff982-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="ff982-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ff982-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff982-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ff982-105">\<bindings></span></span>  
<span data-ttu-id="ff982-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ff982-106">\<webHttpBinding></span></span>  
<span data-ttu-id="ff982-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ff982-107">\<binding></span></span>  
<span data-ttu-id="ff982-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ff982-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff982-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff982-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff982-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff982-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff982-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ff982-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff982-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ff982-112">Attributes</span></span>  
  
|<span data-ttu-id="ff982-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ff982-113">Attribute</span></span>|<span data-ttu-id="ff982-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff982-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff982-115">mod</span><span class="sxs-lookup"><span data-stu-id="ff982-115">mode</span></span>|<span data-ttu-id="ff982-116">Aktarım düzeyi güvenlik veya hiçbir güvenlik bir uç noktası tarafından kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff982-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="ff982-117">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="ff982-117">The default is `None`.</span></span> <span data-ttu-id="ff982-118">Bu öznitelik türünde <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ff982-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ff982-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="ff982-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="ff982-120">Değer</span><span class="sxs-lookup"><span data-stu-id="ff982-120">Value</span></span>|<span data-ttu-id="ff982-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff982-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ff982-122">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ff982-122">None</span></span>|<span data-ttu-id="ff982-123">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ff982-123">Security is disabled.</span></span>|  
|<span data-ttu-id="ff982-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="ff982-124">Transport</span></span>|<span data-ttu-id="ff982-125">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ff982-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="ff982-126">Hizmet SSL sertifikaları ile yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff982-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="ff982-127">İleti tamamen HTTPS kullanan güvenli ve hizmet hizmet SSL sertifikasını kullanarak istemci tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="ff982-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="ff982-128">İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentialType` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ff982-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="ff982-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="ff982-129">TransportCredentialOnly</span></span>|<span data-ttu-id="ff982-130">Bu mod, ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ff982-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="ff982-131">Bu, HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff982-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="ff982-132">Bu mod, dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff982-132">This mode should be used with caution.</span></span> <span data-ttu-id="ff982-133">Burada aktarım güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması WCF altyapısı tarafından sağlanan ortamlarda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff982-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff982-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff982-134">Child Elements</span></span>  
  
|<span data-ttu-id="ff982-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff982-135">Element</span></span>|<span data-ttu-id="ff982-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff982-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff982-137">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="ff982-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="ff982-138">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ff982-138">Defines the transport security settings.</span></span> <span data-ttu-id="ff982-139">Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.</span><span class="sxs-lookup"><span data-stu-id="ff982-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff982-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ff982-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ff982-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="ff982-141">Element</span></span>|<span data-ttu-id="ff982-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff982-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff982-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ff982-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="ff982-144">Bu SOAP iletileri yerine HTTP isteklerine yanıt Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff982-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff982-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff982-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="ff982-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ff982-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ff982-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="ff982-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ff982-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ff982-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ff982-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ff982-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ff982-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ff982-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ff982-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ff982-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="ff982-152">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="ff982-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
