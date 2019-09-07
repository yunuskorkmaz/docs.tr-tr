---
title: <transport> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399296"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="30a85-102">\<\<peertransport > taşıma ></span><span class="sxs-lookup"><span data-stu-id="30a85-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="30a85-103">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="30a85-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
<span data-ttu-id="30a85-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="30a85-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="30a85-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="30a85-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="30a85-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="30a85-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="30a85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="30a85-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="30a85-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="30a85-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="30a85-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="30a85-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="30a85-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="30a85-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)</span></span>\
<span data-ttu-id="30a85-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**</span><span class="sxs-lookup"><span data-stu-id="30a85-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a85-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30a85-112">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30a85-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30a85-113">Attributes and Elements</span></span>  
 <span data-ttu-id="30a85-114">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="30a85-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30a85-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30a85-115">Attributes</span></span>  
  
|<span data-ttu-id="30a85-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30a85-116">Attribute</span></span>|<span data-ttu-id="30a85-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30a85-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30a85-118">credentialType</span><span class="sxs-lookup"><span data-stu-id="30a85-118">credentialType</span></span>|<span data-ttu-id="30a85-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="30a85-119">Optional.</span></span> <span data-ttu-id="30a85-120">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="30a85-120">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="30a85-121">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="30a85-121">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="30a85-122">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="30a85-122">credentialType Attribute</span></span>  
  
|<span data-ttu-id="30a85-123">Değer</span><span class="sxs-lookup"><span data-stu-id="30a85-123">Value</span></span>|<span data-ttu-id="30a85-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30a85-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="30a85-125">Sertifika</span><span class="sxs-lookup"><span data-stu-id="30a85-125">Certificate</span></span>|<span data-ttu-id="30a85-126">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="30a85-126">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="30a85-127">Parola</span><span class="sxs-lookup"><span data-stu-id="30a85-127">Password</span></span>|<span data-ttu-id="30a85-128">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="30a85-128">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30a85-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30a85-129">Child Elements</span></span>  
 <span data-ttu-id="30a85-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="30a85-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30a85-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30a85-131">Parent Elements</span></span>  
  
|<span data-ttu-id="30a85-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="30a85-132">Element</span></span>|<span data-ttu-id="30a85-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30a85-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30a85-134">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="30a85-134">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="30a85-135">Bir eş taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30a85-135">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30a85-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30a85-136">Remarks</span></span>  
 <span data-ttu-id="30a85-137">Bu öğe yalnızca [ \<güvenlik >](security-of-peertransport.md) mod özniteliği veya `TransportWithMessageCredential`olarak `Transport` ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="30a85-137">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a85-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30a85-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="30a85-139">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="30a85-139">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="30a85-140">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="30a85-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="30a85-141">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="30a85-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="30a85-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30a85-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="30a85-143">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="30a85-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="30a85-144">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30a85-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="30a85-145">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30a85-145">\<customBinding></span></span>](custombinding.md)
