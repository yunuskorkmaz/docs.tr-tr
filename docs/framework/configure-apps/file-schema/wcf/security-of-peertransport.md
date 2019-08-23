---
title: <security> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936633"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="3134b-102">\<\<peertransport > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3134b-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="3134b-103">Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi bir eş kanalla ilişkili güvenlik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3134b-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="3134b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3134b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3134b-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3134b-105">\<bindings></span></span>  
<span data-ttu-id="3134b-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3134b-106">\<customBinding></span></span>  
<span data-ttu-id="3134b-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3134b-107">\<binding></span></span>  
<span data-ttu-id="3134b-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="3134b-108">\<peerTransport></span></span>  
<span data-ttu-id="3134b-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3134b-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3134b-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3134b-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3134b-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3134b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3134b-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3134b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3134b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3134b-113">Attributes</span></span>  
  
|<span data-ttu-id="3134b-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3134b-114">Attribute</span></span>|<span data-ttu-id="3134b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3134b-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="3134b-116">Uygulanacak güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3134b-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="3134b-117">Varsayılan değer Iletidir.</span><span class="sxs-lookup"><span data-stu-id="3134b-117">The default value is Message.</span></span> <span data-ttu-id="3134b-118">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3134b-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3134b-119">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="3134b-119">mode Attribute</span></span>  
  
|<span data-ttu-id="3134b-120">Değer</span><span class="sxs-lookup"><span data-stu-id="3134b-120">Value</span></span>|<span data-ttu-id="3134b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3134b-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="3134b-122">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3134b-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="3134b-123">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3134b-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="3134b-124">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3134b-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="3134b-125">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3134b-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="3134b-126">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3134b-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3134b-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3134b-127">Child Elements</span></span>  
  
|<span data-ttu-id="3134b-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="3134b-128">Element</span></span>|<span data-ttu-id="3134b-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3134b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3134b-130">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="3134b-130">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="3134b-131">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3134b-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="3134b-132">Bu öğe, bir `clientCredentialType` hizmetle etkileşim kurarken kullanılacak kimlik bilgilerini belirten bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3134b-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="3134b-133">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3134b-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="3134b-134">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3134b-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3134b-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3134b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3134b-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3134b-136">Element</span></span>|<span data-ttu-id="3134b-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3134b-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3134b-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="3134b-138">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="3134b-139">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3134b-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3134b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3134b-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3134b-141">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="3134b-141">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="3134b-142">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="3134b-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="3134b-143">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="3134b-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3134b-144">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3134b-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3134b-145">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="3134b-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3134b-146">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3134b-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3134b-147">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3134b-147">\<customBinding></span></span>](custombinding.md)
