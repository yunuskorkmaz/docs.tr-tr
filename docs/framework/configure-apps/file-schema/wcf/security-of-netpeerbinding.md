---
title: "&lt;netPeerBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: aac60b8502789e92c23072d139bf892ff055f9b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="33d5b-102">&lt;netPeerBinding&gt; &lt;güvenliği&gt;</span><span class="sxs-lookup"><span data-stu-id="33d5b-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="33d5b-103">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), kimlik doğrulama türü de dahil olmak üzere güvenlik kullanılır ve ileti taşıması için.</span><span class="sxs-lookup"><span data-stu-id="33d5b-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="33d5b-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="33d5b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="33d5b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="33d5b-105">\<bindings></span></span>  
<span data-ttu-id="33d5b-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="33d5b-106">\<netPeerBinding></span></span>  
<span data-ttu-id="33d5b-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="33d5b-107">\<binding></span></span>  
<span data-ttu-id="33d5b-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="33d5b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33d5b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33d5b-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33d5b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="33d5b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="33d5b-111">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="33d5b-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33d5b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="33d5b-112">Attributes</span></span>  
  
|<span data-ttu-id="33d5b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="33d5b-113">Attribute</span></span>|<span data-ttu-id="33d5b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33d5b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33d5b-115">mod</span><span class="sxs-lookup"><span data-stu-id="33d5b-115">mode</span></span>|<span data-ttu-id="33d5b-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="33d5b-116">Optional.</span></span> <span data-ttu-id="33d5b-117">Bu bağlama ile yapılandırılan eş tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="33d5b-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="33d5b-118">Varsayılan değer `Message` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="33d5b-118">The default value is `Message`.</span></span> <span data-ttu-id="33d5b-119">Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="33d5b-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="33d5b-120">mod özniteliği</span><span class="sxs-lookup"><span data-stu-id="33d5b-120">mode Attribute</span></span>  
  
|<span data-ttu-id="33d5b-121">Değer</span><span class="sxs-lookup"><span data-stu-id="33d5b-121">Value</span></span>|<span data-ttu-id="33d5b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33d5b-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="33d5b-123">İleti</span><span class="sxs-lookup"><span data-stu-id="33d5b-123">Message</span></span>|<span data-ttu-id="33d5b-124">SOAP güvenliği kimlik doğrulama, bütünlüğü ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="33d5b-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="33d5b-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="33d5b-125">None</span></span>|<span data-ttu-id="33d5b-126">Güvenliği devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="33d5b-126">Security is disabled.</span></span>|  
|<span data-ttu-id="33d5b-127">Taşıma</span><span class="sxs-lookup"><span data-stu-id="33d5b-127">Transport</span></span>|<span data-ttu-id="33d5b-128">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="33d5b-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="33d5b-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="33d5b-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="33d5b-130">HTTPS kimlik doğrulaması ve gizliliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="33d5b-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="33d5b-131">SOAP iletilerine zengin kimlik bilgisi türler sağlar.</span><span class="sxs-lookup"><span data-stu-id="33d5b-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33d5b-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="33d5b-132">Child Elements</span></span>  
  
|<span data-ttu-id="33d5b-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="33d5b-133">Element</span></span>|<span data-ttu-id="33d5b-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33d5b-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33d5b-135">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="33d5b-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="33d5b-136">Bu bağlama ile yapılandırılan eş tarafından gönderilen güvenli iletiler için aktarım türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="33d5b-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="33d5b-137">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="33d5b-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33d5b-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="33d5b-138">Parent Elements</span></span>  
  
|<span data-ttu-id="33d5b-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="33d5b-139">Element</span></span>|<span data-ttu-id="33d5b-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33d5b-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33d5b-141">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="33d5b-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="33d5b-142">Tüm bağlama özelliklerini tanımlayan [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="33d5b-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33d5b-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33d5b-143">Remarks</span></span>  
 <span data-ttu-id="33d5b-144">Güvenlik ya da ileti veya taşıma özgü olabilir.</span><span class="sxs-lookup"><span data-stu-id="33d5b-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d5b-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33d5b-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="33d5b-146">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="33d5b-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="33d5b-147">Bir kimlik bilgisi türü seçme</span><span class="sxs-lookup"><span data-stu-id="33d5b-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="33d5b-148">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="33d5b-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="33d5b-149">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="33d5b-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="33d5b-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="33d5b-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="33d5b-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="33d5b-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
