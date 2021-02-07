---
description: 'Hakkında daha fazla bilgi edinin: <peer> <clientCredentials> öğe'
title: <peer><clientCredentials>öğesinin
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 1ff9386ba51dcf6bab6df71bd345cdaa59f18e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683794"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="1c4f4-103">\<peer>\<clientCredentials>öğesinin</span><span class="sxs-lookup"><span data-stu-id="1c4f4-103">\<peer> of \<clientCredentials> Element</span></span>

<span data-ttu-id="1c4f4-104">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-104">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="1c4f4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1c4f4-105">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c4f4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c4f4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1c4f4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c4f4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c4f4-108">Attributes</span></span>  

 <span data-ttu-id="1c4f4-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1c4f4-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c4f4-110">Child Elements</span></span>  
  
|<span data-ttu-id="1c4f4-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c4f4-111">Element</span></span>|<span data-ttu-id="1c4f4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c4f4-112">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="1c4f4-113">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-113">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="1c4f4-114">.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-114">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="1c4f4-115">Eş istemciler için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-115">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="1c4f4-116">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-116">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c4f4-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c4f4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1c4f4-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c4f4-118">Element</span></span>|<span data-ttu-id="1c4f4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c4f4-119">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="1c4f4-120">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-120">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c4f4-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c4f4-121">Remarks</span></span>  

 <span data-ttu-id="1c4f4-122">Bu yapılandırma öğesi, bir eş düğümün ağ üzerindeki diğer düğümlere kimliğini doğrulamak için kullandığı kimlik bilgilerini ve bir eş düğümün diğer eş düğümlerinin kimliğini doğrulamak için kullandığı kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-122">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="1c4f4-123">Daha fazla bilgi için bkz. [eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) ve [eş kanal uygulamalarının güvenliğini sağlama](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1c4f4-123">For more information, see [Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4f4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c4f4-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="1c4f4-125">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="1c4f4-125">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="1c4f4-126">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1c4f4-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="1c4f4-127">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1c4f4-127">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1c4f4-128">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1c4f4-128">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1c4f4-129">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1c4f4-129">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="1c4f4-130">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1c4f4-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
