---
title: <security> / <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936622"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="44777-102">\<\<netpeerbinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="44777-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="44777-103">Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik dahil olmak üzere [ \<NetPeerTcpBinding >](netpeertcpbinding.md)güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44777-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="44777-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="44777-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="44777-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="44777-105">\<bindings></span></span>  
<span data-ttu-id="44777-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="44777-106">\<netPeerBinding></span></span>  
<span data-ttu-id="44777-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="44777-107">\<binding></span></span>  
<span data-ttu-id="44777-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="44777-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44777-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44777-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44777-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="44777-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44777-111">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="44777-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44777-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="44777-112">Attributes</span></span>  
  
|<span data-ttu-id="44777-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="44777-113">Attribute</span></span>|<span data-ttu-id="44777-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44777-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44777-115">mod</span><span class="sxs-lookup"><span data-stu-id="44777-115">mode</span></span>|<span data-ttu-id="44777-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="44777-116">Optional.</span></span> <span data-ttu-id="44777-117">Bu bağlama ile yapılandırılan eşler tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="44777-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="44777-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="44777-118">The default value is `Message`.</span></span> <span data-ttu-id="44777-119">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="44777-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="44777-120">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="44777-120">mode Attribute</span></span>  
  
|<span data-ttu-id="44777-121">Değer</span><span class="sxs-lookup"><span data-stu-id="44777-121">Value</span></span>|<span data-ttu-id="44777-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44777-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44777-123">`Message`</span><span class="sxs-lookup"><span data-stu-id="44777-123">Message</span></span>|<span data-ttu-id="44777-124">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="44777-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="44777-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="44777-125">None</span></span>|<span data-ttu-id="44777-126">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="44777-126">Security is disabled.</span></span>|  
|<span data-ttu-id="44777-127">Aktarım</span><span class="sxs-lookup"><span data-stu-id="44777-127">Transport</span></span>|<span data-ttu-id="44777-128">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="44777-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="44777-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="44777-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="44777-130">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="44777-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="44777-131">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="44777-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44777-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="44777-132">Child Elements</span></span>  
  
|<span data-ttu-id="44777-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="44777-133">Element</span></span>|<span data-ttu-id="44777-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44777-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44777-135">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="44777-135">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="44777-136">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44777-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="44777-137">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="44777-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44777-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="44777-138">Parent Elements</span></span>  
  
|<span data-ttu-id="44777-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="44777-139">Element</span></span>|<span data-ttu-id="44777-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44777-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44777-141">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="44777-141">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="44777-142">[ \<NetPeerTcpBinding >](netpeertcpbinding.md)'ın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44777-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44777-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44777-143">Remarks</span></span>  
 <span data-ttu-id="44777-144">Güvenlik, ileti ya da aktarım özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="44777-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44777-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44777-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="44777-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="44777-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="44777-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="44777-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="44777-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="44777-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="44777-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="44777-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="44777-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="44777-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="44777-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="44777-151">\<binding></span></span>](../../../misc/binding.md)
