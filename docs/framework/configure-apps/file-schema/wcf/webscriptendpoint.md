---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 3d95624c82388ed6219fc567dd2d3c17bedad7a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255295"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="5255d-101">\<webScriptEndpoint ></span><span class="sxs-lookup"><span data-stu-id="5255d-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="5255d-102">Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="5255d-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="5255d-103">Bir ASP.NET AJAX uygulamasından çağrılan hizmet yazarken Bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5255d-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="5255d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5255d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5255d-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5255d-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5255d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5255d-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5255d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5255d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5255d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5255d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5255d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5255d-109">Attributes</span></span>  
  
|<span data-ttu-id="5255d-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5255d-110">Attribute</span></span>|<span data-ttu-id="5255d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5255d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5255d-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="5255d-112">webEndpointType</span></span>|<span data-ttu-id="5255d-113">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5255d-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5255d-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5255d-114">Child Elements</span></span>  
 <span data-ttu-id="5255d-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="5255d-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5255d-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5255d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5255d-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5255d-117">Element</span></span>|<span data-ttu-id="5255d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5255d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5255d-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5255d-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5255d-120">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="5255d-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5255d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5255d-121">See also</span></span>
- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
