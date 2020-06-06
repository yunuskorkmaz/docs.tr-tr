---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854807"
---
# \<webScriptEndpoint>
<span data-ttu-id="0a1d1-101">Bu yapılandırma öğesi [\<webHttpBinding>](webhttpbinding.md) , otomatik olarak davranışını ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<enableWebScript>](enablewebscript.md) .</span><span class="sxs-lookup"><span data-stu-id="0a1d1-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="0a1d1-102">Bir ASP.NET AJAX uygulamasından çağrılan bir hizmet yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a1d1-102">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0a1d1-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a1d1-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a1d1-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a1d1-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0a1d1-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0a1d1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a1d1-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0a1d1-106">Attributes</span></span>  
  
|<span data-ttu-id="0a1d1-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0a1d1-107">Attribute</span></span>|<span data-ttu-id="0a1d1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a1d1-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a1d1-109">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="0a1d1-109">webEndpointType</span></span>|<span data-ttu-id="0a1d1-110">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="0a1d1-110">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a1d1-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a1d1-111">Child Elements</span></span>  
 <span data-ttu-id="0a1d1-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="0a1d1-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a1d1-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a1d1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0a1d1-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a1d1-114">Element</span></span>|<span data-ttu-id="0a1d1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a1d1-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0a1d1-116">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0a1d1-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a1d1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a1d1-117">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
