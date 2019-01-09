---
title: '&lt;Üst bilgileri&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 84b9a9437d4b0dfae72a6e625b21f2b830eb28d8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147869"
---
# <a name="ltheadersgt"></a><span data-ttu-id="540c1-102">&lt;Üst bilgileri&gt;</span><span class="sxs-lookup"><span data-stu-id="540c1-102">&lt;headers&gt;</span></span>
<span data-ttu-id="540c1-103">Bir uç nokta temel URI'sini ek olarak bir veya daha fazla SOAP üstbilgileri çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="540c1-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="540c1-104">Bu faydalı olduğu senaryolar bir kümesi, burada aracıların hedeflenen SOAP başlıkları da eklediğinizden istemcilerin bu uç noktanın bir uç nokta gerektiriyor SOAP Ara senaryoları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="540c1-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="540c1-105">Bu yapılandırma öğesi, bu tür özel adres üstbilgileri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="540c1-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="540c1-106">Giriş uç noktası üst bilgisi koleksiyonu kullanıcı tarafından tanımlanan XML öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="540c1-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="540c1-107">Her öğenin biçimlendirilmiş olması gerekir XML.</span><span class="sxs-lookup"><span data-stu-id="540c1-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="540c1-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="540c1-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="540c1-109">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="540c1-109">\<client></span></span>  
<span data-ttu-id="540c1-110">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="540c1-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="540c1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="540c1-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="540c1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="540c1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="540c1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="540c1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="540c1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="540c1-114">Attributes</span></span>  
 <span data-ttu-id="540c1-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="540c1-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="540c1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="540c1-116">Child Elements</span></span>  
  
|<span data-ttu-id="540c1-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="540c1-117">Element</span></span>|<span data-ttu-id="540c1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="540c1-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="540c1-119">Bölge</span><span class="sxs-lookup"><span data-stu-id="540c1-119">Region</span></span>||  
|<span data-ttu-id="540c1-120">Üye</span><span class="sxs-lookup"><span data-stu-id="540c1-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="540c1-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="540c1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="540c1-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="540c1-122">Element</span></span>|<span data-ttu-id="540c1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="540c1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="540c1-124">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="540c1-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="540c1-125">Farklı uç noktalar için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="540c1-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="540c1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="540c1-126">Remarks</span></span>  
 <span data-ttu-id="540c1-127">İsteğe bağlı üst bilgileri tanımlamak veya uç nokta ile etkileşime geçmek için adresleme daha ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="540c1-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="540c1-128">Örneğin, gelen iletileri işlemek nasıl, nerede uç nokta bir yanıt iletisi göndermelidir veya birden fazla örneği bulunduğunda, belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin üst bilgileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="540c1-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540c1-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="540c1-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="540c1-130">Uç noktalar: Adresleri, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="540c1-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
