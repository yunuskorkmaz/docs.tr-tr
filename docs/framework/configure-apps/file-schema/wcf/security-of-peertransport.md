---
description: 'Hakkında daha fazla bilgi <security> edinin: <peerTransport>'
title: <security> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 592f886377a2d5f2008be900a9e7586385fb3782
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786830"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="4a6a1-103">\<security> / \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="4a6a1-103">\<security> of \<peerTransport></span></span>

<span data-ttu-id="4a6a1-104">Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi bir eş kanalla ilişkili güvenlik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-104">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="4a6a1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a6a1-105">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a6a1-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a6a1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4a6a1-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a6a1-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a6a1-108">Attributes</span></span>  
  
|<span data-ttu-id="4a6a1-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4a6a1-109">Attribute</span></span>|<span data-ttu-id="4a6a1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a6a1-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="4a6a1-111">Uygulanacak güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-111">Specifies the type of security to be applied.</span></span> <span data-ttu-id="4a6a1-112">Varsayılan değer Iletidir.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-112">The default value is Message.</span></span> <span data-ttu-id="4a6a1-113">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="4a6a1-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4a6a1-114">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="4a6a1-114">mode Attribute</span></span>  
  
|<span data-ttu-id="4a6a1-115">Değer</span><span class="sxs-lookup"><span data-stu-id="4a6a1-115">Value</span></span>|<span data-ttu-id="4a6a1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a6a1-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="4a6a1-117">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="4a6a1-118">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-118">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="4a6a1-119">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="4a6a1-120">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-120">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="4a6a1-121">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-121">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a6a1-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a6a1-122">Child Elements</span></span>  
  
|<span data-ttu-id="4a6a1-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a6a1-123">Element</span></span>|<span data-ttu-id="4a6a1-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a6a1-124">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="4a6a1-125">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-125">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="4a6a1-126">Bu öğe, `clientCredentialType` bir hizmetle etkileşim kurarken kullanılacak kimlik bilgilerini belirten bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-126">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="4a6a1-127">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="4a6a1-127">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="4a6a1-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="4a6a1-128">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a6a1-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a6a1-129">Parent Elements</span></span>  
  
|<span data-ttu-id="4a6a1-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a6a1-130">Element</span></span>|<span data-ttu-id="4a6a1-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a6a1-131">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="4a6a1-132">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-132">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a6a1-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a6a1-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4a6a1-134">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4a6a1-134">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="4a6a1-135">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="4a6a1-135">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="4a6a1-136">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="4a6a1-136">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4a6a1-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4a6a1-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4a6a1-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4a6a1-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4a6a1-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4a6a1-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
