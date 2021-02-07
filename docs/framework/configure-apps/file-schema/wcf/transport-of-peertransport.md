---
description: 'Hakkında daha fazla bilgi <transport> edinin: <peerTransport>'
title: <transport> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: ba3405c5dfadb513f92ebd537409a3f7b12fa291
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664515"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="3e536-103">\<transport> / \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="3e536-103">\<transport> of \<peerTransport></span></span>

<span data-ttu-id="3e536-104">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e536-104">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="3e536-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e536-105">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e536-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e536-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3e536-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="3e536-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e536-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e536-108">Attributes</span></span>  
  
|<span data-ttu-id="3e536-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e536-109">Attribute</span></span>|<span data-ttu-id="3e536-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e536-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e536-111">credentialType</span><span class="sxs-lookup"><span data-stu-id="3e536-111">credentialType</span></span>|<span data-ttu-id="3e536-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e536-112">Optional.</span></span> <span data-ttu-id="3e536-113">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e536-113">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="3e536-114">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="3e536-114">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="3e536-115">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="3e536-115">credentialType Attribute</span></span>  
  
|<span data-ttu-id="3e536-116">Değer</span><span class="sxs-lookup"><span data-stu-id="3e536-116">Value</span></span>|<span data-ttu-id="3e536-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e536-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3e536-118">Sertifika</span><span class="sxs-lookup"><span data-stu-id="3e536-118">Certificate</span></span>|<span data-ttu-id="3e536-119">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e536-119">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="3e536-120">Parola</span><span class="sxs-lookup"><span data-stu-id="3e536-120">Password</span></span>|<span data-ttu-id="3e536-121">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e536-121">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e536-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e536-122">Child Elements</span></span>  

 <span data-ttu-id="3e536-123">Yok</span><span class="sxs-lookup"><span data-stu-id="3e536-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e536-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e536-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3e536-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e536-125">Element</span></span>|<span data-ttu-id="3e536-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e536-126">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="3e536-127">Bir eş taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e536-127">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e536-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e536-128">Remarks</span></span>  

 <span data-ttu-id="3e536-129">Bu öğe yalnızca mode özniteliği [\<security>](security-of-peertransport.md) veya olarak ayarlandıysa ayarlanır `Transport` `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="3e536-129">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e536-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e536-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3e536-131">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="3e536-131">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="3e536-132">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="3e536-132">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="3e536-133">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="3e536-133">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3e536-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3e536-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3e536-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="3e536-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3e536-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3e536-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
