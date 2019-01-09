---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: beb17d4ccc39bcca30e97d4f0df47c797cde6216
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148779"
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="80dfa-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="80dfa-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="80dfa-103">Bu yapılandırma öğesi ile bir sabit bir standart uç nokta tanımlar [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) otomatik olarak bağlama ekler [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) davranışı.</span><span class="sxs-lookup"><span data-stu-id="80dfa-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="80dfa-104">Bir ASP.NET AJAX uygulamasından çağrılan hizmet yazarken Bu uç noktayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="80dfa-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="80dfa-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80dfa-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="80dfa-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="80dfa-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80dfa-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80dfa-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80dfa-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="80dfa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="80dfa-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80dfa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80dfa-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="80dfa-110">Attributes</span></span>  
  
|<span data-ttu-id="80dfa-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="80dfa-111">Attribute</span></span>|<span data-ttu-id="80dfa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80dfa-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80dfa-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="80dfa-113">webEndpointType</span></span>|<span data-ttu-id="80dfa-114">Uç nokta türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="80dfa-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80dfa-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="80dfa-115">Child Elements</span></span>  
 <span data-ttu-id="80dfa-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="80dfa-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80dfa-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="80dfa-117">Parent Elements</span></span>  
  
|<span data-ttu-id="80dfa-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="80dfa-118">Element</span></span>|<span data-ttu-id="80dfa-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80dfa-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80dfa-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="80dfa-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="80dfa-121">Daha fazla (adresi, bağlama, anlaşma) kendi özellik sabit veya olan standart uç noktaları koleksiyonu uç noktaları biriyle önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="80dfa-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80dfa-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80dfa-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
