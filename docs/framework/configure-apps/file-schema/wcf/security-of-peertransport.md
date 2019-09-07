---
title: <security> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399776"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="bd687-102">\<\<peertransport > Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bd687-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="bd687-103">Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi bir eş kanalla ilişkili güvenlik ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="bd687-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="bd687-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd687-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd687-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd687-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd687-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bd687-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bd687-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="bd687-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="bd687-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="bd687-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bd687-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="bd687-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="bd687-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**</span><span class="sxs-lookup"><span data-stu-id="bd687-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd687-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd687-111">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd687-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd687-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bd687-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd687-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd687-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd687-114">Attributes</span></span>  
  
|<span data-ttu-id="bd687-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bd687-115">Attribute</span></span>|<span data-ttu-id="bd687-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd687-116">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="bd687-117">Uygulanacak güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd687-117">Specifies the type of security to be applied.</span></span> <span data-ttu-id="bd687-118">Varsayılan değer Iletidir.</span><span class="sxs-lookup"><span data-stu-id="bd687-118">The default value is Message.</span></span> <span data-ttu-id="bd687-119">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="bd687-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="bd687-120">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="bd687-120">mode Attribute</span></span>  
  
|<span data-ttu-id="bd687-121">Değer</span><span class="sxs-lookup"><span data-stu-id="bd687-121">Value</span></span>|<span data-ttu-id="bd687-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd687-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="bd687-123">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="bd687-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="bd687-124">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bd687-124">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="bd687-125">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd687-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="bd687-126">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd687-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="bd687-127">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd687-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd687-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd687-128">Child Elements</span></span>  
  
|<span data-ttu-id="bd687-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd687-129">Element</span></span>|<span data-ttu-id="bd687-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd687-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd687-131">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="bd687-131">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="bd687-132">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd687-132">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="bd687-133">Bu öğe, bir `clientCredentialType` hizmetle etkileşim kurarken kullanılacak kimlik bilgilerini belirten bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bd687-133">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="bd687-134">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="bd687-134">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="bd687-135">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="bd687-135">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd687-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd687-136">Parent Elements</span></span>  
  
|<span data-ttu-id="bd687-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd687-137">Element</span></span>|<span data-ttu-id="bd687-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd687-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd687-139">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="bd687-139">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="bd687-140">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd687-140">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd687-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd687-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bd687-142">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="bd687-142">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="bd687-143">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="bd687-143">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="bd687-144">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="bd687-144">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="bd687-145">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bd687-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bd687-146">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="bd687-146">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bd687-147">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bd687-147">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bd687-148">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bd687-148">\<customBinding></span></span>](custombinding.md)
