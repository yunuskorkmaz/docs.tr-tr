---
title: '&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 2b89ae090d24ff6aad1aae1b39a0a18961bd2537
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181004"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="744bc-102">&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="744bc-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="744bc-103">Kullanırken aktarım düzeyi güvenlik ayarlarını belirtir [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="744bc-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="744bc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="744bc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="744bc-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="744bc-105">\<bindings></span></span>  
<span data-ttu-id="744bc-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="744bc-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="744bc-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="744bc-107">\<binding></span></span>  
<span data-ttu-id="744bc-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="744bc-108">\<security></span></span>  
<span data-ttu-id="744bc-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="744bc-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744bc-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="744bc-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="744bc-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="744bc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="744bc-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="744bc-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="744bc-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="744bc-113">Attributes</span></span>  
  
|<span data-ttu-id="744bc-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="744bc-114">Attribute</span></span>|<span data-ttu-id="744bc-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="744bc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="744bc-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="744bc-116">credentialType</span></span>|<span data-ttu-id="744bc-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="744bc-117">Optional.</span></span> <span data-ttu-id="744bc-118">Eş ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="744bc-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="744bc-119">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="744bc-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="744bc-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="744bc-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="744bc-121">Değer</span><span class="sxs-lookup"><span data-stu-id="744bc-121">Value</span></span>|<span data-ttu-id="744bc-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="744bc-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="744bc-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="744bc-123">Certificate</span></span>|<span data-ttu-id="744bc-124">Eş kanal kimlik doğrulaması gerektiren x X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="744bc-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="744bc-125">Parola</span><span class="sxs-lookup"><span data-stu-id="744bc-125">Password</span></span>|<span data-ttu-id="744bc-126">Eş kanal kimlik doğrulaması için doğru parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="744bc-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="744bc-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="744bc-127">Child Elements</span></span>  
 <span data-ttu-id="744bc-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="744bc-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="744bc-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="744bc-129">Parent Elements</span></span>  
  
|<span data-ttu-id="744bc-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="744bc-130">Element</span></span>|<span data-ttu-id="744bc-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="744bc-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="744bc-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="744bc-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="744bc-133">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="744bc-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="744bc-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="744bc-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="744bc-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="744bc-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="744bc-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="744bc-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="744bc-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="744bc-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="744bc-138">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="744bc-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="744bc-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="744bc-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
