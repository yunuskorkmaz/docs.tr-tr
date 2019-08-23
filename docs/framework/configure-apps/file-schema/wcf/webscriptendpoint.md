---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: cc69029d9830fd12df5a4070f11847fadf4c60bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940413"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="e037f-101">\<webScriptEndpoint ></span><span class="sxs-lookup"><span data-stu-id="e037f-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="e037f-102">Bu yapılandırma öğesi [ ,\<enablewebscript >](enablewebscript.md) davranışını otomatik olarak ekleyen bir fixed [ \<WebHttpBinding >](webhttpbinding.md) bağlaması olan bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e037f-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="e037f-103">Bir ASP.NET AJAX uygulamasından çağrılan bir hizmet yazarken bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e037f-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="e037f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e037f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e037f-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e037f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e037f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e037f-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e037f-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e037f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e037f-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e037f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e037f-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e037f-109">Attributes</span></span>  
  
|<span data-ttu-id="e037f-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e037f-110">Attribute</span></span>|<span data-ttu-id="e037f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e037f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e037f-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="e037f-112">webEndpointType</span></span>|<span data-ttu-id="e037f-113">Uç noktanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e037f-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e037f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e037f-114">Child Elements</span></span>  
 <span data-ttu-id="e037f-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e037f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e037f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e037f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e037f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e037f-117">Element</span></span>|<span data-ttu-id="e037f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e037f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e037f-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e037f-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="e037f-120">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e037f-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e037f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e037f-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
