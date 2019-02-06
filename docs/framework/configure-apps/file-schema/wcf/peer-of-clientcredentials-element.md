---
title: <peer> ' ın <clientCredentials> öğesi
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 8bdb52ccaaa8b41b3321447d2d68f9021a093481
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758358"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="952ce-102">\<Eş >, \<clientCredentials > öğesi</span><span class="sxs-lookup"><span data-stu-id="952ce-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="952ce-103">Eşler arası istemcilerin kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="952ce-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="952ce-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="952ce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="952ce-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="952ce-105">\<behaviors></span></span>  
<span data-ttu-id="952ce-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="952ce-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="952ce-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="952ce-107">\<behavior></span></span>  
<span data-ttu-id="952ce-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="952ce-108">\<clientCredentials></span></span>  
<span data-ttu-id="952ce-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="952ce-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952ce-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="952ce-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="952ce-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="952ce-111">Attributes and Elements</span></span>  
 <span data-ttu-id="952ce-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="952ce-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="952ce-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="952ce-113">Attributes</span></span>  
 <span data-ttu-id="952ce-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="952ce-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="952ce-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="952ce-115">Child Elements</span></span>  
  
|<span data-ttu-id="952ce-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="952ce-116">Element</span></span>|<span data-ttu-id="952ce-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="952ce-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="952ce-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="952ce-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="952ce-119">İmzalama ve eşler arası istemcileri için iletileri şifrelemek için bir X.509 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="952ce-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="952ce-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="952ce-120">.</span></span>|  
|[<span data-ttu-id="952ce-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="952ce-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="952ce-122">Eş istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="952ce-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="952ce-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="952ce-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="952ce-124">İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="952ce-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="952ce-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="952ce-125">Parent Elements</span></span>  
  
|<span data-ttu-id="952ce-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="952ce-126">Element</span></span>|<span data-ttu-id="952ce-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="952ce-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="952ce-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="952ce-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="952ce-129">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="952ce-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="952ce-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="952ce-130">Remarks</span></span>  
 <span data-ttu-id="952ce-131">Bu yapılandırma öğesini bir eşdüzey düğüm diğer eş düğümleri kimlik doğrulaması için kullandığı kimlik doğrulama ayarları yanı sıra, diğer düğümlerde kafes kendi kimliğini doğrulamak için bir eş düğüm kullandığı kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="952ce-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="952ce-132">Daha fazla bilgi için [eş kanal iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) ve [eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="952ce-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952ce-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="952ce-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="952ce-134">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="952ce-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="952ce-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="952ce-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- <span data-ttu-id="952ce-136">[Eş kanal ileti kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="952ce-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="952ce-137">[Eş kanal özel kimlik doğrulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="952ce-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="952ce-138">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="952ce-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="952ce-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="952ce-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
