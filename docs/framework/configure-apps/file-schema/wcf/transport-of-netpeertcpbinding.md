---
title: <transport> / <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 157637615abafbd5913e4d90b702bb0224d5f121
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788329"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="d2fd2-102">\<Aktarım >, \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="d2fd2-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="d2fd2-103">Kullanırken aktarım düzeyi güvenlik ayarlarını belirtir [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d2fd2-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="d2fd2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2fd2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2fd2-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d2fd2-105">\<bindings></span></span>  
<span data-ttu-id="d2fd2-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="d2fd2-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="d2fd2-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d2fd2-107">\<binding></span></span>  
<span data-ttu-id="d2fd2-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d2fd2-108">\<security></span></span>  
<span data-ttu-id="d2fd2-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="d2fd2-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2fd2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2fd2-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2fd2-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2fd2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2fd2-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2fd2-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2fd2-113">Attributes</span></span>  
  
|<span data-ttu-id="d2fd2-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d2fd2-114">Attribute</span></span>|<span data-ttu-id="d2fd2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2fd2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2fd2-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="d2fd2-116">credentialType</span></span>|<span data-ttu-id="d2fd2-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-117">Optional.</span></span> <span data-ttu-id="d2fd2-118">Eş ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="d2fd2-119">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="d2fd2-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="d2fd2-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="d2fd2-121">Değer</span><span class="sxs-lookup"><span data-stu-id="d2fd2-121">Value</span></span>|<span data-ttu-id="d2fd2-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2fd2-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d2fd2-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="d2fd2-123">Certificate</span></span>|<span data-ttu-id="d2fd2-124">Eş kanal kimlik doğrulaması gerektiren x X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="d2fd2-125">Parola</span><span class="sxs-lookup"><span data-stu-id="d2fd2-125">Password</span></span>|<span data-ttu-id="d2fd2-126">Eş kanal kimlik doğrulaması için doğru parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2fd2-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2fd2-127">Child Elements</span></span>  
 <span data-ttu-id="d2fd2-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2fd2-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2fd2-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d2fd2-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2fd2-130">Element</span></span>|<span data-ttu-id="d2fd2-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2fd2-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2fd2-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d2fd2-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="d2fd2-133">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d2fd2-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2fd2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2fd2-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="d2fd2-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d2fd2-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d2fd2-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d2fd2-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d2fd2-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d2fd2-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d2fd2-138">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2fd2-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d2fd2-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d2fd2-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
