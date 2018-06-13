---
title: '&lt;serviceCredentials&gt; &lt;eşi&gt;'
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: f50c192639df7b7ed35e863821d5b7a8d62f29bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747687"
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="79606-102">&lt;serviceCredentials&gt; &lt;eşi&gt;</span><span class="sxs-lookup"><span data-stu-id="79606-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="79606-103">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79606-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="79606-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79606-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79606-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="79606-105">\<behaviors></span></span>  
<span data-ttu-id="79606-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="79606-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="79606-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="79606-107">\<behavior></span></span>  
<span data-ttu-id="79606-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="79606-108">\<serviceCredentials></span></span>  
<span data-ttu-id="79606-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="79606-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79606-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79606-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79606-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79606-111">Attributes and Elements</span></span>  
 <span data-ttu-id="79606-112">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="79606-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79606-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79606-113">Attributes</span></span>  
 <span data-ttu-id="79606-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="79606-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79606-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79606-115">Child Elements</span></span>  
  
|<span data-ttu-id="79606-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="79606-116">Element</span></span>|<span data-ttu-id="79606-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79606-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79606-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="79606-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="79606-119">İmzalama ve eşler arası Hizmetleri için iletileri şifrelemek için kullanılacak bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="79606-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="79606-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="79606-120">.</span></span>|  
|[<span data-ttu-id="79606-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="79606-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="79606-122">İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79606-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="79606-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="79606-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="79606-124">Eş hizmetler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79606-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79606-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79606-125">Parent Elements</span></span>  
  
|<span data-ttu-id="79606-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="79606-126">Element</span></span>|<span data-ttu-id="79606-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79606-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79606-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="79606-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="79606-129">Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79606-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79606-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79606-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="79606-131">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="79606-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="79606-132">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="79606-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="79606-133">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="79606-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="79606-134">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="79606-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="79606-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="79606-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
