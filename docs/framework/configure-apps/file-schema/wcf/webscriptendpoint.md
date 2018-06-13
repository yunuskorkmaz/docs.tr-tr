---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b53b7cc3ce812b72830c0ad83c5cc2b42bfc25a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755311"
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="3c3a6-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="3c3a6-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="3c3a6-103">Bu yapılandırma öğesi bir sabit ile standart bir uç nokta tanımlayan [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="3c3a6-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="3c3a6-104">Bir ASP.NET AJAX uygulamasından adlı bir hizmet yazarken Bu uç nokta kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c3a6-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="3c3a6-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3c3a6-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3c3a6-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3c3a6-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c3a6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c3a6-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c3a6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c3a6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3c3a6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c3a6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c3a6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c3a6-110">Attributes</span></span>  
  
|<span data-ttu-id="3c3a6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3c3a6-111">Attribute</span></span>|<span data-ttu-id="3c3a6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c3a6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c3a6-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="3c3a6-113">webEndpointType</span></span>|<span data-ttu-id="3c3a6-114">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3c3a6-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c3a6-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c3a6-115">Child Elements</span></span>  
 <span data-ttu-id="3c3a6-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c3a6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c3a6-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3c3a6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3c3a6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3c3a6-118">Element</span></span>|<span data-ttu-id="3c3a6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c3a6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3c3a6-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3c3a6-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="3c3a6-121">Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.</span><span class="sxs-lookup"><span data-stu-id="3c3a6-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c3a6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c3a6-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
