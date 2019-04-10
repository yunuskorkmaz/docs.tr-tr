---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224571"
---
# <a name="headers"></a><span data-ttu-id="70844-101">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="70844-101">\<headers></span></span>
<span data-ttu-id="70844-102">Bir uç nokta temel URI'sini ek olarak bir veya daha fazla SOAP üstbilgileri çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="70844-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="70844-103">Bu faydalı olduğu senaryolar bir kümesi, burada aracıların hedeflenen SOAP başlıkları da eklediğinizden istemcilerin bu uç noktanın bir uç nokta gerektiriyor SOAP Ara senaryoları kümesidir.</span><span class="sxs-lookup"><span data-stu-id="70844-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="70844-104">Bu yapılandırma öğesi, bu tür özel adres üstbilgileri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="70844-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="70844-105">Giriş uç noktası üst bilgisi koleksiyonu kullanıcı tarafından tanımlanan XML öğeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="70844-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="70844-106">Her öğenin biçimlendirilmiş olması gerekir XML.</span><span class="sxs-lookup"><span data-stu-id="70844-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="70844-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="70844-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="70844-108">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="70844-108">\<client></span></span>  
<span data-ttu-id="70844-109">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="70844-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70844-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70844-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70844-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70844-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70844-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70844-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70844-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70844-113">Attributes</span></span>  
 <span data-ttu-id="70844-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="70844-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70844-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70844-115">Child Elements</span></span>  
 <span data-ttu-id="70844-116">Kullanıcı tanımlı XML öğeleri.</span><span class="sxs-lookup"><span data-stu-id="70844-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70844-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70844-117">Parent Elements</span></span>  
  
|<span data-ttu-id="70844-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="70844-118">Element</span></span>|<span data-ttu-id="70844-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70844-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70844-120">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="70844-120">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="70844-121">Farklı uç noktalar için yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="70844-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70844-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70844-122">Remarks</span></span>  
 <span data-ttu-id="70844-123">İsteğe bağlı üst bilgileri tanımlamak veya uç nokta ile etkileşime geçmek için adresleme daha ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="70844-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="70844-124">Örneğin, gelen iletileri işlemek nasıl, nerede uç nokta bir yanıt iletisi göndermelidir veya birden fazla örneği bulunduğunda, belirli bir kullanıcıdan gelen iletiyi işlemek için kullanılacak bir hizmetin hangi örneğinin üst bilgileri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="70844-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70844-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70844-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="70844-126">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="70844-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
