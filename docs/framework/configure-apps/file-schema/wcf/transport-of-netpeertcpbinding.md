---
title: <transport> / <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 157637615abafbd5913e4d90b702bb0224d5f121
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204880"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="7c775-102">\<Aktarım >, \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="7c775-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="7c775-103">Kullanırken aktarım düzeyi güvenlik ayarlarını belirtir [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7c775-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="7c775-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7c775-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7c775-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="7c775-105">\<bindings></span></span>  
<span data-ttu-id="7c775-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="7c775-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="7c775-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7c775-107">\<binding></span></span>  
<span data-ttu-id="7c775-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7c775-108">\<security></span></span>  
<span data-ttu-id="7c775-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="7c775-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c775-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c775-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c775-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c775-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7c775-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c775-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c775-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7c775-113">Attributes</span></span>  
  
|<span data-ttu-id="7c775-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7c775-114">Attribute</span></span>|<span data-ttu-id="7c775-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c775-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c775-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="7c775-116">credentialType</span></span>|<span data-ttu-id="7c775-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7c775-117">Optional.</span></span> <span data-ttu-id="7c775-118">Eş ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c775-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="7c775-119">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7c775-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="7c775-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="7c775-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="7c775-121">Değer</span><span class="sxs-lookup"><span data-stu-id="7c775-121">Value</span></span>|<span data-ttu-id="7c775-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c775-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c775-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="7c775-123">Certificate</span></span>|<span data-ttu-id="7c775-124">Eş kanal kimlik doğrulaması gerektiren x X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="7c775-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="7c775-125">Parola</span><span class="sxs-lookup"><span data-stu-id="7c775-125">Password</span></span>|<span data-ttu-id="7c775-126">Eş kanal kimlik doğrulaması için doğru parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7c775-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c775-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c775-127">Child Elements</span></span>  
 <span data-ttu-id="7c775-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="7c775-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c775-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7c775-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7c775-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="7c775-130">Element</span></span>|<span data-ttu-id="7c775-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c775-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c775-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7c775-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="7c775-133">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7c775-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c775-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c775-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="7c775-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7c775-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7c775-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7c775-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7c775-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7c775-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7c775-138">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7c775-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7c775-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7c775-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
