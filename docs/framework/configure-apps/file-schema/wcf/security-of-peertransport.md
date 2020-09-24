---
title: <security> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: f37c336b0e42993e1eef3f06e2f919705f425a2e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169966"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="36852-102">\<security> / \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="36852-102">\<security> of \<peerTransport></span></span>

<span data-ttu-id="36852-103">Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi bir eş kanalla ilişkili güvenlik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="36852-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="36852-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="36852-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36852-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36852-105">Attributes and Elements</span></span>  

 <span data-ttu-id="36852-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36852-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36852-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36852-107">Attributes</span></span>  
  
|<span data-ttu-id="36852-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="36852-108">Attribute</span></span>|<span data-ttu-id="36852-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36852-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="36852-110">Uygulanacak güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="36852-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="36852-111">Varsayılan değer Iletidir.</span><span class="sxs-lookup"><span data-stu-id="36852-111">The default value is Message.</span></span> <span data-ttu-id="36852-112">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="36852-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="36852-113">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="36852-113">mode Attribute</span></span>  
  
|<span data-ttu-id="36852-114">Değer</span><span class="sxs-lookup"><span data-stu-id="36852-114">Value</span></span>|<span data-ttu-id="36852-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36852-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="36852-116">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="36852-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="36852-117">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="36852-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="36852-118">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="36852-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="36852-119">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="36852-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="36852-120">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="36852-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36852-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36852-121">Child Elements</span></span>  
  
|<span data-ttu-id="36852-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="36852-122">Element</span></span>|<span data-ttu-id="36852-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36852-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="36852-124">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36852-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="36852-125">Bu öğe, `clientCredentialType` bir hizmetle etkileşim kurarken kullanılacak kimlik bilgilerini belirten bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="36852-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="36852-126">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="36852-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="36852-127">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="36852-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36852-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36852-128">Parent Elements</span></span>  
  
|<span data-ttu-id="36852-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="36852-129">Element</span></span>|<span data-ttu-id="36852-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36852-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="36852-131">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36852-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36852-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36852-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="36852-133">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="36852-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="36852-134">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="36852-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="36852-135">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="36852-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="36852-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="36852-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="36852-137">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="36852-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="36852-138">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="36852-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
