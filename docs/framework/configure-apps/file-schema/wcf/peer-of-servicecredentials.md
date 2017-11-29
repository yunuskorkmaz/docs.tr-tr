---
title: "&lt;serviceCredentials&gt; &lt;eşi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3af8c07e86b7ccdf5443a666626b523914a2c45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="adf46-102">&lt;serviceCredentials&gt; &lt;eşi&gt;</span><span class="sxs-lookup"><span data-stu-id="adf46-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="adf46-103">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adf46-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="adf46-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="adf46-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="adf46-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="adf46-105">\<behaviors></span></span>  
<span data-ttu-id="adf46-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="adf46-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="adf46-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="adf46-107">\<behavior></span></span>  
<span data-ttu-id="adf46-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="adf46-108">\<serviceCredentials></span></span>  
<span data-ttu-id="adf46-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="adf46-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adf46-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adf46-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adf46-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="adf46-111">Attributes and Elements</span></span>  
 <span data-ttu-id="adf46-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="adf46-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adf46-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="adf46-113">Attributes</span></span>  
 <span data-ttu-id="adf46-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="adf46-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="adf46-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="adf46-115">Child Elements</span></span>  
  
|<span data-ttu-id="adf46-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="adf46-116">Element</span></span>|<span data-ttu-id="adf46-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adf46-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adf46-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="adf46-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="adf46-119">İmzalama ve eşler arası Hizmetleri için iletileri şifrelemek için kullanılacak bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="adf46-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="adf46-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="adf46-120">.</span></span>|  
|[<span data-ttu-id="adf46-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="adf46-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="adf46-122">İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adf46-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="adf46-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="adf46-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="adf46-124">Eş hizmetler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adf46-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adf46-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="adf46-125">Parent Elements</span></span>  
  
|<span data-ttu-id="adf46-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="adf46-126">Element</span></span>|<span data-ttu-id="adf46-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adf46-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adf46-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="adf46-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="adf46-129">Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="adf46-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adf46-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="adf46-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="adf46-131">Eşler arası ağ</span><span class="sxs-lookup"><span data-stu-id="adf46-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="adf46-132">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="adf46-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="adf46-133">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="adf46-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="adf46-134">Eş kanalı uygulamalarını güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="adf46-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="adf46-135">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="adf46-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
