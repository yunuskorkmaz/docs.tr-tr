---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: acafb5b6a5c4911dcf21a55cfb9e93883067e5ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566391"
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="e45c8-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="e45c8-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="e45c8-103">Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="e45c8-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="e45c8-104">Bir ASP.NET AJAX uygulamasından çağrılan hizmet yazarken Bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e45c8-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="e45c8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e45c8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e45c8-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e45c8-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45c8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e45c8-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e45c8-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e45c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e45c8-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e45c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e45c8-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e45c8-110">Attributes</span></span>  
  
|<span data-ttu-id="e45c8-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e45c8-111">Attribute</span></span>|<span data-ttu-id="e45c8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e45c8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e45c8-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="e45c8-113">webEndpointType</span></span>|<span data-ttu-id="e45c8-114">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e45c8-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e45c8-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e45c8-115">Child Elements</span></span>  
 <span data-ttu-id="e45c8-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e45c8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e45c8-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e45c8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e45c8-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e45c8-118">Element</span></span>|<span data-ttu-id="e45c8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e45c8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e45c8-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e45c8-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e45c8-121">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e45c8-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e45c8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e45c8-122">See also</span></span>
- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
