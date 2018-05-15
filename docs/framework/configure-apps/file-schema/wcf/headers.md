---
title: '&lt;Üstbilgileri&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltheadersgt"></a><span data-ttu-id="e3169-102">&lt;Üstbilgileri&gt;</span><span class="sxs-lookup"><span data-stu-id="e3169-102">&lt;headers&gt;</span></span>
<span data-ttu-id="e3169-103">Bir uç nokta temel URI'sini yanı sıra bir veya daha fazla SOAP üstbilgileri çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="e3169-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="e3169-104">Bu faydalı olduğu senaryolar bir dizi, burada bir uç nokta aracılar hedeflenen SOAP üstbilgileri dahil etmek Bu uç noktanın gerektirir. istemciler SOAP Ara senaryoları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="e3169-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="e3169-105">Bu yapılandırma öğesi, bu tür özel adres üstbilgileri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3169-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="e3169-106">Uç nokta üstbilgi koleksiyonu girişleri, kullanıcı tanımlı XML öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="e3169-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="e3169-107">Doğru biçimlendirilmiş olması her öğeye sahip XML.</span><span class="sxs-lookup"><span data-stu-id="e3169-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="e3169-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3169-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3169-109">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="e3169-109">\<client></span></span>  
<span data-ttu-id="e3169-110">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="e3169-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3169-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3169-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3169-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3169-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e3169-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3169-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3169-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3169-114">Attributes</span></span>  
 <span data-ttu-id="e3169-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3169-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e3169-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3169-116">Child Elements</span></span>  
  
|<span data-ttu-id="e3169-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3169-117">Element</span></span>|<span data-ttu-id="e3169-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3169-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3169-119">Bölge</span><span class="sxs-lookup"><span data-stu-id="e3169-119">Region</span></span>||  
|<span data-ttu-id="e3169-120">Üye</span><span class="sxs-lookup"><span data-stu-id="e3169-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="e3169-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3169-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e3169-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3169-122">Element</span></span>|<span data-ttu-id="e3169-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3169-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3169-124">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="e3169-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="e3169-125">Farklı türde uç noktalar yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e3169-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3169-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3169-126">Remarks</span></span>  
 <span data-ttu-id="e3169-127">İsteğe bağlı üstbilgi tanımlamak veya uç noktasıyla etkileşim için adresleme daha ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3169-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="e3169-128">Örneğin, üstbilgileri gelen iletiyi işlemeye nasıl, burada uç nokta bir yanıt iletisi göndermesi gerekir veya birden çok örneği kullanılamadığında belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="e3169-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3169-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3169-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="e3169-130">Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="e3169-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
