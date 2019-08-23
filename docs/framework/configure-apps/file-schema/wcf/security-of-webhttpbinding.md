---
title: <security> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 806cf8524ed1a1439ca85a4b918e8e486e5dc94b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936583"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="f9140-102">\<\<WebHttpBinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f9140-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="f9140-103">[ Bir\<WebHttpBinding >](webhttpbinding.md)ile yapılandırılmış bir uç noktanın güvenlik gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9140-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
 <span data-ttu-id="f9140-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9140-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9140-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f9140-105">\<bindings></span></span>  
<span data-ttu-id="f9140-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f9140-106">\<webHttpBinding></span></span>  
<span data-ttu-id="f9140-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f9140-107">\<binding></span></span>  
<span data-ttu-id="f9140-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f9140-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9140-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9140-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9140-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9140-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f9140-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9140-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9140-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9140-112">Attributes</span></span>  
  
|<span data-ttu-id="f9140-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9140-113">Attribute</span></span>|<span data-ttu-id="f9140-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9140-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9140-115">mod</span><span class="sxs-lookup"><span data-stu-id="f9140-115">mode</span></span>|<span data-ttu-id="f9140-116">Aktarım düzeyi güvenliğinin veya bir uç nokta tarafından bir güvenlik kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9140-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="f9140-117">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f9140-117">The default is `None`.</span></span> <span data-ttu-id="f9140-118">Bu öznitelik türü <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f9140-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f9140-119">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="f9140-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="f9140-120">Değer</span><span class="sxs-lookup"><span data-stu-id="f9140-120">Value</span></span>|<span data-ttu-id="f9140-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9140-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f9140-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9140-122">None</span></span>|<span data-ttu-id="f9140-123">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f9140-123">Security is disabled.</span></span>|  
|<span data-ttu-id="f9140-124">Aktarım</span><span class="sxs-lookup"><span data-stu-id="f9140-124">Transport</span></span>|<span data-ttu-id="f9140-125">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f9140-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="f9140-126">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9140-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="f9140-127">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="f9140-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="f9140-128">İstemci kimlik doğrulaması, `ClientCredentialType` [ \<> taşıma](transport-of-webhttpbinding.md)özniteliği aracılığıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="f9140-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="f9140-129">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="f9140-129">TransportCredentialOnly</span></span>|<span data-ttu-id="f9140-130">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f9140-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f9140-131">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9140-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="f9140-132">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9140-132">This mode should be used with caution.</span></span> <span data-ttu-id="f9140-133">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9140-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9140-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9140-134">Child Elements</span></span>  
  
|<span data-ttu-id="f9140-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9140-135">Element</span></span>|<span data-ttu-id="f9140-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9140-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9140-137">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="f9140-137">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="f9140-138">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9140-138">Defines the transport security settings.</span></span> <span data-ttu-id="f9140-139">Bu öğe <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f9140-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9140-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9140-140">Parent Elements</span></span>  
  
|<span data-ttu-id="f9140-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9140-141">Element</span></span>|<span data-ttu-id="f9140-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9140-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9140-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="f9140-143">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="f9140-144">SOAP iletileri yerine HTTP isteklerine yanıt veren Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="f9140-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9140-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9140-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="f9140-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f9140-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f9140-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="f9140-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f9140-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f9140-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f9140-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f9140-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f9140-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f9140-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f9140-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f9140-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="f9140-152">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="f9140-152">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
