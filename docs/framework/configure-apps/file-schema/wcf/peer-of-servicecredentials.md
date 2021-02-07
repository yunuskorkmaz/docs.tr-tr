---
description: 'Hakkında daha fazla bilgi <peer> edinin: <serviceCredentials>'
title: <peer> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 4d959f5061bb8069623b277219576dbd77ea52c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683742"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="2d7f7-103">\<peer> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2d7f7-103">\<peer> of \<serviceCredentials></span></span>

<span data-ttu-id="2d7f7-104">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-104">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="2d7f7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2d7f7-105">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d7f7-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d7f7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2d7f7-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="2d7f7-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d7f7-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2d7f7-108">Attributes</span></span>  

 <span data-ttu-id="2d7f7-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2d7f7-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d7f7-110">Child Elements</span></span>  
  
|<span data-ttu-id="2d7f7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d7f7-111">Element</span></span>|<span data-ttu-id="2d7f7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d7f7-112">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="2d7f7-113">Eşler arası hizmetler için iletileri imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-113">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="2d7f7-114">.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-114">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="2d7f7-115">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-115">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="2d7f7-116">Eş Hizmetleri için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-116">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d7f7-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2d7f7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2d7f7-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="2d7f7-118">Element</span></span>|<span data-ttu-id="2d7f7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d7f7-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="2d7f7-120">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-120">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d7f7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d7f7-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="2d7f7-122">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="2d7f7-122">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2d7f7-123">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2d7f7-123">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2d7f7-124">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2d7f7-124">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2d7f7-125">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2d7f7-125">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="2d7f7-126">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2d7f7-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
