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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 787d4569416203364e04898c6adcd57fb5a7aec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="30140-102">&lt;peerTransport&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="30140-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="30140-103">Bu bağlama ile yapılandırılan eş tarafından gönderilen güvenli iletiler aktarım türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="30140-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="30140-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="30140-104">\<system.serviceModel></span></span>  
<span data-ttu-id="30140-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="30140-105">\<bindings></span></span>  
<span data-ttu-id="30140-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30140-106">\<customBinding></span></span>  
<span data-ttu-id="30140-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30140-107">\<binding></span></span>  
<span data-ttu-id="30140-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="30140-108">\<peerTransport></span></span>  
<span data-ttu-id="30140-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="30140-109">\<security></span></span>  
<span data-ttu-id="30140-110">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="30140-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30140-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30140-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30140-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30140-112">Attributes and Elements</span></span>  
 <span data-ttu-id="30140-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="30140-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30140-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30140-114">Attributes</span></span>  
  
|<span data-ttu-id="30140-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30140-115">Attribute</span></span>|<span data-ttu-id="30140-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30140-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30140-117">CredentialType</span><span class="sxs-lookup"><span data-stu-id="30140-117">credentialType</span></span>|<span data-ttu-id="30140-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="30140-118">Optional.</span></span> <span data-ttu-id="30140-119">Eş taşıması ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="30140-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="30140-120">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="30140-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="30140-121">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="30140-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="30140-122">Değer</span><span class="sxs-lookup"><span data-stu-id="30140-122">Value</span></span>|<span data-ttu-id="30140-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30140-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="30140-124">Sertifika</span><span class="sxs-lookup"><span data-stu-id="30140-124">Certificate</span></span>|<span data-ttu-id="30140-125">Eş kanal taşıma kimlik doğrulaması gerektiren bir X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="30140-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="30140-126">Parola</span><span class="sxs-lookup"><span data-stu-id="30140-126">Password</span></span>|<span data-ttu-id="30140-127">Eş kanal taşıma kimlik doğrulaması doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="30140-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30140-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30140-128">Child Elements</span></span>  
 <span data-ttu-id="30140-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="30140-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30140-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30140-130">Parent Elements</span></span>  
  
|<span data-ttu-id="30140-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="30140-131">Element</span></span>|<span data-ttu-id="30140-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30140-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30140-133">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="30140-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="30140-134">Bir eş taşıma için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30140-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30140-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30140-135">Remarks</span></span>  
 <span data-ttu-id="30140-136">Bu öğe yalnızca ayarlanır modu öznitelik [ \<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) ayarlanır `Transport` veya `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="30140-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30140-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30140-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="30140-138">Taşıma güvenliği</span><span class="sxs-lookup"><span data-stu-id="30140-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="30140-139">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="30140-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="30140-140">Taşıma seçme</span><span class="sxs-lookup"><span data-stu-id="30140-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="30140-141">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="30140-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="30140-142">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="30140-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="30140-143">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30140-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="30140-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30140-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
