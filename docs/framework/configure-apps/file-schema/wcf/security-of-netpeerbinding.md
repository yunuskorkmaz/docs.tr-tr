---
description: 'Hakkında daha fazla bilgi <security> edinin: <netPeerBinding>'
title: <security> / <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: f67cfa445a5a605b99783cfd67dd1bae6e17b51e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786843"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="d2b04-103">\<security> / \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="d2b04-103">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="d2b04-104">[\<netPeerTcpBinding>](netpeertcpbinding.md)Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik gibi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b04-104">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="d2b04-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2b04-105">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2b04-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2b04-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d2b04-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="d2b04-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2b04-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2b04-108">Attributes</span></span>  
  
|<span data-ttu-id="d2b04-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d2b04-109">Attribute</span></span>|<span data-ttu-id="d2b04-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2b04-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2b04-111">mod</span><span class="sxs-lookup"><span data-stu-id="d2b04-111">mode</span></span>|<span data-ttu-id="d2b04-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d2b04-112">Optional.</span></span> <span data-ttu-id="d2b04-113">Bu bağlama ile yapılandırılan eşler tarafından kullanılan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2b04-113">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="d2b04-114">`Message` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d2b04-114">The default value is `Message`.</span></span> <span data-ttu-id="d2b04-115">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="d2b04-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d2b04-116">mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="d2b04-116">mode Attribute</span></span>  
  
|<span data-ttu-id="d2b04-117">Değer</span><span class="sxs-lookup"><span data-stu-id="d2b04-117">Value</span></span>|<span data-ttu-id="d2b04-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2b04-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d2b04-119">İleti</span><span class="sxs-lookup"><span data-stu-id="d2b04-119">Message</span></span>|<span data-ttu-id="d2b04-120">SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b04-120">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="d2b04-121">Yok</span><span class="sxs-lookup"><span data-stu-id="d2b04-121">None</span></span>|<span data-ttu-id="d2b04-122">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d2b04-122">Security is disabled.</span></span>|  
|<span data-ttu-id="d2b04-123">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d2b04-123">Transport</span></span>|<span data-ttu-id="d2b04-124">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d2b04-124">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="d2b04-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d2b04-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="d2b04-126">HTTPS kimlik doğrulaması ve gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b04-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="d2b04-127">SOAP iletileri zengin kimlik bilgisi türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b04-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2b04-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2b04-128">Child Elements</span></span>  
  
|<span data-ttu-id="d2b04-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2b04-129">Element</span></span>|<span data-ttu-id="d2b04-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2b04-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="d2b04-131">Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2b04-131">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="d2b04-132">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="d2b04-132">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2b04-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2b04-133">Parent Elements</span></span>  
  
|<span data-ttu-id="d2b04-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2b04-134">Element</span></span>|<span data-ttu-id="d2b04-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2b04-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d2b04-136">Öğesinin tüm bağlama yeteneklerini tanımlar [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d2b04-136">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2b04-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2b04-137">Remarks</span></span>  

 <span data-ttu-id="d2b04-138">Güvenlik, ileti ya da aktarım özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2b04-138">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2b04-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2b04-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="d2b04-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d2b04-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d2b04-141">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="d2b04-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d2b04-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d2b04-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d2b04-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d2b04-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d2b04-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2b04-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
