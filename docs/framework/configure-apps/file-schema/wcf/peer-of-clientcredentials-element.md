---
title: <peer><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400092"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="1706b-102">\<\<ClientCredentials > öğesinin eşdüzey ></span><span class="sxs-lookup"><span data-stu-id="1706b-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="1706b-103">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1706b-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
<span data-ttu-id="1706b-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1706b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1706b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1706b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1706b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1706b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1706b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1706b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="1706b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1706b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="1706b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="1706b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="1706b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<eş >**</span><span class="sxs-lookup"><span data-stu-id="1706b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1706b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1706b-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1706b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1706b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1706b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1706b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1706b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1706b-114">Attributes</span></span>  
 <span data-ttu-id="1706b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1706b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1706b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1706b-116">Child Elements</span></span>  
  
|<span data-ttu-id="1706b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1706b-117">Element</span></span>|<span data-ttu-id="1706b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1706b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1706b-119">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="1706b-119">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="1706b-120">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="1706b-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="1706b-121">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="1706b-121">.</span></span>|  
|[<span data-ttu-id="1706b-122">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1706b-122">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="1706b-123">Eş istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1706b-123">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="1706b-124">\<Iletienderauthentication ></span><span class="sxs-lookup"><span data-stu-id="1706b-124">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="1706b-125">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1706b-125">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1706b-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1706b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1706b-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="1706b-127">Element</span></span>|<span data-ttu-id="1706b-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1706b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1706b-129">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1706b-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="1706b-130">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1706b-130">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1706b-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1706b-131">Remarks</span></span>  
 <span data-ttu-id="1706b-132">Bu yapılandırma öğesi, bir eş düğümün ağ üzerindeki diğer düğümlere kimliğini doğrulamak için kullandığı kimlik bilgilerini ve bir eş düğümün diğer eş düğümlerinin kimliğini doğrulamak için kullandığı kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1706b-132">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="1706b-133">Daha fazla bilgi için bkz. [eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) ve [eş kanal uygulamalarının güvenliğini sağlama](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1706b-133">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1706b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1706b-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="1706b-135">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="1706b-135">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="1706b-136">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1706b-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="1706b-137">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1706b-137">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1706b-138">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1706b-138">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1706b-139">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1706b-139">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="1706b-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1706b-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
