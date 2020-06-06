---
title: <peer><clientCredentials>öğesinin
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400092"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="15343-102">\<peer>\<clientCredentials>öğesinin</span><span class="sxs-lookup"><span data-stu-id="15343-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="15343-103">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15343-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="15343-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15343-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15343-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15343-105">Attributes and Elements</span></span>  
 <span data-ttu-id="15343-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15343-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15343-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15343-107">Attributes</span></span>  
 <span data-ttu-id="15343-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="15343-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15343-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15343-109">Child Elements</span></span>  
  
|<span data-ttu-id="15343-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="15343-110">Element</span></span>|<span data-ttu-id="15343-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15343-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="15343-112">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="15343-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="15343-113">.</span><span class="sxs-lookup"><span data-stu-id="15343-113">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="15343-114">Eş istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15343-114">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="15343-115">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15343-115">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15343-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15343-116">Parent Elements</span></span>  
  
|<span data-ttu-id="15343-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="15343-117">Element</span></span>|<span data-ttu-id="15343-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15343-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="15343-119">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15343-119">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15343-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15343-120">Remarks</span></span>  
 <span data-ttu-id="15343-121">Bu yapılandırma öğesi, bir eş düğümün ağ üzerindeki diğer düğümlere kimliğini doğrulamak için kullandığı kimlik bilgilerini ve bir eş düğümün diğer eş düğümlerinin kimliğini doğrulamak için kullandığı kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15343-121">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="15343-122">Daha fazla bilgi için bkz. [eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) ve [eş kanal uygulamalarının güvenliğini sağlama](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="15343-122">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15343-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15343-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="15343-124">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="15343-124">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="15343-125">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="15343-125">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="15343-126">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="15343-126">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="15343-127">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="15343-127">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="15343-128">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="15343-128">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="15343-129">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="15343-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
