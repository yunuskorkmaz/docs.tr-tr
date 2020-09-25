---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 5e3ca9c4a43432d7f5da6d8816b6a2b984851050
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177857"
---
# \<webScriptEndpoint>

<span data-ttu-id="3b18a-101">Bu yapılandırma öğesi [\<webHttpBinding>](webhttpbinding.md) , otomatik olarak davranışını ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<enableWebScript>](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="3b18a-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="3b18a-102">Bir ASP.NET AJAX uygulamasından çağrılan bir hizmet yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b18a-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="3b18a-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b18a-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b18a-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b18a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3b18a-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b18a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b18a-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b18a-106">Attributes</span></span>  
  
|<span data-ttu-id="3b18a-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3b18a-107">Attribute</span></span>|<span data-ttu-id="3b18a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b18a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b18a-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="3b18a-109">webEndpointType</span></span>|<span data-ttu-id="3b18a-110">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3b18a-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b18a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b18a-111">Child Elements</span></span>  

 <span data-ttu-id="3b18a-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3b18a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b18a-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b18a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="3b18a-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b18a-114">Element</span></span>|<span data-ttu-id="3b18a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b18a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="3b18a-116">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3b18a-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b18a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b18a-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
