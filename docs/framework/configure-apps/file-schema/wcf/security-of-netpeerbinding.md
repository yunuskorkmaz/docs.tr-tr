---
title: <security> / <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 543c57d6b2dba1ff5934b49e0e219cf2e5cad153
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170031"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="c65e5-102">\<security> / \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="c65e5-102">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="c65e5-103">[\<netPeerTcpBinding>](netpeertcpbinding.md)Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c65e5-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="c65e5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c65e5-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c65e5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c65e5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c65e5-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c65e5-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c65e5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c65e5-107">Attributes</span></span>  
  
|<span data-ttu-id="c65e5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c65e5-108">Attribute</span></span>|<span data-ttu-id="c65e5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c65e5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c65e5-110">mod</span><span class="sxs-lookup"><span data-stu-id="c65e5-110">mode</span></span>|<span data-ttu-id="c65e5-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c65e5-111">Optional.</span></span> <span data-ttu-id="c65e5-112">Bu bağlama ile yapılandırılan eşler tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c65e5-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="c65e5-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="c65e5-113">The default value is `Message`.</span></span> <span data-ttu-id="c65e5-114">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="c65e5-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c65e5-115">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="c65e5-115">mode Attribute</span></span>  
  
|<span data-ttu-id="c65e5-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c65e5-116">Value</span></span>|<span data-ttu-id="c65e5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c65e5-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c65e5-118">İleti</span><span class="sxs-lookup"><span data-stu-id="c65e5-118">Message</span></span>|<span data-ttu-id="c65e5-119">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c65e5-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="c65e5-120">Yok</span><span class="sxs-lookup"><span data-stu-id="c65e5-120">None</span></span>|<span data-ttu-id="c65e5-121">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c65e5-121">Security is disabled.</span></span>|  
|<span data-ttu-id="c65e5-122">Aktarım</span><span class="sxs-lookup"><span data-stu-id="c65e5-122">Transport</span></span>|<span data-ttu-id="c65e5-123">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c65e5-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="c65e5-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c65e5-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="c65e5-125">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c65e5-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="c65e5-126">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c65e5-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c65e5-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c65e5-127">Child Elements</span></span>  
  
|<span data-ttu-id="c65e5-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="c65e5-128">Element</span></span>|<span data-ttu-id="c65e5-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c65e5-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="c65e5-130">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c65e5-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="c65e5-131">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="c65e5-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c65e5-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c65e5-132">Parent Elements</span></span>  
  
|<span data-ttu-id="c65e5-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="c65e5-133">Element</span></span>|<span data-ttu-id="c65e5-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c65e5-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c65e5-135">Öğesinin tüm bağlama yeteneklerini tanımlar [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c65e5-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c65e5-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c65e5-136">Remarks</span></span>  

 <span data-ttu-id="c65e5-137">Güvenlik, ileti ya da aktarım özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="c65e5-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65e5-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c65e5-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="c65e5-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c65e5-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c65e5-140">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="c65e5-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c65e5-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c65e5-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c65e5-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c65e5-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c65e5-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c65e5-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
