---
title: "&lt;peerTransport&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d08d839d0eb80c23b96f87cf26d3d68db7d358f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="3619a-102">&lt;peerTransport&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="3619a-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="3619a-103">Kullanılan kimlik doğrulama ve ileti taşıma için kullanılan güvenlik türünü de dahil olmak üzere bir eş kanalı ile ilişkili güvenlik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3619a-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="3619a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3619a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3619a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3619a-105">\<bindings></span></span>  
<span data-ttu-id="3619a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3619a-106">\<customBinding></span></span>  
<span data-ttu-id="3619a-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3619a-107">\<binding></span></span>  
<span data-ttu-id="3619a-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="3619a-108">\<peerTransport></span></span>  
<span data-ttu-id="3619a-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3619a-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3619a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3619a-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3619a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3619a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3619a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3619a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3619a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3619a-113">Attributes</span></span>  
  
|<span data-ttu-id="3619a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3619a-114">Attribute</span></span>|<span data-ttu-id="3619a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3619a-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="3619a-116">Uygulanacak güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3619a-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="3619a-117">İleti varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="3619a-117">The default value is Message.</span></span> <span data-ttu-id="3619a-118">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3619a-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3619a-119">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="3619a-119">mode Attribute</span></span>  
  
|<span data-ttu-id="3619a-120">Değer</span><span class="sxs-lookup"><span data-stu-id="3619a-120">Value</span></span>|<span data-ttu-id="3619a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3619a-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="3619a-122">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3619a-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="3619a-123">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3619a-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="3619a-124">SOAP güvenliği kimlik doğrulama, bütünlüğü ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3619a-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="3619a-125">HTTPS kimlik doğrulaması ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="3619a-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="3619a-126">SOAP iletilerine zengin kimlik bilgisi türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3619a-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3619a-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3619a-127">Child Elements</span></span>  
  
|<span data-ttu-id="3619a-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="3619a-128">Element</span></span>|<span data-ttu-id="3619a-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3619a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3619a-130">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="3619a-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="3619a-131">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3619a-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="3619a-132">Bu öğeye sahip bir `clientCredentialType` özniteliği olan bir hizmeti kullanılırken kullanılacak kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3619a-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="3619a-133">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="3619a-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="3619a-134">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3619a-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3619a-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3619a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3619a-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3619a-136">Element</span></span>|<span data-ttu-id="3619a-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3619a-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3619a-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="3619a-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="3619a-139">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3619a-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3619a-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3619a-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="3619a-141">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="3619a-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="3619a-142">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="3619a-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="3619a-143">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="3619a-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="3619a-144">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3619a-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3619a-145">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="3619a-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3619a-146">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3619a-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3619a-147">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3619a-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
