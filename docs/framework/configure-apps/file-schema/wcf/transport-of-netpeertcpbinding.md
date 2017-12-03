---
title: "&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 181e6a9458754934d6b3b27a31c2cf2dd3455f52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="17134-102">&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="17134-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="17134-103">Aktarım düzeyi güvenlik ayarlarını kullanırken belirtir [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="17134-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="17134-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="17134-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="17134-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="17134-105">\<bindings></span></span>  
<span data-ttu-id="17134-106">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="17134-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="17134-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="17134-107">\<binding></span></span>  
<span data-ttu-id="17134-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="17134-108">\<security></span></span>  
<span data-ttu-id="17134-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="17134-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17134-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17134-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17134-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="17134-111">Attributes and Elements</span></span>  
 <span data-ttu-id="17134-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="17134-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17134-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="17134-113">Attributes</span></span>  
  
|<span data-ttu-id="17134-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="17134-114">Attribute</span></span>|<span data-ttu-id="17134-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17134-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17134-116">CredentialType</span><span class="sxs-lookup"><span data-stu-id="17134-116">credentialType</span></span>|<span data-ttu-id="17134-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="17134-117">Optional.</span></span> <span data-ttu-id="17134-118">Eş taşıması ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="17134-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="17134-119">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="17134-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="17134-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="17134-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="17134-121">Değer</span><span class="sxs-lookup"><span data-stu-id="17134-121">Value</span></span>|<span data-ttu-id="17134-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17134-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17134-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="17134-123">Certificate</span></span>|<span data-ttu-id="17134-124">Eş kanal taşıma kimlik doğrulaması gerektiren bir X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="17134-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="17134-125">Parola</span><span class="sxs-lookup"><span data-stu-id="17134-125">Password</span></span>|<span data-ttu-id="17134-126">Eş kanal taşıma kimlik doğrulaması doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="17134-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17134-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="17134-127">Child Elements</span></span>  
 <span data-ttu-id="17134-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="17134-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17134-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="17134-129">Parent Elements</span></span>  
  
|<span data-ttu-id="17134-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="17134-130">Element</span></span>|<span data-ttu-id="17134-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17134-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17134-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="17134-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="17134-133">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="17134-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17134-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17134-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="17134-135">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="17134-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="17134-136">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="17134-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="17134-137">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="17134-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="17134-138">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="17134-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="17134-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="17134-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
