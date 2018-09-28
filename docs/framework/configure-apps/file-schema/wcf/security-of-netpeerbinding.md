---
title: '&lt;netPeerBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
ms.openlocfilehash: d17d063ffdd354327c2523415b7d9394e723135a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47436303"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="42ce1-102">&lt;netPeerBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="42ce1-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="42ce1-103">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), kimlik doğrulaması türü de dahil olmak üzere kullanılan ve güvenlik ileti aktarım için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42ce1-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="42ce1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="42ce1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="42ce1-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="42ce1-105">\<bindings></span></span>  
<span data-ttu-id="42ce1-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="42ce1-106">\<netPeerBinding></span></span>  
<span data-ttu-id="42ce1-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="42ce1-107">\<binding></span></span>  
<span data-ttu-id="42ce1-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="42ce1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ce1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42ce1-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42ce1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="42ce1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="42ce1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42ce1-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42ce1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="42ce1-112">Attributes</span></span>  
  
|<span data-ttu-id="42ce1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="42ce1-113">Attribute</span></span>|<span data-ttu-id="42ce1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42ce1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42ce1-115">mod</span><span class="sxs-lookup"><span data-stu-id="42ce1-115">mode</span></span>|<span data-ttu-id="42ce1-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="42ce1-116">Optional.</span></span> <span data-ttu-id="42ce1-117">Bu bağlama ile yapılandırılan eş tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="42ce1-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="42ce1-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="42ce1-118">The default value is `Message`.</span></span> <span data-ttu-id="42ce1-119">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="42ce1-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="42ce1-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="42ce1-120">mode Attribute</span></span>  
  
|<span data-ttu-id="42ce1-121">Değer</span><span class="sxs-lookup"><span data-stu-id="42ce1-121">Value</span></span>|<span data-ttu-id="42ce1-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42ce1-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="42ce1-123">İleti</span><span class="sxs-lookup"><span data-stu-id="42ce1-123">Message</span></span>|<span data-ttu-id="42ce1-124">SOAP güvenliği, kimlik doğrulaması, bütünlüğü ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="42ce1-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="42ce1-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="42ce1-125">None</span></span>|<span data-ttu-id="42ce1-126">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="42ce1-126">Security is disabled.</span></span>|  
|<span data-ttu-id="42ce1-127">Taşıma</span><span class="sxs-lookup"><span data-stu-id="42ce1-127">Transport</span></span>|<span data-ttu-id="42ce1-128">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="42ce1-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="42ce1-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="42ce1-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="42ce1-130">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="42ce1-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="42ce1-131">SOAP iletilerini zengin kimlik bilgisi türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="42ce1-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42ce1-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="42ce1-132">Child Elements</span></span>  
  
|<span data-ttu-id="42ce1-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="42ce1-133">Element</span></span>|<span data-ttu-id="42ce1-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42ce1-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42ce1-135">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="42ce1-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="42ce1-136">Bu bağlama ile yapılandırılan eşleri tarafından gönderilen güvenli iletiler için aktarım türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="42ce1-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="42ce1-137">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="42ce1-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42ce1-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="42ce1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="42ce1-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="42ce1-139">Element</span></span>|<span data-ttu-id="42ce1-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42ce1-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42ce1-141">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="42ce1-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="42ce1-142">Tüm bağlama yeteneklerini tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="42ce1-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42ce1-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42ce1-143">Remarks</span></span>  
 <span data-ttu-id="42ce1-144">Güvenlik ya da ileti veya aktarım özgü olabilir.</span><span class="sxs-lookup"><span data-stu-id="42ce1-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ce1-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42ce1-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="42ce1-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="42ce1-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="42ce1-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="42ce1-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="42ce1-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="42ce1-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="42ce1-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="42ce1-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="42ce1-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="42ce1-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="42ce1-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="42ce1-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
