---
title: '&lt;clientCredentials&gt; Öğesi &lt;eşi&gt;'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 9d63aaaa6404b791559d1288730098075f1fd8eb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504489"
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="64f31-102">&lt;clientCredentials&gt; Öğesi &lt;eşi&gt;</span><span class="sxs-lookup"><span data-stu-id="64f31-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="64f31-103">Eşler arası istemcilerin kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64f31-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="64f31-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="64f31-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="64f31-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="64f31-105">\<behaviors></span></span>  
<span data-ttu-id="64f31-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="64f31-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="64f31-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="64f31-107">\<behavior></span></span>  
<span data-ttu-id="64f31-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="64f31-108">\<clientCredentials></span></span>  
<span data-ttu-id="64f31-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="64f31-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64f31-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64f31-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64f31-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="64f31-111">Attributes and Elements</span></span>  
 <span data-ttu-id="64f31-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64f31-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64f31-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="64f31-113">Attributes</span></span>  
 <span data-ttu-id="64f31-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="64f31-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64f31-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="64f31-115">Child Elements</span></span>  
  
|<span data-ttu-id="64f31-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="64f31-116">Element</span></span>|<span data-ttu-id="64f31-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64f31-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64f31-118">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="64f31-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="64f31-119">İmzalama ve eşler arası istemcileri için iletileri şifrelemek için bir X.509 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="64f31-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="64f31-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="64f31-120">.</span></span>|  
|[<span data-ttu-id="64f31-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="64f31-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="64f31-122">Eş istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64f31-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="64f31-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="64f31-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="64f31-124">İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64f31-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64f31-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="64f31-125">Parent Elements</span></span>  
  
|<span data-ttu-id="64f31-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="64f31-126">Element</span></span>|<span data-ttu-id="64f31-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64f31-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64f31-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="64f31-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="64f31-129">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64f31-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64f31-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64f31-130">Remarks</span></span>  
 <span data-ttu-id="64f31-131">Bu yapılandırma öğesini bir eşdüzey düğüm diğer eş düğümleri kimlik doğrulaması için kullandığı kimlik doğrulama ayarları yanı sıra, diğer düğümlerde kafes kendi kimliğini doğrulamak için bir eş düğüm kullandığı kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64f31-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="64f31-132">Daha fazla bilgi için [eş kanal iletisi kimlik doğrulaması](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) ve [eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="64f31-132">For more information, see [Peer Channel Message Authentication](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f31-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64f31-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="64f31-134">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="64f31-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="64f31-135">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="64f31-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="64f31-136">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="64f31-136">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="64f31-137">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="64f31-137">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="64f31-138">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="64f31-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="64f31-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="64f31-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
