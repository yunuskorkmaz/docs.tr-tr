---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855176"
---
# <a name="headers"></a><span data-ttu-id="407f3-101">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="407f3-101">\<headers></span></span>
<span data-ttu-id="407f3-102">Bir uç nokta, temel URI 'sine ek olarak bir veya daha fazla SOAP üst bilgisi tarafından çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="407f3-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="407f3-103">Bu çok sayıda senaryo kümesi, bir uç noktanın, bu uç noktanın istemcilerine, aracıların hedeflediği SOAP üstbilgilerini içermesini gerektiren bir dizi SOAP aracı senaryolarından biridir.</span><span class="sxs-lookup"><span data-stu-id="407f3-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="407f3-104">Bu yapılandırma öğesi, bu tür özel adres üstbilgilerini tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="407f3-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="407f3-105">Uç nokta üst bilgi koleksiyonundaki girişler Kullanıcı tanımlı XML öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="407f3-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="407f3-106">Her öğe iyi biçimlendirilmiş XML olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="407f3-106">Each element has to be well-formed XML.</span></span>  
  
<span data-ttu-id="407f3-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="407f3-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="407f3-108">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="407f3-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="407f3-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="407f3-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="407f3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<uç nokta >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="407f3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="407f3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<üst bilgiler >**</span><span class="sxs-lookup"><span data-stu-id="407f3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407f3-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="407f3-112">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="407f3-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="407f3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="407f3-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="407f3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="407f3-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="407f3-115">Attributes</span></span>  
 <span data-ttu-id="407f3-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="407f3-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="407f3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="407f3-117">Child Elements</span></span>  
 <span data-ttu-id="407f3-118">Kullanıcı tanımlı XML öğeleri.</span><span class="sxs-lookup"><span data-stu-id="407f3-118">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="407f3-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="407f3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="407f3-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="407f3-120">Element</span></span>|<span data-ttu-id="407f3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="407f3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="407f3-122">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="407f3-122">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="407f3-123">Farklı uç nokta türlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="407f3-123">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="407f3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="407f3-124">Remarks</span></span>  
 <span data-ttu-id="407f3-125">İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya ile etkileşimde bulunmak için daha ayrıntılı adresleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="407f3-125">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="407f3-126">Örneğin, üst bilgilerin bir yanıt iletisi gönderebilmesi veya birden çok örnek kullanılabilir olduğunda belirli bir kullanıcıdan gelen bir iletiyi işlemek için kullanılacak bir hizmet örneği olan gelen bir iletiyi nasıl işleyeceğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="407f3-126">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407f3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="407f3-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="407f3-128">Noktalarının Adresler, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="407f3-128">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
