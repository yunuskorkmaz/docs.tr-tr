---
title: <peer> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 7f6669d3f53a6ee0d189786fa9ca3625fdedd127
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162484"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="a55dd-102">\<peer> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a55dd-102">\<peer> of \<serviceCredentials></span></span>

<span data-ttu-id="a55dd-103">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a55dd-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="a55dd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a55dd-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a55dd-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a55dd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a55dd-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="a55dd-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a55dd-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a55dd-107">Attributes</span></span>  

 <span data-ttu-id="a55dd-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="a55dd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a55dd-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a55dd-109">Child Elements</span></span>  
  
|<span data-ttu-id="a55dd-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="a55dd-110">Element</span></span>|<span data-ttu-id="a55dd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a55dd-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="a55dd-112">Eşler arası hizmetler için iletileri imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="a55dd-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="a55dd-113">.</span><span class="sxs-lookup"><span data-stu-id="a55dd-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="a55dd-114">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a55dd-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="a55dd-115">Eş Hizmetleri için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a55dd-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a55dd-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a55dd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a55dd-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="a55dd-117">Element</span></span>|<span data-ttu-id="a55dd-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a55dd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="a55dd-119">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a55dd-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a55dd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a55dd-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="a55dd-121">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="a55dd-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="a55dd-122">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a55dd-122">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="a55dd-123">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a55dd-123">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="a55dd-124">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a55dd-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="a55dd-125">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a55dd-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
