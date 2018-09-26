---
title: '&lt;peerTransport&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
author: BrucePerlerMS
ms.openlocfilehash: 152087550d3fa881a7a88271d9c91dfcc5c894c8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176766"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="4d0b0-102">&lt;peerTransport&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="4d0b0-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="4d0b0-103">İle kullanılan kimlik doğrulaması ve ileti aktarım için kullanılan güvenlik türü de dahil olmak üzere, eş kanaldan ilgili güvenlik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="4d0b0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4d0b0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4d0b0-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-105">\<bindings></span></span>  
<span data-ttu-id="4d0b0-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-106">\<customBinding></span></span>  
<span data-ttu-id="4d0b0-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-107">\<binding></span></span>  
<span data-ttu-id="4d0b0-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-108">\<peerTransport></span></span>  
<span data-ttu-id="4d0b0-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d0b0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d0b0-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d0b0-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d0b0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4d0b0-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d0b0-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d0b0-113">Attributes</span></span>  
  
|<span data-ttu-id="4d0b0-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4d0b0-114">Attribute</span></span>|<span data-ttu-id="4d0b0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d0b0-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="4d0b0-116">Uygulanacak güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="4d0b0-117">İleti varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-117">The default value is Message.</span></span> <span data-ttu-id="4d0b0-118">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4d0b0-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="4d0b0-119">mode Attribute</span></span>  
  
|<span data-ttu-id="4d0b0-120">Değer</span><span class="sxs-lookup"><span data-stu-id="4d0b0-120">Value</span></span>|<span data-ttu-id="4d0b0-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d0b0-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="4d0b0-122">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="4d0b0-123">HTTPS kullanarak güvenliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="4d0b0-124">SOAP güvenliği, kimlik doğrulaması, bütünlüğü ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="4d0b0-125">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="4d0b0-126">SOAP iletilerini zengin kimlik bilgisi türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d0b0-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d0b0-127">Child Elements</span></span>  
  
|<span data-ttu-id="4d0b0-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d0b0-128">Element</span></span>|<span data-ttu-id="4d0b0-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d0b0-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d0b0-130">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="4d0b0-131">Özel bağlama için bir eş tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="4d0b0-132">Bu öğeyi bir `clientCredentialType` özniteliği bir hizmetle etkileşim kurulurken kullanılacak kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="4d0b0-133">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="4d0b0-134">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d0b0-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d0b0-135">Parent Elements</span></span>  
  
|<span data-ttu-id="4d0b0-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d0b0-136">Element</span></span>|<span data-ttu-id="4d0b0-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d0b0-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d0b0-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="4d0b0-139">Özel bağlama için bir eş tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d0b0-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d0b0-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="4d0b0-141">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4d0b0-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="4d0b0-142">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="4d0b0-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="4d0b0-143">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="4d0b0-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="4d0b0-144">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4d0b0-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4d0b0-145">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4d0b0-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4d0b0-146">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4d0b0-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4d0b0-147">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4d0b0-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
