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
ms.openlocfilehash: c3479b52c6e06b7b9ebd69d46780e8dca70d2ef7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="e2979-102">&lt;clientCredentials&gt; Öğesi &lt;eşi&gt;</span><span class="sxs-lookup"><span data-stu-id="e2979-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="e2979-103">Eşler arası istemcileri kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2979-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="e2979-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2979-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2979-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="e2979-105">\<behaviors></span></span>  
<span data-ttu-id="e2979-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e2979-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e2979-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e2979-107">\<behavior></span></span>  
<span data-ttu-id="e2979-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e2979-108">\<clientCredentials></span></span>  
<span data-ttu-id="e2979-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="e2979-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2979-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2979-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2979-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2979-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e2979-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2979-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2979-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2979-113">Attributes</span></span>  
 <span data-ttu-id="e2979-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e2979-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2979-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2979-115">Child Elements</span></span>  
  
|<span data-ttu-id="e2979-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2979-116">Element</span></span>|<span data-ttu-id="e2979-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2979-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2979-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="e2979-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="e2979-119">İmzalama ve eşler arası istemcileri için iletileri şifrelemek için kullanılacak bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2979-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="e2979-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="e2979-120">.</span></span>|  
|[<span data-ttu-id="e2979-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="e2979-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="e2979-122">Eş istemcileri için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2979-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="e2979-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="e2979-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="e2979-124">İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2979-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2979-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2979-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e2979-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2979-126">Element</span></span>|<span data-ttu-id="e2979-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2979-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2979-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e2979-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="e2979-129">Bir hizmet için bir istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2979-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2979-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2979-130">Remarks</span></span>  
 <span data-ttu-id="e2979-131">Bu yapılandırma öğesi Eş düğüm diğer eş düğümleri kimliğini doğrulamak için kullandığı kimlik doğrulama ayarları yanı sıra bir eş düğüm kafes içindeki diğer düğümlere kendi kimliğini doğrulamak için kullandığı kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2979-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="e2979-132">Daha fazla bilgi için bkz: [eş kanal ileti kimlik doğrulama](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) ve [eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="e2979-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2979-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2979-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="e2979-134">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="e2979-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="e2979-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e2979-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="e2979-136">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e2979-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="e2979-137">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="e2979-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="e2979-138">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e2979-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="e2979-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="e2979-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
