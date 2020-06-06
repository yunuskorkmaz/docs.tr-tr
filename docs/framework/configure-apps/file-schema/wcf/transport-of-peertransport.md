---
title: <transport> / <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399296"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="edc0b-102">\<transport> / \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="edc0b-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="edc0b-103">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="edc0b-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="edc0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edc0b-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edc0b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="edc0b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="edc0b-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="edc0b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edc0b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="edc0b-107">Attributes</span></span>  
  
|<span data-ttu-id="edc0b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="edc0b-108">Attribute</span></span>|<span data-ttu-id="edc0b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edc0b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="edc0b-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="edc0b-110">credentialType</span></span>|<span data-ttu-id="edc0b-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="edc0b-111">Optional.</span></span> <span data-ttu-id="edc0b-112">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="edc0b-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="edc0b-113">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="edc0b-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="edc0b-114">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="edc0b-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="edc0b-115">Değer</span><span class="sxs-lookup"><span data-stu-id="edc0b-115">Value</span></span>|<span data-ttu-id="edc0b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edc0b-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="edc0b-117">Sertifika</span><span class="sxs-lookup"><span data-stu-id="edc0b-117">Certificate</span></span>|<span data-ttu-id="edc0b-118">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="edc0b-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="edc0b-119">Parola</span><span class="sxs-lookup"><span data-stu-id="edc0b-119">Password</span></span>|<span data-ttu-id="edc0b-120">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="edc0b-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edc0b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="edc0b-121">Child Elements</span></span>  
 <span data-ttu-id="edc0b-122">Yok</span><span class="sxs-lookup"><span data-stu-id="edc0b-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="edc0b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="edc0b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="edc0b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="edc0b-124">Element</span></span>|<span data-ttu-id="edc0b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edc0b-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="edc0b-126">Bir eş taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="edc0b-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edc0b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edc0b-127">Remarks</span></span>  
 <span data-ttu-id="edc0b-128">Bu öğe yalnızca mode özniteliği [\<security>](security-of-peertransport.md) veya olarak ayarlandıysa ayarlanır `Transport` `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="edc0b-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc0b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edc0b-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="edc0b-130">Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="edc0b-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="edc0b-131">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="edc0b-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="edc0b-132">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="edc0b-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="edc0b-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="edc0b-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="edc0b-134">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="edc0b-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="edc0b-135">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="edc0b-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
