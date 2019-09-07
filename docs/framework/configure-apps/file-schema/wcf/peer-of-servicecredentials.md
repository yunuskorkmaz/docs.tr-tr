---
title: <peer> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397636"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="83968-102">\<\<ServiceCredentials > > eşi</span><span class="sxs-lookup"><span data-stu-id="83968-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="83968-103">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="83968-103">Specifies the current credentials for a peer node.</span></span>  
  
<span data-ttu-id="83968-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="83968-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="83968-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="83968-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="83968-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="83968-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="83968-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="83968-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="83968-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="83968-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="83968-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="83968-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="83968-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<eş >**</span><span class="sxs-lookup"><span data-stu-id="83968-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83968-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83968-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83968-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="83968-112">Attributes and Elements</span></span>  
 <span data-ttu-id="83968-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="83968-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83968-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="83968-114">Attributes</span></span>  
 <span data-ttu-id="83968-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="83968-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="83968-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="83968-116">Child Elements</span></span>  
  
|<span data-ttu-id="83968-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="83968-117">Element</span></span>|<span data-ttu-id="83968-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83968-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83968-119">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="83968-119">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="83968-120">Eşler arası hizmetler için iletileri imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="83968-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="83968-121">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="83968-121">.</span></span>|  
|[<span data-ttu-id="83968-122">\<Iletienderauthentication ></span><span class="sxs-lookup"><span data-stu-id="83968-122">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="83968-123">İleti gönderenlerin kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="83968-123">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="83968-124">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="83968-124">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="83968-125">Eş Hizmetleri için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="83968-125">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83968-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="83968-126">Parent Elements</span></span>  
  
|<span data-ttu-id="83968-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="83968-127">Element</span></span>|<span data-ttu-id="83968-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="83968-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83968-129">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="83968-129">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="83968-130">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="83968-130">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83968-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83968-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="83968-132">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="83968-132">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="83968-133">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="83968-133">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="83968-134">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="83968-134">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="83968-135">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="83968-135">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="83968-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="83968-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
