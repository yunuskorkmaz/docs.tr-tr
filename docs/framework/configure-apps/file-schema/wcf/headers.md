---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: a982fa87ab84725e36ee913f00200cd34f0b8f6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925569"
---
# <a name="headers"></a><span data-ttu-id="f0463-101">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="f0463-101">\<headers></span></span>
<span data-ttu-id="f0463-102">Bir uç nokta, temel URI 'sine ek olarak bir veya daha fazla SOAP üst bilgisi tarafından çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="f0463-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="f0463-103">Bu çok sayıda senaryo kümesi, bir uç noktanın, bu uç noktanın istemcilerine, aracıların hedeflediği SOAP üstbilgilerini içermesini gerektiren bir dizi SOAP aracı senaryolarından biridir.</span><span class="sxs-lookup"><span data-stu-id="f0463-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="f0463-104">Bu yapılandırma öğesi, bu tür özel adres üstbilgilerini tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0463-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="f0463-105">Uç nokta üst bilgi koleksiyonundaki girişler Kullanıcı tanımlı XML öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="f0463-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="f0463-106">Her öğe iyi biçimlendirilmiş XML olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0463-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="f0463-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f0463-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="f0463-108">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="f0463-108">\<client></span></span>  
<span data-ttu-id="f0463-109">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="f0463-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0463-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0463-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0463-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0463-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f0463-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0463-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0463-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0463-113">Attributes</span></span>  
 <span data-ttu-id="f0463-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f0463-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f0463-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0463-115">Child Elements</span></span>  
 <span data-ttu-id="f0463-116">Kullanıcı tanımlı XML öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f0463-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0463-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0463-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f0463-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0463-118">Element</span></span>|<span data-ttu-id="f0463-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0463-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0463-120">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="f0463-120">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="f0463-121">Farklı uç nokta türlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f0463-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0463-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0463-122">Remarks</span></span>  
 <span data-ttu-id="f0463-123">İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya ile etkileşimde bulunmak için daha ayrıntılı adresleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0463-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="f0463-124">Örneğin, üst bilgilerin bir yanıt iletisi gönderebilmesi veya birden çok örnek kullanılabilir olduğunda belirli bir kullanıcıdan gelen bir iletiyi işlemek için kullanılacak bir hizmet örneği olan gelen bir iletiyi nasıl işleyeceğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="f0463-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0463-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0463-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="f0463-126">Noktalarının Adresler, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="f0463-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
