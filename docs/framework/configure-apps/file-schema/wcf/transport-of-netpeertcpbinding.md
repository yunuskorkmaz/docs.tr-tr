---
title: <transport> , <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: f5feca232265cbcad7feff78c0c66e3606c8567e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270400"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="4c579-102">\<Aktarım >, \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="4c579-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="4c579-103">Kullanırken aktarım düzeyi güvenlik ayarlarını belirtir [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4c579-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="4c579-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4c579-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4c579-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4c579-105">\<bindings></span></span>  
<span data-ttu-id="4c579-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4c579-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="4c579-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4c579-107">\<binding></span></span>  
<span data-ttu-id="4c579-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4c579-108">\<security></span></span>  
<span data-ttu-id="4c579-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="4c579-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c579-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c579-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c579-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c579-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4c579-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c579-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c579-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4c579-113">Attributes</span></span>  
  
|<span data-ttu-id="4c579-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4c579-114">Attribute</span></span>|<span data-ttu-id="4c579-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c579-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c579-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="4c579-116">credentialType</span></span>|<span data-ttu-id="4c579-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c579-117">Optional.</span></span> <span data-ttu-id="4c579-118">Eş ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c579-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="4c579-119">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="4c579-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="4c579-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="4c579-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="4c579-121">Değer</span><span class="sxs-lookup"><span data-stu-id="4c579-121">Value</span></span>|<span data-ttu-id="4c579-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c579-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c579-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="4c579-123">Certificate</span></span>|<span data-ttu-id="4c579-124">Eş kanal kimlik doğrulaması gerektiren x X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="4c579-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="4c579-125">Parola</span><span class="sxs-lookup"><span data-stu-id="4c579-125">Password</span></span>|<span data-ttu-id="4c579-126">Eş kanal kimlik doğrulaması için doğru parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c579-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c579-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c579-127">Child Elements</span></span>  
 <span data-ttu-id="4c579-128">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="4c579-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c579-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4c579-129">Parent Elements</span></span>  
  
|<span data-ttu-id="4c579-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="4c579-130">Element</span></span>|<span data-ttu-id="4c579-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c579-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c579-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4c579-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="4c579-133">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4c579-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c579-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c579-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="4c579-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4c579-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4c579-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4c579-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4c579-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4c579-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4c579-138">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="4c579-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4c579-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4c579-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
