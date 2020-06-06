---
title: <security> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738630"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="f2e5b-102">\<security> / \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f2e5b-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="f2e5b-103">İle yapılandırılmış bir uç noktanın güvenlik gereksinimlerini belirtir [\<webHttpBinding>](webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f2e5b-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f2e5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2e5b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2e5b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2e5b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f2e5b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2e5b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2e5b-107">Attributes</span></span>  
  
|<span data-ttu-id="f2e5b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2e5b-108">Attribute</span></span>|<span data-ttu-id="f2e5b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2e5b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2e5b-110">mod</span><span class="sxs-lookup"><span data-stu-id="f2e5b-110">mode</span></span>|<span data-ttu-id="f2e5b-111">Aktarım düzeyi güvenliğinin veya bir uç nokta tarafından bir güvenlik kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="f2e5b-112">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-112">The default is `None`.</span></span> <span data-ttu-id="f2e5b-113">Bu öznitelik türü <xref:System.ServiceModel.WebHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="f2e5b-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f2e5b-114">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="f2e5b-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="f2e5b-115">Değer</span><span class="sxs-lookup"><span data-stu-id="f2e5b-115">Value</span></span>|<span data-ttu-id="f2e5b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2e5b-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2e5b-117">Yok</span><span class="sxs-lookup"><span data-stu-id="f2e5b-117">None</span></span>|<span data-ttu-id="f2e5b-118">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-118">Security is disabled.</span></span>|  
|<span data-ttu-id="f2e5b-119">Aktarım</span><span class="sxs-lookup"><span data-stu-id="f2e5b-119">Transport</span></span>|<span data-ttu-id="f2e5b-120">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="f2e5b-121">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="f2e5b-122">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="f2e5b-123">İstemci kimlik doğrulaması, özniteliği aracılığıyla denetlenir `ClientCredentialType` [\<transport>](transport-of-webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f2e5b-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="f2e5b-124">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="f2e5b-124">TransportCredentialOnly</span></span>|<span data-ttu-id="f2e5b-125">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="f2e5b-126">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="f2e5b-127">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-127">This mode should be used with caution.</span></span> <span data-ttu-id="f2e5b-128">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2e5b-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2e5b-129">Child Elements</span></span>  
  
|<span data-ttu-id="f2e5b-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2e5b-130">Element</span></span>|<span data-ttu-id="f2e5b-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2e5b-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="f2e5b-132">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-132">Defines the transport security settings.</span></span> <span data-ttu-id="f2e5b-133">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="f2e5b-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2e5b-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2e5b-134">Parent Elements</span></span>  
  
|<span data-ttu-id="f2e5b-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2e5b-135">Element</span></span>|<span data-ttu-id="f2e5b-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2e5b-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="f2e5b-137">SOAP iletileri yerine HTTP isteklerine yanıt veren Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2e5b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2e5b-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="f2e5b-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f2e5b-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f2e5b-140">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="f2e5b-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f2e5b-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f2e5b-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f2e5b-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f2e5b-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f2e5b-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f2e5b-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="f2e5b-144">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="f2e5b-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
