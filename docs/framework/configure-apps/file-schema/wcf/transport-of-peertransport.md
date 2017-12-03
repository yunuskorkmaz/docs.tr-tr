---
title: "&lt;peerTransport&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 69b62699f5db0ab11fac3cc4d1ba4e2aa022934d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="52a0c-102">&lt;peerTransport&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="52a0c-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="52a0c-103">Bu bağlama ile yapılandırılan eş tarafından gönderilen güvenli iletiler aktarım türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="52a0c-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="52a0c-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="52a0c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="52a0c-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="52a0c-105">\<bindings></span></span>  
<span data-ttu-id="52a0c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="52a0c-106">\<customBinding></span></span>  
<span data-ttu-id="52a0c-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="52a0c-107">\<binding></span></span>  
<span data-ttu-id="52a0c-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="52a0c-108">\<peerTransport></span></span>  
<span data-ttu-id="52a0c-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="52a0c-109">\<security></span></span>  
<span data-ttu-id="52a0c-110">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="52a0c-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a0c-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52a0c-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52a0c-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="52a0c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="52a0c-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="52a0c-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52a0c-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52a0c-114">Attributes</span></span>  
  
|<span data-ttu-id="52a0c-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52a0c-115">Attribute</span></span>|<span data-ttu-id="52a0c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52a0c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52a0c-117">CredentialType</span><span class="sxs-lookup"><span data-stu-id="52a0c-117">credentialType</span></span>|<span data-ttu-id="52a0c-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="52a0c-118">Optional.</span></span> <span data-ttu-id="52a0c-119">Eş taşıması ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="52a0c-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="52a0c-120">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="52a0c-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="52a0c-121">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="52a0c-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="52a0c-122">Değer</span><span class="sxs-lookup"><span data-stu-id="52a0c-122">Value</span></span>|<span data-ttu-id="52a0c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52a0c-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="52a0c-124">Sertifika</span><span class="sxs-lookup"><span data-stu-id="52a0c-124">Certificate</span></span>|<span data-ttu-id="52a0c-125">Eş kanal taşıma kimlik doğrulaması gerektiren bir X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="52a0c-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="52a0c-126">Parola</span><span class="sxs-lookup"><span data-stu-id="52a0c-126">Password</span></span>|<span data-ttu-id="52a0c-127">Eş kanal taşıma kimlik doğrulaması doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="52a0c-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52a0c-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="52a0c-128">Child Elements</span></span>  
 <span data-ttu-id="52a0c-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="52a0c-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52a0c-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="52a0c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="52a0c-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="52a0c-131">Element</span></span>|<span data-ttu-id="52a0c-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52a0c-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52a0c-133">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="52a0c-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="52a0c-134">Bir eş taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="52a0c-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52a0c-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52a0c-135">Remarks</span></span>  
 <span data-ttu-id="52a0c-136">Bu öğe yalnızca ayarlanır modu öznitelik [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) ayarlanır `Transport` veya `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="52a0c-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a0c-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52a0c-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="52a0c-138">Taşıma güvenliği</span><span class="sxs-lookup"><span data-stu-id="52a0c-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="52a0c-139">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="52a0c-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="52a0c-140">Taşıma seçme</span><span class="sxs-lookup"><span data-stu-id="52a0c-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="52a0c-141">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="52a0c-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="52a0c-142">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="52a0c-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="52a0c-143">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="52a0c-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="52a0c-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="52a0c-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
