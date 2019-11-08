---
title: <transport> / <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735980"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="c77b2-102">\<netPeerTcpBinding > \<taşıma ></span><span class="sxs-lookup"><span data-stu-id="c77b2-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="c77b2-103">[\<netPeerTcpBinding >](netpeertcpbinding.md)kullanılırken aktarım düzeyi güvenliği için ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
<span data-ttu-id="c77b2-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c77b2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c77b2-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c77b2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c77b2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c77b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="c77b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="c77b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c77b2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-netpeerbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c77b2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)</span></span>\
<span data-ttu-id="c77b2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<taşıma >**</span><span class="sxs-lookup"><span data-stu-id="c77b2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c77b2-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c77b2-111">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c77b2-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c77b2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c77b2-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="c77b2-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c77b2-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c77b2-114">Attributes</span></span>  
  
|<span data-ttu-id="c77b2-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c77b2-115">Attribute</span></span>|<span data-ttu-id="c77b2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c77b2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c77b2-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="c77b2-117">credentialType</span></span>|<span data-ttu-id="c77b2-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c77b2-118">Optional.</span></span> <span data-ttu-id="c77b2-119">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="c77b2-120">Bu öznitelik <xref:System.ServiceModel.PeerTransportCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="c77b2-121">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="c77b2-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="c77b2-122">Değer</span><span class="sxs-lookup"><span data-stu-id="c77b2-122">Value</span></span>|<span data-ttu-id="c77b2-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c77b2-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c77b2-124">Sertifika</span><span class="sxs-lookup"><span data-stu-id="c77b2-124">Certificate</span></span>|<span data-ttu-id="c77b2-125">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="c77b2-126">istemcisiyle yönetilen bir cihaz için)</span><span class="sxs-lookup"><span data-stu-id="c77b2-126">Password</span></span>|<span data-ttu-id="c77b2-127">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c77b2-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c77b2-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c77b2-128">Child Elements</span></span>  
 <span data-ttu-id="c77b2-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="c77b2-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c77b2-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c77b2-130">Parent Elements</span></span>  
  
|<span data-ttu-id="c77b2-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="c77b2-131">Element</span></span>|<span data-ttu-id="c77b2-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c77b2-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c77b2-133">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="c77b2-133">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="c77b2-134">[\<netPeerTcpBinding >](netpeertcpbinding.md)için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c77b2-134">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c77b2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c77b2-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="c77b2-136">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c77b2-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c77b2-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c77b2-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c77b2-138">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c77b2-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c77b2-139">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c77b2-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c77b2-140">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="c77b2-140">\<binding></span></span>](bindings.md)
