---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 347a08a35ff898ab7037c11d3c87fda73c3ab2ab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178119"
---
# \<headers>

<span data-ttu-id="905cd-101">Bir uç nokta, temel URI 'sine ek olarak bir veya daha fazla SOAP üst bilgisi tarafından çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="905cd-101">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="905cd-102">Bu çok sayıda senaryo kümesi, bir uç noktanın, bu uç noktanın istemcilerine, aracıların hedeflediği SOAP üstbilgilerini içermesini gerektiren bir dizi SOAP aracı senaryolarından biridir.</span><span class="sxs-lookup"><span data-stu-id="905cd-102">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="905cd-103">Bu yapılandırma öğesi, bu tür özel adres üstbilgilerini tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="905cd-103">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="905cd-104">Uç nokta üst bilgi koleksiyonundaki girişler Kullanıcı tanımlı XML öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="905cd-104">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="905cd-105">Her öğe iyi biçimlendirilmiş XML olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="905cd-105">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="905cd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="905cd-106">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="905cd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="905cd-107">Attributes and Elements</span></span>  

 <span data-ttu-id="905cd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="905cd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="905cd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="905cd-109">Attributes</span></span>  

 <span data-ttu-id="905cd-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="905cd-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="905cd-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="905cd-111">Child Elements</span></span>  

 <span data-ttu-id="905cd-112">Kullanıcı tanımlı XML öğeleri.</span><span class="sxs-lookup"><span data-stu-id="905cd-112">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="905cd-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="905cd-113">Parent Elements</span></span>  
  
|<span data-ttu-id="905cd-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="905cd-114">Element</span></span>|<span data-ttu-id="905cd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="905cd-115">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="905cd-116">Farklı uç nokta türlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="905cd-116">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="905cd-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="905cd-117">Remarks</span></span>  

 <span data-ttu-id="905cd-118">İsteğe bağlı üstbilgiler, uç noktayı tanımlamak veya ile etkileşimde bulunmak için daha ayrıntılı adresleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="905cd-118">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="905cd-119">Örneğin, üst bilgilerin bir yanıt iletisi gönderebilmesi veya birden çok örnek kullanılabilir olduğunda belirli bir kullanıcıdan gelen bir iletiyi işlemek için kullanılacak bir hizmet örneği olan gelen bir iletiyi nasıl işleyeceğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="905cd-119">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905cd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="905cd-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="905cd-121">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="905cd-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
