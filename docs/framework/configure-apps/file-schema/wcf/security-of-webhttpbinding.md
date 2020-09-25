---
title: <security> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 60b863a0a2a846a60dde2e4b323a305b5096b1cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169901"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="e9a29-102">\<security> / \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e9a29-102">\<security> of \<webHttpBinding></span></span>

<span data-ttu-id="e9a29-103">İle yapılandırılmış bir uç noktanın güvenlik gereksinimlerini belirtir [\<webHttpBinding>](webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e9a29-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="e9a29-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e9a29-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9a29-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9a29-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e9a29-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9a29-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9a29-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9a29-107">Attributes</span></span>  
  
|<span data-ttu-id="e9a29-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e9a29-108">Attribute</span></span>|<span data-ttu-id="e9a29-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9a29-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9a29-110">mod</span><span class="sxs-lookup"><span data-stu-id="e9a29-110">mode</span></span>|<span data-ttu-id="e9a29-111">Aktarım düzeyi güvenliğinin veya bir uç nokta tarafından bir güvenlik kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9a29-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="e9a29-112">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="e9a29-112">The default is `None`.</span></span> <span data-ttu-id="e9a29-113">Bu öznitelik türü <xref:System.ServiceModel.WebHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="e9a29-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e9a29-114">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="e9a29-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="e9a29-115">Değer</span><span class="sxs-lookup"><span data-stu-id="e9a29-115">Value</span></span>|<span data-ttu-id="e9a29-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9a29-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9a29-117">Yok</span><span class="sxs-lookup"><span data-stu-id="e9a29-117">None</span></span>|<span data-ttu-id="e9a29-118">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e9a29-118">Security is disabled.</span></span>|  
|<span data-ttu-id="e9a29-119">Aktarım</span><span class="sxs-lookup"><span data-stu-id="e9a29-119">Transport</span></span>|<span data-ttu-id="e9a29-120">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e9a29-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="e9a29-121">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9a29-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="e9a29-122">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="e9a29-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="e9a29-123">İstemci kimlik doğrulaması, özniteliği aracılığıyla denetlenir `ClientCredentialType` [\<transport>](transport-of-webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e9a29-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="e9a29-124">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="e9a29-124">TransportCredentialOnly</span></span>|<span data-ttu-id="e9a29-125">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="e9a29-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="e9a29-126">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9a29-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="e9a29-127">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9a29-127">This mode should be used with caution.</span></span> <span data-ttu-id="e9a29-128">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9a29-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9a29-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9a29-129">Child Elements</span></span>  
  
|<span data-ttu-id="e9a29-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9a29-130">Element</span></span>|<span data-ttu-id="e9a29-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9a29-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="e9a29-132">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e9a29-132">Defines the transport security settings.</span></span> <span data-ttu-id="e9a29-133">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="e9a29-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9a29-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9a29-134">Parent Elements</span></span>  
  
|<span data-ttu-id="e9a29-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9a29-135">Element</span></span>|<span data-ttu-id="e9a29-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9a29-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="e9a29-137">SOAP iletileri yerine HTTP isteklerine yanıt veren Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="e9a29-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9a29-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9a29-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="e9a29-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e9a29-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e9a29-140">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="e9a29-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="e9a29-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e9a29-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9a29-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e9a29-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e9a29-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e9a29-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="e9a29-144">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="e9a29-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
