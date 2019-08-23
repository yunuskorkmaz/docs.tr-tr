---
title: <peer><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 2f1cb5689125e2483a74dcac515beb07abbb7c70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934042"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="1e8e1-102">\<\<ClientCredentials > öğesinin eşdüzey ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="1e8e1-103">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="1e8e1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1e8e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e8e1-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-105">\<behaviors></span></span>  
<span data-ttu-id="1e8e1-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1e8e1-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-107">\<behavior></span></span>  
<span data-ttu-id="1e8e1-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-108">\<clientCredentials></span></span>  
<span data-ttu-id="1e8e1-109">\<eş ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e8e1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e8e1-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e8e1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e8e1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1e8e1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e8e1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1e8e1-113">Attributes</span></span>  
 <span data-ttu-id="1e8e1-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e8e1-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e8e1-115">Child Elements</span></span>  
  
|<span data-ttu-id="1e8e1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e8e1-116">Element</span></span>|<span data-ttu-id="1e8e1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e8e1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e8e1-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-118">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="1e8e1-119">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="1e8e1-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-120">.</span></span>|  
|[<span data-ttu-id="1e8e1-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-121">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="1e8e1-122">Eş istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="1e8e1-123">\<Iletienderauthentication ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-123">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="1e8e1-124">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e8e1-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e8e1-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1e8e1-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e8e1-126">Element</span></span>|<span data-ttu-id="1e8e1-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e8e1-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e8e1-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1e8e1-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="1e8e1-129">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e8e1-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e8e1-130">Remarks</span></span>  
 <span data-ttu-id="1e8e1-131">Bu yapılandırma öğesi, bir eş düğümün ağ üzerindeki diğer düğümlere kimliğini doğrulamak için kullandığı kimlik bilgilerini ve bir eş düğümün diğer eş düğümlerinin kimliğini doğrulamak için kullandığı kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="1e8e1-132">Daha fazla bilgi için bkz. [eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) ve [eş kanal uygulamalarının güvenliğini sağlama](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1e8e1-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8e1-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="1e8e1-134">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="1e8e1-134">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="1e8e1-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1e8e1-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="1e8e1-136">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e8e1-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1e8e1-137">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e8e1-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1e8e1-138">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1e8e1-138">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="1e8e1-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1e8e1-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
