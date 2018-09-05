---
title: '&lt;netPeerBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 45000554226fcde753041fca283bfc8b1eeba5ce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541775"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="bb711-102">&lt;netPeerBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="bb711-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="bb711-103">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), kimlik doğrulaması türü de dahil olmak üzere kullanılan ve güvenlik ileti aktarım için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb711-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="bb711-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bb711-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bb711-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bb711-105">\<bindings></span></span>  
<span data-ttu-id="bb711-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="bb711-106">\<netPeerBinding></span></span>  
<span data-ttu-id="bb711-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bb711-107">\<binding></span></span>  
<span data-ttu-id="bb711-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bb711-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb711-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb711-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb711-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb711-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bb711-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb711-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb711-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb711-112">Attributes</span></span>  
  
|<span data-ttu-id="bb711-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bb711-113">Attribute</span></span>|<span data-ttu-id="bb711-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb711-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb711-115">mod</span><span class="sxs-lookup"><span data-stu-id="bb711-115">mode</span></span>|<span data-ttu-id="bb711-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="bb711-116">Optional.</span></span> <span data-ttu-id="bb711-117">Bu bağlama ile yapılandırılan eş tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb711-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="bb711-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bb711-118">The default value is `Message`.</span></span> <span data-ttu-id="bb711-119">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="bb711-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="bb711-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="bb711-120">mode Attribute</span></span>  
  
|<span data-ttu-id="bb711-121">Değer</span><span class="sxs-lookup"><span data-stu-id="bb711-121">Value</span></span>|<span data-ttu-id="bb711-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb711-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bb711-123">İleti</span><span class="sxs-lookup"><span data-stu-id="bb711-123">Message</span></span>|<span data-ttu-id="bb711-124">SOAP güvenliği, kimlik doğrulaması, bütünlüğü ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb711-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="bb711-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="bb711-125">None</span></span>|<span data-ttu-id="bb711-126">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="bb711-126">Security is disabled.</span></span>|  
|<span data-ttu-id="bb711-127">Taşıma</span><span class="sxs-lookup"><span data-stu-id="bb711-127">Transport</span></span>|<span data-ttu-id="bb711-128">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bb711-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="bb711-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="bb711-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="bb711-130">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb711-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="bb711-131">SOAP iletilerini zengin kimlik bilgisi türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb711-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb711-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb711-132">Child Elements</span></span>  
  
|<span data-ttu-id="bb711-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb711-133">Element</span></span>|<span data-ttu-id="bb711-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb711-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb711-135">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="bb711-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="bb711-136">Bu bağlama ile yapılandırılan eşleri tarafından gönderilen güvenli iletiler için aktarım türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bb711-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="bb711-137">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="bb711-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb711-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb711-138">Parent Elements</span></span>  
  
|<span data-ttu-id="bb711-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb711-139">Element</span></span>|<span data-ttu-id="bb711-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb711-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb711-141">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bb711-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bb711-142">Tüm bağlama yeteneklerini tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bb711-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb711-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb711-143">Remarks</span></span>  
 <span data-ttu-id="bb711-144">Güvenlik ya da ileti veya aktarım özgü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb711-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb711-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb711-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="bb711-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="bb711-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="bb711-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="bb711-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="bb711-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bb711-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bb711-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bb711-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bb711-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="bb711-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bb711-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bb711-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
