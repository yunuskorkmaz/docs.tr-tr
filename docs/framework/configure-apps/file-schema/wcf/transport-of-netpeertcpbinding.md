---
title: '&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 9793f3ce101129b1eea8202d41104555e2b16536
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149390"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="0a686-102">&lt;netPeerTcpBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="0a686-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="0a686-103">Kullanırken aktarım düzeyi güvenlik ayarlarını belirtir [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0a686-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="0a686-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0a686-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a686-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0a686-105">\<bindings></span></span>  
<span data-ttu-id="0a686-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="0a686-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="0a686-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0a686-107">\<binding></span></span>  
<span data-ttu-id="0a686-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0a686-108">\<security></span></span>  
<span data-ttu-id="0a686-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="0a686-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a686-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a686-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a686-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a686-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0a686-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0a686-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a686-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0a686-113">Attributes</span></span>  
  
|<span data-ttu-id="0a686-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0a686-114">Attribute</span></span>|<span data-ttu-id="0a686-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a686-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a686-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="0a686-116">credentialType</span></span>|<span data-ttu-id="0a686-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0a686-117">Optional.</span></span> <span data-ttu-id="0a686-118">Eş ile gönderilen iletileri doğrulamak için kullanılan kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a686-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="0a686-119">Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="0a686-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="0a686-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="0a686-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="0a686-121">Değer</span><span class="sxs-lookup"><span data-stu-id="0a686-121">Value</span></span>|<span data-ttu-id="0a686-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a686-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a686-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="0a686-123">Certificate</span></span>|<span data-ttu-id="0a686-124">Eş kanal kimlik doğrulaması gerektiren x X509 sertifika.</span><span class="sxs-lookup"><span data-stu-id="0a686-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="0a686-125">Parola</span><span class="sxs-lookup"><span data-stu-id="0a686-125">Password</span></span>|<span data-ttu-id="0a686-126">Eş kanal kimlik doğrulaması için doğru parola gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0a686-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a686-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a686-127">Child Elements</span></span>  
 <span data-ttu-id="0a686-128">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="0a686-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a686-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a686-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0a686-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a686-130">Element</span></span>|<span data-ttu-id="0a686-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a686-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a686-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0a686-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="0a686-133">Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0a686-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a686-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a686-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="0a686-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0a686-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0a686-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0a686-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0a686-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0a686-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0a686-138">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0a686-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="0a686-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0a686-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
