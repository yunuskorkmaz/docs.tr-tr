---
title: <security> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738630"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="63bdf-102">\<webHttpBinding \<güvenlik > ></span><span class="sxs-lookup"><span data-stu-id="63bdf-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="63bdf-103">[\<webHttpBinding >](webhttpbinding.md)ile yapılandırılmış bir uç noktanın güvenlik gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="63bdf-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="63bdf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="63bdf-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="63bdf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="63bdf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="63bdf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="63bdf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="63bdf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="63bdf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="63bdf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="63bdf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="63bdf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63bdf-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63bdf-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63bdf-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="63bdf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63bdf-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63bdf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63bdf-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="63bdf-113">Attributes</span></span>  
  
|<span data-ttu-id="63bdf-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="63bdf-114">Attribute</span></span>|<span data-ttu-id="63bdf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63bdf-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63bdf-116">mod</span><span class="sxs-lookup"><span data-stu-id="63bdf-116">mode</span></span>|<span data-ttu-id="63bdf-117">Aktarım düzeyi güvenliğinin veya bir uç nokta tarafından bir güvenlik kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="63bdf-118">Varsayılan, `None` değeridir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-118">The default is `None`.</span></span> <span data-ttu-id="63bdf-119">Bu öznitelik <xref:System.ServiceModel.WebHttpSecurityMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="63bdf-120">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="63bdf-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="63bdf-121">Değer</span><span class="sxs-lookup"><span data-stu-id="63bdf-121">Value</span></span>|<span data-ttu-id="63bdf-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63bdf-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63bdf-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="63bdf-123">None</span></span>|<span data-ttu-id="63bdf-124">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="63bdf-124">Security is disabled.</span></span>|  
|<span data-ttu-id="63bdf-125">Aktarım</span><span class="sxs-lookup"><span data-stu-id="63bdf-125">Transport</span></span>|<span data-ttu-id="63bdf-126">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="63bdf-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="63bdf-127">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="63bdf-128">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="63bdf-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="63bdf-129">İstemci kimlik doğrulaması, [\<taşıma >](transport-of-webhttpbinding.md)`ClientCredentialType` özniteliği aracılığıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="63bdf-130">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="63bdf-130">TransportCredentialOnly</span></span>|<span data-ttu-id="63bdf-131">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="63bdf-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="63bdf-132">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="63bdf-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="63bdf-133">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63bdf-133">This mode should be used with caution.</span></span> <span data-ttu-id="63bdf-134">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63bdf-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="63bdf-135">Child Elements</span></span>  
  
|<span data-ttu-id="63bdf-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="63bdf-136">Element</span></span>|<span data-ttu-id="63bdf-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63bdf-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63bdf-138">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="63bdf-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="63bdf-139">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="63bdf-139">Defines the transport security settings.</span></span> <span data-ttu-id="63bdf-140">Bu öğe <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türüne karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="63bdf-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63bdf-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="63bdf-141">Parent Elements</span></span>  
  
|<span data-ttu-id="63bdf-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="63bdf-142">Element</span></span>|<span data-ttu-id="63bdf-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63bdf-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63bdf-144">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="63bdf-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="63bdf-145">SOAP iletileri yerine HTTP isteklerine yanıt veren Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="63bdf-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63bdf-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63bdf-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="63bdf-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="63bdf-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="63bdf-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="63bdf-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="63bdf-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="63bdf-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="63bdf-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="63bdf-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="63bdf-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="63bdf-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="63bdf-152">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="63bdf-152">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="63bdf-153">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="63bdf-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
