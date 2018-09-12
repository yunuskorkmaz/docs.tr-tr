---
title: '&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 2b89ae090d24ff6aad1aae1b39a0a18961bd2537
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44704559"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="30245-102">&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="30245-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="30245-103">Kullanırken aktarım düzeyi güvenlik ayarlarını belirtir [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="30245-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="30245-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="30245-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="30245-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="30245-105">\<bindings></span></span>  
<span data-ttu-id="30245-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="30245-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="30245-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30245-107">\<binding></span></span>  
<span data-ttu-id="30245-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="30245-108">\<security></span></span>  
<span data-ttu-id="30245-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="30245-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30245-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30245-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30245-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="30245-111">Attributes and Elements</span></span>  
 <span data-ttu-id="30245-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30245-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30245-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30245-113">Attributes</span></span>  
  
|<span data-ttu-id="30245-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="30245-114">Attribute</span></span>|<span data-ttu-id="30245-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30245-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30245-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="30245-116">credentialType</span></span>|<span data-ttu-id="30245-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="30245-117">Optional.</span></span> <span data-ttu-id="30245-118">Eş ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="30245-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="30245-119">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="30245-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="30245-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="30245-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="30245-121">Değer</span><span class="sxs-lookup"><span data-stu-id="30245-121">Value</span></span>|<span data-ttu-id="30245-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30245-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="30245-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="30245-123">Certificate</span></span>|<span data-ttu-id="30245-124">Eş kanal kimlik doğrulaması gerektiren x X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="30245-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="30245-125">Parola</span><span class="sxs-lookup"><span data-stu-id="30245-125">Password</span></span>|<span data-ttu-id="30245-126">Eş kanal kimlik doğrulaması için doğru parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30245-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30245-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="30245-127">Child Elements</span></span>  
 <span data-ttu-id="30245-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="30245-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30245-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="30245-129">Parent Elements</span></span>  
  
|<span data-ttu-id="30245-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="30245-130">Element</span></span>|<span data-ttu-id="30245-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30245-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30245-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="30245-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="30245-133">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="30245-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30245-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30245-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="30245-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="30245-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="30245-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="30245-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="30245-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="30245-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="30245-138">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="30245-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="30245-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="30245-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
