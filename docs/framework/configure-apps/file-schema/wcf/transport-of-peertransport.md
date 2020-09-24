---
title: <transport> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 7328d67c4649010dce3e1c866238d1e0067e4990
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157076"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="730fd-102">\<transport> / \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="730fd-102">\<transport> of \<peerTransport></span></span>

<span data-ttu-id="730fd-103">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="730fd-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="730fd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="730fd-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="730fd-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="730fd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="730fd-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="730fd-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="730fd-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="730fd-107">Attributes</span></span>  
  
|<span data-ttu-id="730fd-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="730fd-108">Attribute</span></span>|<span data-ttu-id="730fd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730fd-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="730fd-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="730fd-110">credentialType</span></span>|<span data-ttu-id="730fd-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="730fd-111">Optional.</span></span> <span data-ttu-id="730fd-112">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="730fd-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="730fd-113">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="730fd-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="730fd-114">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="730fd-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="730fd-115">Değer</span><span class="sxs-lookup"><span data-stu-id="730fd-115">Value</span></span>|<span data-ttu-id="730fd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730fd-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="730fd-117">Sertifika</span><span class="sxs-lookup"><span data-stu-id="730fd-117">Certificate</span></span>|<span data-ttu-id="730fd-118">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="730fd-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="730fd-119">Parola</span><span class="sxs-lookup"><span data-stu-id="730fd-119">Password</span></span>|<span data-ttu-id="730fd-120">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="730fd-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="730fd-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="730fd-121">Child Elements</span></span>  

 <span data-ttu-id="730fd-122">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="730fd-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="730fd-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="730fd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="730fd-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="730fd-124">Element</span></span>|<span data-ttu-id="730fd-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730fd-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="730fd-126">Bir eş taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="730fd-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="730fd-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="730fd-127">Remarks</span></span>  

 <span data-ttu-id="730fd-128">Bu öğe yalnızca mode özniteliği [\<security>](security-of-peertransport.md) veya olarak ayarlandıysa ayarlanır `Transport` `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="730fd-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730fd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="730fd-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="730fd-130">Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="730fd-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="730fd-131">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="730fd-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="730fd-132">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="730fd-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="730fd-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="730fd-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="730fd-134">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="730fd-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="730fd-135">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="730fd-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
