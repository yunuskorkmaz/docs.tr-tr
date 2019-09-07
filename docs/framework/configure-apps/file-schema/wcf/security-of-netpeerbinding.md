---
title: <security> / <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 88aa2898472c20c9e52cfd5830c0e41e8ea9ba21
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399810"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="5ad52-102">\<\<netpeerbinding > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="5ad52-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="5ad52-103">Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik dahil olmak üzere [ \<NetPeerTcpBinding >](netpeertcpbinding.md)güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ad52-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="5ad52-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ad52-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ad52-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5ad52-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5ad52-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5ad52-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5ad52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5ad52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="5ad52-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="5ad52-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5ad52-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="5ad52-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ad52-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ad52-110">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ad52-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad52-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5ad52-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="5ad52-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ad52-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ad52-113">Attributes</span></span>  
  
|<span data-ttu-id="5ad52-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ad52-114">Attribute</span></span>|<span data-ttu-id="5ad52-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ad52-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ad52-116">mod</span><span class="sxs-lookup"><span data-stu-id="5ad52-116">mode</span></span>|<span data-ttu-id="5ad52-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5ad52-117">Optional.</span></span> <span data-ttu-id="5ad52-118">Bu bağlama ile yapılandırılan eşler tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ad52-118">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="5ad52-119">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5ad52-119">The default value is `Message`.</span></span> <span data-ttu-id="5ad52-120">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5ad52-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5ad52-121">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="5ad52-121">mode Attribute</span></span>  
  
|<span data-ttu-id="5ad52-122">Değer</span><span class="sxs-lookup"><span data-stu-id="5ad52-122">Value</span></span>|<span data-ttu-id="5ad52-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ad52-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ad52-124">`Message`</span><span class="sxs-lookup"><span data-stu-id="5ad52-124">Message</span></span>|<span data-ttu-id="5ad52-125">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ad52-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="5ad52-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ad52-126">None</span></span>|<span data-ttu-id="5ad52-127">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="5ad52-127">Security is disabled.</span></span>|  
|<span data-ttu-id="5ad52-128">Aktarım</span><span class="sxs-lookup"><span data-stu-id="5ad52-128">Transport</span></span>|<span data-ttu-id="5ad52-129">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5ad52-129">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="5ad52-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="5ad52-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="5ad52-131">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ad52-131">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="5ad52-132">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ad52-132">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ad52-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad52-133">Child Elements</span></span>  
  
|<span data-ttu-id="5ad52-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ad52-134">Element</span></span>|<span data-ttu-id="5ad52-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ad52-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ad52-136">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="5ad52-136">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="5ad52-137">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ad52-137">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="5ad52-138">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5ad52-138">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ad52-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ad52-139">Parent Elements</span></span>  
  
|<span data-ttu-id="5ad52-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ad52-140">Element</span></span>|<span data-ttu-id="5ad52-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ad52-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ad52-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5ad52-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5ad52-143">[ \<NetPeerTcpBinding >](netpeertcpbinding.md)'ın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ad52-143">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ad52-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ad52-144">Remarks</span></span>  
 <span data-ttu-id="5ad52-145">Güvenlik, ileti ya da aktarım özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ad52-145">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad52-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ad52-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="5ad52-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5ad52-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5ad52-148">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="5ad52-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="5ad52-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5ad52-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5ad52-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5ad52-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5ad52-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ad52-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5ad52-152">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="5ad52-152">\<binding></span></span>](../../../misc/binding.md)
