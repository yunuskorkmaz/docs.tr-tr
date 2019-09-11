---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854807"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="949ac-101">\<webScriptEndpoint ></span><span class="sxs-lookup"><span data-stu-id="949ac-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="949ac-102">Bu yapılandırma öğesi [ ,\<enablewebscript >](enablewebscript.md) davranışını otomatik olarak ekleyen bir fixed [ \<WebHttpBinding >](webhttpbinding.md) bağlaması olan bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="949ac-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="949ac-103">Bir ASP.NET AJAX uygulamasından çağrılan bir hizmet yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="949ac-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="949ac-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="949ac-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="949ac-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="949ac-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="949ac-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="949ac-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="949ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webScriptEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="949ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949ac-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="949ac-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="949ac-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="949ac-109">Attributes and Elements</span></span>  
 <span data-ttu-id="949ac-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="949ac-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="949ac-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="949ac-111">Attributes</span></span>  
  
|<span data-ttu-id="949ac-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="949ac-112">Attribute</span></span>|<span data-ttu-id="949ac-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="949ac-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="949ac-114">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="949ac-114">webEndpointType</span></span>|<span data-ttu-id="949ac-115">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="949ac-115">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="949ac-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="949ac-116">Child Elements</span></span>  
 <span data-ttu-id="949ac-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="949ac-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="949ac-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="949ac-118">Parent Elements</span></span>  
  
|<span data-ttu-id="949ac-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="949ac-119">Element</span></span>|<span data-ttu-id="949ac-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="949ac-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="949ac-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="949ac-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="949ac-122">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="949ac-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="949ac-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="949ac-123">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
