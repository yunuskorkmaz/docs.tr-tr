---
title: <transport> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 5dbc55db25c0c49d72ec2cd8dd1041a3f8705d8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940639"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="30514-102">\<\<peertransport > taşıma ></span><span class="sxs-lookup"><span data-stu-id="30514-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="30514-103">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="30514-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="30514-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30514-104">\<system.serviceModel></span></span>  
<span data-ttu-id="30514-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30514-105">\<bindings></span></span>  
<span data-ttu-id="30514-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30514-106">\<customBinding></span></span>  
<span data-ttu-id="30514-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30514-107">\<binding></span></span>  
<span data-ttu-id="30514-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="30514-108">\<peerTransport></span></span>  
<span data-ttu-id="30514-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="30514-109">\<security></span></span>  
<span data-ttu-id="30514-110">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="30514-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30514-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30514-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30514-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30514-112">Attributes and Elements</span></span>  
 <span data-ttu-id="30514-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="30514-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30514-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30514-114">Attributes</span></span>  
  
|<span data-ttu-id="30514-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30514-115">Attribute</span></span>|<span data-ttu-id="30514-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30514-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30514-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="30514-117">credentialType</span></span>|<span data-ttu-id="30514-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="30514-118">Optional.</span></span> <span data-ttu-id="30514-119">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="30514-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="30514-120">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="30514-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="30514-121">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="30514-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="30514-122">Değer</span><span class="sxs-lookup"><span data-stu-id="30514-122">Value</span></span>|<span data-ttu-id="30514-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30514-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="30514-124">Sertifika</span><span class="sxs-lookup"><span data-stu-id="30514-124">Certificate</span></span>|<span data-ttu-id="30514-125">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="30514-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="30514-126">Parola</span><span class="sxs-lookup"><span data-stu-id="30514-126">Password</span></span>|<span data-ttu-id="30514-127">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="30514-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30514-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30514-128">Child Elements</span></span>  
 <span data-ttu-id="30514-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="30514-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30514-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30514-130">Parent Elements</span></span>  
  
|<span data-ttu-id="30514-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="30514-131">Element</span></span>|<span data-ttu-id="30514-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30514-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30514-133">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="30514-133">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="30514-134">Bir eş taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30514-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30514-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30514-135">Remarks</span></span>  
 <span data-ttu-id="30514-136">Bu öğe yalnızca [ \<güvenlik >](security-of-peertransport.md) mod özniteliği veya `TransportWithMessageCredential`olarak `Transport` ayarlandıysa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="30514-136">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30514-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30514-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="30514-138">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="30514-138">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="30514-139">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="30514-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="30514-140">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="30514-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="30514-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30514-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="30514-142">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="30514-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="30514-143">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30514-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="30514-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30514-144">\<customBinding></span></span>](custombinding.md)
