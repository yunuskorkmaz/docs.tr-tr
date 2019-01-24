---
title: '&lt;Üst bilgileri&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: f47462ba63b9bd8868420ee9d3a320ba18c83c65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557831"
---
# <a name="ltheadersgt"></a><span data-ttu-id="67e78-102">&lt;Üst bilgileri&gt;</span><span class="sxs-lookup"><span data-stu-id="67e78-102">&lt;headers&gt;</span></span>
<span data-ttu-id="67e78-103">Bir uç nokta temel URI'sini ek olarak bir veya daha fazla SOAP üstbilgileri çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="67e78-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="67e78-104">Bu faydalı olduğu senaryolar bir kümesi, burada aracıların hedeflenen SOAP başlıkları da eklediğinizden istemcilerin bu uç noktanın bir uç nokta gerektiriyor SOAP Ara senaryoları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="67e78-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="67e78-105">Bu yapılandırma öğesi, bu tür özel adres üstbilgileri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67e78-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="67e78-106">Giriş uç noktası üst bilgisi koleksiyonu kullanıcı tarafından tanımlanan XML öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="67e78-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="67e78-107">Her öğenin biçimlendirilmiş olması gerekir XML.</span><span class="sxs-lookup"><span data-stu-id="67e78-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="67e78-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="67e78-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="67e78-109">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="67e78-109">\<client></span></span>  
<span data-ttu-id="67e78-110">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="67e78-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e78-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67e78-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67e78-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="67e78-112">Attributes and Elements</span></span>  
 <span data-ttu-id="67e78-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67e78-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67e78-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="67e78-114">Attributes</span></span>  
 <span data-ttu-id="67e78-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="67e78-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67e78-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="67e78-116">Child Elements</span></span>  
 <span data-ttu-id="67e78-117">Kullanıcı tanımlı XML öğeleri.</span><span class="sxs-lookup"><span data-stu-id="67e78-117">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67e78-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="67e78-118">Parent Elements</span></span>  
  
|<span data-ttu-id="67e78-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="67e78-119">Element</span></span>|<span data-ttu-id="67e78-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67e78-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67e78-121">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="67e78-121">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="67e78-122">Farklı uç noktalar için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="67e78-122">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67e78-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67e78-123">Remarks</span></span>  
 <span data-ttu-id="67e78-124">İsteğe bağlı üst bilgileri tanımlamak veya uç nokta ile etkileşime geçmek için adresleme daha ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67e78-124">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="67e78-125">Örneğin, gelen iletileri işlemek nasıl, nerede uç nokta bir yanıt iletisi göndermelidir veya birden fazla örneği bulunduğunda, belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin üst bilgileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="67e78-125">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e78-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e78-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="67e78-127">Uç noktalar: Adresleri, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="67e78-127">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
