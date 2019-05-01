---
title: <peer> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: d726ab460141b1e373a1cabf770b8958f50319eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783402"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="66fbf-102">\<Eş >, \<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="66fbf-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="66fbf-103">Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66fbf-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="66fbf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="66fbf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="66fbf-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="66fbf-105">\<behaviors></span></span>  
<span data-ttu-id="66fbf-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="66fbf-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="66fbf-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="66fbf-107">\<behavior></span></span>  
<span data-ttu-id="66fbf-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="66fbf-108">\<serviceCredentials></span></span>  
<span data-ttu-id="66fbf-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="66fbf-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66fbf-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66fbf-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66fbf-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="66fbf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="66fbf-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66fbf-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66fbf-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="66fbf-113">Attributes</span></span>  
 <span data-ttu-id="66fbf-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="66fbf-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66fbf-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="66fbf-115">Child Elements</span></span>  
  
|<span data-ttu-id="66fbf-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="66fbf-116">Element</span></span>|<span data-ttu-id="66fbf-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66fbf-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66fbf-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="66fbf-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="66fbf-119">İmzalama ve eşler arası Hizmetleri iletileri şifrelemek için kullanılacak bir X.509 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="66fbf-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="66fbf-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="66fbf-120">.</span></span>|  
|[<span data-ttu-id="66fbf-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="66fbf-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="66fbf-122">İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66fbf-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="66fbf-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="66fbf-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="66fbf-124">Eş hizmetler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66fbf-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66fbf-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="66fbf-125">Parent Elements</span></span>  
  
|<span data-ttu-id="66fbf-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="66fbf-126">Element</span></span>|<span data-ttu-id="66fbf-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66fbf-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66fbf-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="66fbf-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="66fbf-129">Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66fbf-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66fbf-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66fbf-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="66fbf-131">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="66fbf-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="66fbf-132">[Eş kanal ileti kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="66fbf-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="66fbf-133">[Eş kanal özel kimlik doğrulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="66fbf-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="66fbf-134">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="66fbf-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="66fbf-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="66fbf-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
