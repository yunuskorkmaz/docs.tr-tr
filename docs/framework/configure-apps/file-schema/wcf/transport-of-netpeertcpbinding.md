---
title: <transport> / <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 837d01540fa63579877ab4085bd8034c78f2fbe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915570"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="ea133-102">\<\<NetPeerTcpBinding > taşıma ></span><span class="sxs-lookup"><span data-stu-id="ea133-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="ea133-103">[ \<NetPeerTcpBinding >](netpeertcpbinding.md)kullanılırken aktarım düzeyi güvenliği için ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea133-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="ea133-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ea133-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ea133-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ea133-105">\<bindings></span></span>  
<span data-ttu-id="ea133-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="ea133-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="ea133-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ea133-107">\<binding></span></span>  
<span data-ttu-id="ea133-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ea133-108">\<security></span></span>  
<span data-ttu-id="ea133-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="ea133-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea133-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea133-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea133-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea133-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ea133-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="ea133-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea133-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea133-113">Attributes</span></span>  
  
|<span data-ttu-id="ea133-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea133-114">Attribute</span></span>|<span data-ttu-id="ea133-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea133-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea133-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="ea133-116">credentialType</span></span>|<span data-ttu-id="ea133-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ea133-117">Optional.</span></span> <span data-ttu-id="ea133-118">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea133-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="ea133-119">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ea133-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="ea133-120">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="ea133-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="ea133-121">Değer</span><span class="sxs-lookup"><span data-stu-id="ea133-121">Value</span></span>|<span data-ttu-id="ea133-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea133-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ea133-123">Sertifika</span><span class="sxs-lookup"><span data-stu-id="ea133-123">Certificate</span></span>|<span data-ttu-id="ea133-124">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ea133-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="ea133-125">Parola</span><span class="sxs-lookup"><span data-stu-id="ea133-125">Password</span></span>|<span data-ttu-id="ea133-126">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ea133-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea133-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea133-127">Child Elements</span></span>  
 <span data-ttu-id="ea133-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="ea133-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea133-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea133-129">Parent Elements</span></span>  
  
|<span data-ttu-id="ea133-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea133-130">Element</span></span>|<span data-ttu-id="ea133-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea133-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea133-132">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ea133-132">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="ea133-133">[ \<NetPeerTcpBinding >](netpeertcpbinding.md)için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ea133-133">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea133-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea133-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="ea133-135">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ea133-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ea133-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ea133-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ea133-137">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ea133-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ea133-138">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ea133-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ea133-139">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ea133-139">\<binding></span></span>](../../../misc/binding.md)
