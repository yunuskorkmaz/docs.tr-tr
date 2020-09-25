---
title: <transport> / <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 5df47b1bfc149b524fc9b90eacffa832817f653c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172872"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="85f0b-102">\<transport> / \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="85f0b-102">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="85f0b-103">Kullanırken aktarım düzeyi güvenliği için ayarları belirtir [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="85f0b-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="85f0b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="85f0b-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85f0b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85f0b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="85f0b-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="85f0b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85f0b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85f0b-107">Attributes</span></span>  
  
|<span data-ttu-id="85f0b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="85f0b-108">Attribute</span></span>|<span data-ttu-id="85f0b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85f0b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85f0b-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="85f0b-110">credentialType</span></span>|<span data-ttu-id="85f0b-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="85f0b-111">Optional.</span></span> <span data-ttu-id="85f0b-112">Eş aktarımlarla gönderilen iletileri doğrulamak için kullanılan kimlik bilgilerinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="85f0b-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="85f0b-113">Bu öznitelik türü <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="85f0b-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="85f0b-114">credentialType özniteliği</span><span class="sxs-lookup"><span data-stu-id="85f0b-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="85f0b-115">Değer</span><span class="sxs-lookup"><span data-stu-id="85f0b-115">Value</span></span>|<span data-ttu-id="85f0b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85f0b-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="85f0b-117">Sertifika</span><span class="sxs-lookup"><span data-stu-id="85f0b-117">Certificate</span></span>|<span data-ttu-id="85f0b-118">Eş kanal taşımanın kimlik doğrulaması bir x509 sertifikası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="85f0b-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="85f0b-119">Parola</span><span class="sxs-lookup"><span data-stu-id="85f0b-119">Password</span></span>|<span data-ttu-id="85f0b-120">Eş kanal taşımanın kimlik doğrulaması, doğru bir parola gerektirir.</span><span class="sxs-lookup"><span data-stu-id="85f0b-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85f0b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85f0b-121">Child Elements</span></span>  

 <span data-ttu-id="85f0b-122">Yok</span><span class="sxs-lookup"><span data-stu-id="85f0b-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85f0b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85f0b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="85f0b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="85f0b-124">Element</span></span>|<span data-ttu-id="85f0b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85f0b-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="85f0b-126">İçin güvenlik ayarlarını tanımlar [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="85f0b-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85f0b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85f0b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="85f0b-128">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="85f0b-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="85f0b-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="85f0b-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="85f0b-130">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="85f0b-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="85f0b-131">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="85f0b-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
