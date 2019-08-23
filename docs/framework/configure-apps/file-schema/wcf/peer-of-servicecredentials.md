---
title: <peer> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50415cb9b35d2a2053efa3313a415de518b7e36e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933781"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="fc8f2-102">\<\<ServiceCredentials > > eşi</span><span class="sxs-lookup"><span data-stu-id="fc8f2-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="fc8f2-103">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="fc8f2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fc8f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fc8f2-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="fc8f2-105">\<behaviors></span></span>  
<span data-ttu-id="fc8f2-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fc8f2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fc8f2-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="fc8f2-107">\<behavior></span></span>  
<span data-ttu-id="fc8f2-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fc8f2-108">\<serviceCredentials></span></span>  
<span data-ttu-id="fc8f2-109">\<eş ></span><span class="sxs-lookup"><span data-stu-id="fc8f2-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8f2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc8f2-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc8f2-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc8f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fc8f2-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="fc8f2-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc8f2-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc8f2-113">Attributes</span></span>  
 <span data-ttu-id="fc8f2-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fc8f2-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc8f2-115">Child Elements</span></span>  
  
|<span data-ttu-id="fc8f2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc8f2-116">Element</span></span>|<span data-ttu-id="fc8f2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc8f2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc8f2-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="fc8f2-118">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="fc8f2-119">Eşler arası hizmetler için iletileri imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="fc8f2-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-120">.</span></span>|  
|[<span data-ttu-id="fc8f2-121">\<Iletienderauthentication ></span><span class="sxs-lookup"><span data-stu-id="fc8f2-121">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="fc8f2-122">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="fc8f2-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="fc8f2-123">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="fc8f2-124">Eş Hizmetleri için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc8f2-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc8f2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fc8f2-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc8f2-126">Element</span></span>|<span data-ttu-id="fc8f2-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc8f2-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc8f2-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="fc8f2-128">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="fc8f2-129">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc8f2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc8f2-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="fc8f2-131">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="fc8f2-131">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="fc8f2-132">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fc8f2-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="fc8f2-133">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fc8f2-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="fc8f2-134">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fc8f2-134">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="fc8f2-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fc8f2-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
