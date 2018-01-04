---
title: "&lt;clientCredentials&gt; Öğesi &lt;eşi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: accd6c261a393da3ffcffd261d6603d20b8fcb3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="5c8ea-102">&lt;clientCredentials&gt; Öğesi &lt;eşi&gt;</span><span class="sxs-lookup"><span data-stu-id="5c8ea-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="5c8ea-103">Eşler arası istemcileri kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="5c8ea-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c8ea-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-105">\<behaviors></span></span>  
<span data-ttu-id="5c8ea-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5c8ea-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-107">\<behavior></span></span>  
<span data-ttu-id="5c8ea-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-108">\<clientCredentials></span></span>  
<span data-ttu-id="5c8ea-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8ea-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c8ea-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c8ea-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c8ea-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5c8ea-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c8ea-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c8ea-113">Attributes</span></span>  
 <span data-ttu-id="5c8ea-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5c8ea-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c8ea-115">Child Elements</span></span>  
  
|<span data-ttu-id="5c8ea-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c8ea-116">Element</span></span>|<span data-ttu-id="5c8ea-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c8ea-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c8ea-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="5c8ea-119">İmzalama ve eşler arası istemcileri için iletileri şifrelemek için kullanılacak bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="5c8ea-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-120">.</span></span>|  
|[<span data-ttu-id="5c8ea-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="5c8ea-122">Eş istemcileri için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="5c8ea-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="5c8ea-124">İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c8ea-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c8ea-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5c8ea-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c8ea-126">Element</span></span>|<span data-ttu-id="5c8ea-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c8ea-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c8ea-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5c8ea-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5c8ea-129">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c8ea-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c8ea-130">Remarks</span></span>  
 <span data-ttu-id="5c8ea-131">Bu yapılandırma öğesi Eş düğüm diğer eş düğümleri kimliğini doğrulamak için kullandığı kimlik doğrulama ayarları yanı sıra bir eş düğüm kafes içindeki diğer düğümlere kendi kimliğini doğrulamak için kullandığı kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="5c8ea-132">Daha fazla bilgi için bkz: [eş kanal ileti kimlik doğrulama](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) ve [eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="5c8ea-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8ea-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c8ea-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="5c8ea-134">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="5c8ea-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="5c8ea-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5c8ea-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5c8ea-136">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="5c8ea-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="5c8ea-137">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="5c8ea-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="5c8ea-138">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5c8ea-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="5c8ea-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5c8ea-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
