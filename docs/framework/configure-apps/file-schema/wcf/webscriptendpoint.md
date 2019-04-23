---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: 9619c27c8c6d41250eeaeccabebe611e94b7d874
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105657"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="73571-101">\<webScriptEndpoint ></span><span class="sxs-lookup"><span data-stu-id="73571-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="73571-102">Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="73571-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="73571-103">Bir ASP.NET AJAX uygulamasından çağrılan hizmet yazarken Bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="73571-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="73571-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="73571-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73571-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="73571-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73571-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73571-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73571-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73571-107">Attributes and Elements</span></span>  
 <span data-ttu-id="73571-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73571-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73571-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73571-109">Attributes</span></span>  
  
|<span data-ttu-id="73571-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73571-110">Attribute</span></span>|<span data-ttu-id="73571-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73571-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73571-112">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="73571-112">webEndpointType</span></span>|<span data-ttu-id="73571-113">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="73571-113">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73571-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73571-114">Child Elements</span></span>  
 <span data-ttu-id="73571-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="73571-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73571-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73571-116">Parent Elements</span></span>  
  
|<span data-ttu-id="73571-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="73571-117">Element</span></span>|<span data-ttu-id="73571-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73571-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73571-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="73571-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="73571-120">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="73571-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73571-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73571-121">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
