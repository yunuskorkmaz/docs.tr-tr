---
title: <security> / <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738664"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="2d712-102">\<netPeerBinding > Güvenlik > \<</span><span class="sxs-lookup"><span data-stu-id="2d712-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="2d712-103">Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi [\<netPeerTcpBinding >](netpeertcpbinding.md)güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d712-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="2d712-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2d712-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d712-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="2d712-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2d712-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2d712-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2d712-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="2d712-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="2d712-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="2d712-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2d712-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="2d712-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d712-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d712-110">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d712-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d712-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2d712-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="2d712-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d712-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d712-113">Attributes</span></span>  
  
|<span data-ttu-id="2d712-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2d712-114">Attribute</span></span>|<span data-ttu-id="2d712-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d712-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d712-116">mod</span><span class="sxs-lookup"><span data-stu-id="2d712-116">mode</span></span>|<span data-ttu-id="2d712-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2d712-117">Optional.</span></span> <span data-ttu-id="2d712-118">Bu bağlama ile yapılandırılan eşler tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d712-118">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="2d712-119">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2d712-119">The default value is `Message`.</span></span> <span data-ttu-id="2d712-120">Bu öznitelik <xref:System.ServiceModel.SecurityMode>türündedir.</span><span class="sxs-lookup"><span data-stu-id="2d712-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2d712-121">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="2d712-121">mode Attribute</span></span>  
  
|<span data-ttu-id="2d712-122">Değer</span><span class="sxs-lookup"><span data-stu-id="2d712-122">Value</span></span>|<span data-ttu-id="2d712-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d712-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d712-124">İleti</span><span class="sxs-lookup"><span data-stu-id="2d712-124">Message</span></span>|<span data-ttu-id="2d712-125">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d712-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="2d712-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d712-126">None</span></span>|<span data-ttu-id="2d712-127">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="2d712-127">Security is disabled.</span></span>|  
|<span data-ttu-id="2d712-128">Aktarım</span><span class="sxs-lookup"><span data-stu-id="2d712-128">Transport</span></span>|<span data-ttu-id="2d712-129">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2d712-129">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="2d712-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2d712-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="2d712-131">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d712-131">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="2d712-132">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d712-132">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d712-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d712-133">Child Elements</span></span>  
  
|<span data-ttu-id="2d712-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d712-134">Element</span></span>|<span data-ttu-id="2d712-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d712-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d712-136">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="2d712-136">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="2d712-137">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d712-137">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="2d712-138">Bu öğe <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="2d712-138">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d712-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d712-139">Parent Elements</span></span>  
  
|<span data-ttu-id="2d712-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d712-140">Element</span></span>|<span data-ttu-id="2d712-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d712-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d712-142">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="2d712-142">\<binding></span></span>](bindings.md)|<span data-ttu-id="2d712-143">[\<netPeerTcpBinding >](netpeertcpbinding.md)bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d712-143">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d712-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d712-144">Remarks</span></span>  
 <span data-ttu-id="2d712-145">Güvenlik, ileti ya da aktarım özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="2d712-145">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d712-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d712-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="2d712-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2d712-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2d712-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="2d712-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="2d712-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2d712-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2d712-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2d712-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2d712-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="2d712-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2d712-152">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="2d712-152">\<binding></span></span>](bindings.md)
