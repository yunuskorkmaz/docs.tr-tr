---
title: <security> / <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 6348bc6f6c0d3a9656fbe57bf71f531d1287a949
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670488"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="ada40-102">\<Güvenlik >, \<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="ada40-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="ada40-103">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), kimlik doğrulaması türü de dahil olmak üzere kullanılan ve güvenlik ileti aktarım için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ada40-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="ada40-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ada40-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ada40-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ada40-105">\<bindings></span></span>  
<span data-ttu-id="ada40-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="ada40-106">\<netPeerBinding></span></span>  
<span data-ttu-id="ada40-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ada40-107">\<binding></span></span>  
<span data-ttu-id="ada40-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ada40-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada40-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ada40-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ada40-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ada40-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ada40-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ada40-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ada40-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ada40-112">Attributes</span></span>  
  
|<span data-ttu-id="ada40-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ada40-113">Attribute</span></span>|<span data-ttu-id="ada40-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ada40-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ada40-115">mod</span><span class="sxs-lookup"><span data-stu-id="ada40-115">mode</span></span>|<span data-ttu-id="ada40-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ada40-116">Optional.</span></span> <span data-ttu-id="ada40-117">Bu bağlama ile yapılandırılan eş tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ada40-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="ada40-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ada40-118">The default value is `Message`.</span></span> <span data-ttu-id="ada40-119">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ada40-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ada40-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="ada40-120">mode Attribute</span></span>  
  
|<span data-ttu-id="ada40-121">Değer</span><span class="sxs-lookup"><span data-stu-id="ada40-121">Value</span></span>|<span data-ttu-id="ada40-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ada40-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ada40-123">İleti</span><span class="sxs-lookup"><span data-stu-id="ada40-123">Message</span></span>|<span data-ttu-id="ada40-124">SOAP güvenliği, kimlik doğrulaması, bütünlüğü ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ada40-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="ada40-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="ada40-125">None</span></span>|<span data-ttu-id="ada40-126">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ada40-126">Security is disabled.</span></span>|  
|<span data-ttu-id="ada40-127">Taşıma</span><span class="sxs-lookup"><span data-stu-id="ada40-127">Transport</span></span>|<span data-ttu-id="ada40-128">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ada40-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="ada40-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ada40-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="ada40-130">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ada40-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="ada40-131">SOAP iletilerini zengin kimlik bilgisi türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ada40-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ada40-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ada40-132">Child Elements</span></span>  
  
|<span data-ttu-id="ada40-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="ada40-133">Element</span></span>|<span data-ttu-id="ada40-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ada40-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ada40-135">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="ada40-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="ada40-136">Bu bağlama ile yapılandırılan eşleri tarafından gönderilen güvenli iletiler için aktarım türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ada40-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="ada40-137">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ada40-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ada40-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ada40-138">Parent Elements</span></span>  
  
|<span data-ttu-id="ada40-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="ada40-139">Element</span></span>|<span data-ttu-id="ada40-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ada40-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ada40-141">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ada40-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ada40-142">Tüm bağlama yeteneklerini tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ada40-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ada40-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ada40-143">Remarks</span></span>  
 <span data-ttu-id="ada40-144">Güvenlik ya da ileti veya aktarım özgü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ada40-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada40-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ada40-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="ada40-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ada40-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ada40-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="ada40-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ada40-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ada40-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ada40-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ada40-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ada40-150">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ada40-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ada40-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ada40-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
