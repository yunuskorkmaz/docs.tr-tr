---
description: 'Hakkında daha fazla bilgi <transport> edinin: <netPeerTcpBinding>'
title: <transport> / <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: e93885234577e4f3c7a99be66e4798d33ffb5893
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664580"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="dbb5a-103">\<transport> / \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="dbb5a-103">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="dbb5a-104">Kullanırken aktarım düzeyi güvenliği için ayarları belirtir [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dbb5a-104">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="dbb5a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dbb5a-105">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbb5a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbb5a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dbb5a-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="dbb5a-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbb5a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbb5a-108">Attributes</span></span>  
  
|<span data-ttu-id="dbb5a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbb5a-109">Attribute</span></span>|<span data-ttu-id="dbb5a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbb5a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbb5a-111">credentialType</span><span class="sxs-lookup"><span data-stu-id="dbb5a-111">credentialType</span></span>|<span data-ttu-id="dbb5a-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dbb5a-112">Optional.</span></span> <span data-ttu-id="dbb5a-113">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbb5a-113">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="dbb5a-114">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="dbb5a-114">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="dbb5a-115">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="dbb5a-115">credentialType Attribute</span></span>  
  
|<span data-ttu-id="dbb5a-116">Değer</span><span class="sxs-lookup"><span data-stu-id="dbb5a-116">Value</span></span>|<span data-ttu-id="dbb5a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbb5a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbb5a-118">Sertifika</span><span class="sxs-lookup"><span data-stu-id="dbb5a-118">Certificate</span></span>|<span data-ttu-id="dbb5a-119">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dbb5a-119">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="dbb5a-120">Parola</span><span class="sxs-lookup"><span data-stu-id="dbb5a-120">Password</span></span>|<span data-ttu-id="dbb5a-121">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dbb5a-121">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbb5a-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbb5a-122">Child Elements</span></span>  

 <span data-ttu-id="dbb5a-123">Yok</span><span class="sxs-lookup"><span data-stu-id="dbb5a-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbb5a-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbb5a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dbb5a-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbb5a-125">Element</span></span>|<span data-ttu-id="dbb5a-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbb5a-126">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="dbb5a-127">İçin güvenlik ayarlarını tanımlar [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dbb5a-127">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbb5a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbb5a-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="dbb5a-129">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dbb5a-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dbb5a-130">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="dbb5a-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dbb5a-131">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dbb5a-131">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dbb5a-132">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="dbb5a-132">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
