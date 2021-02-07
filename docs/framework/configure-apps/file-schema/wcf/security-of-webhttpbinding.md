---
description: 'Hakkında daha fazla bilgi <security> edinin: <webHttpBinding>'
title: <security> / <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: a80a919ef877f01503e5ceaeb4fe7432e46f288c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683053"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="623b4-103">\<security> / \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="623b4-103">\<security> of \<webHttpBinding></span></span>

<span data-ttu-id="623b4-104">İle yapılandırılmış bir uç noktanın güvenlik gereksinimlerini belirtir [\<webHttpBinding>](webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="623b4-104">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="623b4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="623b4-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="623b4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="623b4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="623b4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="623b4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="623b4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="623b4-108">Attributes</span></span>  
  
|<span data-ttu-id="623b4-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="623b4-109">Attribute</span></span>|<span data-ttu-id="623b4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="623b4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="623b4-111">mod</span><span class="sxs-lookup"><span data-stu-id="623b4-111">mode</span></span>|<span data-ttu-id="623b4-112">Aktarım düzeyi güvenliğinin veya bir uç nokta tarafından bir güvenlik kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="623b4-112">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="623b4-113">Varsayılan değer: `None`.</span><span class="sxs-lookup"><span data-stu-id="623b4-113">The default is `None`.</span></span> <span data-ttu-id="623b4-114">Bu öznitelik türü <xref:System.ServiceModel.WebHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="623b4-114">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="623b4-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="623b4-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="623b4-116">Değer</span><span class="sxs-lookup"><span data-stu-id="623b4-116">Value</span></span>|<span data-ttu-id="623b4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="623b4-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="623b4-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="623b4-118">None</span></span>|<span data-ttu-id="623b4-119">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="623b4-119">Security is disabled.</span></span>|  
|<span data-ttu-id="623b4-120">Aktarım</span><span class="sxs-lookup"><span data-stu-id="623b4-120">Transport</span></span>|<span data-ttu-id="623b4-121">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="623b4-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="623b4-122">Hizmetin SSL sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="623b4-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="623b4-123">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="623b4-123">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="623b4-124">İstemci kimlik doğrulaması, özniteliği aracılığıyla denetlenir `ClientCredentialType` [\<transport>](transport-of-webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="623b4-124">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="623b4-125">Yalnızca transportcredential</span><span class="sxs-lookup"><span data-stu-id="623b4-125">TransportCredentialOnly</span></span>|<span data-ttu-id="623b4-126">Bu mod ileti bütünlüğü ve gizliliği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="623b4-126">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="623b4-127">HTTP tabanlı istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="623b4-127">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="623b4-128">Bu mod dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="623b4-128">This mode should be used with caution.</span></span> <span data-ttu-id="623b4-129">Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="623b4-129">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="623b4-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="623b4-130">Child Elements</span></span>  
  
|<span data-ttu-id="623b4-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="623b4-131">Element</span></span>|<span data-ttu-id="623b4-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="623b4-132">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="623b4-133">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="623b4-133">Defines the transport security settings.</span></span> <span data-ttu-id="623b4-134">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="623b4-134">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="623b4-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="623b4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="623b4-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="623b4-136">Element</span></span>|<span data-ttu-id="623b4-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="623b4-137">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="623b4-138">SOAP iletileri yerine HTTP isteklerine yanıt veren Windows Communication Foundation (WCF) Web Hizmetleri için uç noktaları yapılandırmak için kullanılan bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="623b4-138">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="623b4-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="623b4-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="623b4-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="623b4-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="623b4-141">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="623b4-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="623b4-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="623b4-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="623b4-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="623b4-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="623b4-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="623b4-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="623b4-145">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="623b4-145">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
